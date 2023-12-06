# assignment3Part2

index.html --> /var/www/my-site directory
hello-server (binary file) --> /var/www/backend
hello.conf --> /etc/nginx/sites-available
hello.conf (symbolic link) --> /etc/nginx/sites-enabled
backend.log --> /var/log/hello-server
hello-sever.service --> /etc/systemd/system

### Cloud config script
users:
  - name: web1
    primary_group: web
    groups: sudo
    shell: /bin/bash
    sudo: ['ALL=(ALL) NOPASSWD:ALL']
    ssh-authorized-keys:
      - ssh-ed7862 AAAAGC3joE5FG9LKft398WDc2dw4Fe9hG7290Ey3vb email@gmail.com

packages:
  - ripgrep
  - rsync
  - nginx
  - ufw

runcmd:
  - sed -i 's/^#\(Storage=auto\)/\1/' /etc/systemd/journald.conf
  - sed -i -e '/^PermitRootLogin/s/^.*$/PermitRootLogin no/' /etc/ssh/sshd_config
  - systemctl restart ssh
  - systemctl restart systemd-journald
  - ufw allow ssh
  - ufw allow http
