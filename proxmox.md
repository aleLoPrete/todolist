## Proxmox setup todolist

### Updates

Set up automatic updates (unstable)
[ ] In /etc/apt/sources.list :
    # not for production use
    deb http://download.proxmox.com/debian buster pve-no-subscription

[ ] In /etc/apt/sources.list.d/pve-enterprise.list, comment the line out, to avoid error during updates

[ ] apt-get update
[ ] apt dist-upgrade

### Laptop specific tuning

- Installing tlp for battery management optimization
    apt install -y tlp

- Disable network manager
    systemctl disable network-manager --now

- Handling lid closing
    echo "@reboot root systemctl disable network-manager --now" >> /etc/crontab
    echo "HandleLidSwitch=ignore" >> /etc/systemd/logind.conf
    echo "HandleLidSwitchExternalPower=ignore" >> /etc/systemd/logind.conf
    echo "HandleLidSwitchDocked=ignore" >> /etc/systemd/logind.conf


