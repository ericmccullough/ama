# AMA

Install/Configure an Automated Malware Analysis server using
  Viper for static analysis
  Cuckoo for behavioral analysis
  Cuckoo uses Yara for signature based scanning
  Cuckoo uses Elasticsearch for the results
  Cuckoo can use Volatility for memory dump analysis

## Installation notes
on base unbuntu box, install chef client
```apt-get install chef```
sudo apt install curl
curl -L https://omnitruck.chef.io/install.sh | sudo bash


sudo apt install ssh

to install berkshelf
sudo apt install build-essential
sudo apt install ruby-dev
sudo gem install berkshelf --no-rdoc --no-ri

sudo apt install git
git clone https://github.com/ericmccullough/ama.git

cd ama/cookbooks/ama
berks vendor ..
sudo chef-client -z -o ama

vi ../supervisor/metadata.json     # change python to poise-python
vi ../supervisor/recipes/default.rb    # change python to poise-python and python_pip to python_package
vi ../cuckoo/attributes/default.rb
change default[:cuckoo][:host][:source][:revision] = '2.0-rc1' to default[:cuckoo][:host][:source][:revision] = '2.0.3'
change default[:virtualbox][:version] = '5.0' to default[:virtualbox][:version] = '5.1'
vi ../cuckoo/recipes/host.rb
comment out pip_requirements "#{node[:cuckoo][:host][:source][:dest]}/requirements.txt"
