## DietPi

```bash
curl -sfL https://get.k3s.io | K3S_URL=https://$MASTER_IP:6443 K3S_TOKEN=$K3S_TOKEN sh -
```
You can get the `K3S_TOKEN` from `/var/lib/rancher/k3s/server/node-token` on the master node.
Then add `cgroup_memory=1 cgroup_enable=memory` to the end of `/boot/cmdline.txt`, then do
```bash
sudo reboot
sudo systemctl enable --now k3s-agent
```

### Add static ip 
`sudo nano /etc/network/interfaces` and change `iface wlan0 inet dhcp` to `iface wlan0 inet static` and set the address and then do `sudo reboot`. This reboot will require manually unpluggin and plugging back in the device.