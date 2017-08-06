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
sudo gem install berkshelf

sudo apt install git
git clone https://github.com/ericmccullough/ama.git

cd ama/cookbooks/ama
berks vendor ..
chef-client -z -o ama