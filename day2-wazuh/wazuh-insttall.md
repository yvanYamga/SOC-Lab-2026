sudo apt update && sudo apt upgrade -y
sudo apt install -y curl wget vim net-tools htop

sudo hostnamectl set-hostname "wazuh-aio"

cd ~/tmp/
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh && sudo bash ./wazuh-install.sh -a