# Ansible scripts for install Adguard Home

## Installation

This application requires you have a Python interpreter installed.

__Create a virtual environment__
```console
python -m venv --prompt adguard-ansible .venv
```

__Install ansible__
```console
.venv/bin/pip install -U pip -r requirements.txt
```

## Rock 4 SE

### Preparation

Some preparation is required before you can run the ansible script, namely:

- You will need to update sudoers
- You will need to connect the device to your network

Boot the device and login with the default username and password:

- username: radxa
- password: radxa

__Create the appropriate sudoers entry__
```console
sudo sh -c 'echo "radxa ALL=(ALL)   NOPASSWD: ALL" > /etc/sudoers.d/sudoers'
```

__Connect to your network__
```console
sudo nmcli dev wifi connect <SSID> --ask
```

You should now be able to SSH into the device.

```console
ssh-copy-id -i ~/.ssh/id_rsa.pub radxa@<device ip>
ssh radxa@<device ip>
```

### Running the playbook

```console
,runplay -i <device ip> -p play_rockpi_deb.yml
```

After the playbook has run you can configure Adguard Home by visting [http://adguard.local:3000/](http://adguard.local:3000/).