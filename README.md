# cluster

# Control Node

* Ubuntu server 20 amd
* Don't install OpeSSH -- install dropbear
* Remove open-vm-tools service
* Stop and disable multipath-tools service

### Commands
```bash
sudo apt update
sudo apt install dropbear -y
systemctl stop open-vm-tools
sudo systemctl disable open-vm-tools
sudo rm -rf /etc/systemd/system/open-vm-tools.service.requires/
sudo rm /usr/lib/systemd/system/open-fm-tools.service
sudo rm /etc/init.d/open-vm-tools
systemctl daemon-reload
sudo systemctl reset-failed
sudo apt -y upgrade && sudo systemctl reboot
curl -sfL https://get.k3s.io | sh -

GITHUB_URL=https://github.com/kubernetes/dashboard/releases
VERSION_KUBE_DASHBOARD=$(curl -w '%{url_effective}' -I -L -s -S ${GITHUB_URL}/latest -o /dev/null | sed -e 's|.*/||')
sudo k3s kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/${VERSION_KUBE_DASHBOARD}/aio/deploy/recommended.yaml
mkdir dashboard
cd dashboard
wget http://staging:8000/dashboard.admin-user.yml
wget http://staging:8000/dashboard.admin-user-role.yml
sudo k3s kubectl create -f dashboard.admin-user.yml -f dashboard.admin-user-role.yml
sudo kubectl proxy --accept-hosts='^192\.168\.0\.[0-9][0-9][0-9]'
```

### TODO

* Configure rsyslog
* Get dashboard working https://sondnpt00343.medium.com/deploying-a-publicly-accessible-kubernetes-dashboard-v2-0-0-betax-8e39680d4067
