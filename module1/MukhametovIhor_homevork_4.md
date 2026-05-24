# Homework 4

## Завдання 1

```bash
ubuntu@ubuntu-VirtualBox:~$ sudo apt remove tree
Зчитування переліків пакунків... Виконано
Побудова дерева залежностей... Виконано            
Зчитування інформації про стан... Виконано   
Пакунки, які будуть ВИДАЛЕНІ:
  tree
оновлено 0, встановлено 0 нових, 1 відмічено для видалення і 132 не оновлено.
Після цієї операції об'єм зайнятого дискового простору зменшиться на 116 kB.
Бажаєте продовжити? [Y=ТАК/n=ні] y
(Читання бази даних ... на дану мить встановлено 211648 файлів та каталогів.)
Вилучення tree (2.0.2-1) ...
Обробка тригерів man-db (2.10.2-1)...
ubuntu@ubuntu-VirtualBox:~$ systemctl status cron
● cron.service - Regular background program processing daemon
     Loaded: loaded (/lib/systemd/system/cron.service; enabled; vendor preset: >
     Active: active (running) since Sun 2026-05-24 20:55:41 EEST; 2h 48min ago
       Docs: man:cron(8)
   Main PID: 564 (cron)
      Tasks: 1 (limit: 7010)
     Memory: 460.0K
        CPU: 183ms
     CGroup: /system.slice/cron.service
             └─564 /usr/sbin/cron -f -P

тра 24 22:17:01 ubuntu-VirtualBox CRON[2272]: pam_unix(cron:session): session o>
тра 24 22:17:01 ubuntu-VirtualBox CRON[2272]: pam_unix(cron:session): session c>
тра 24 22:30:01 ubuntu-VirtualBox CRON[2351]: pam_unix(cron:session): session o>
тра 24 22:30:01 ubuntu-VirtualBox CRON[2352]: (root) CMD ([ -x /etc/init.d/anac>
тра 24 22:30:02 ubuntu-

```

### Пояснення:
apt update — оновлює список доступних пакетів.
apt install tree — встановлює пакет tree.
tree --version — показує версію встановленої утиліти.
dpkg -l | grep tree — перевіряє, чи пакет встановлено.
apt remove tree — видаляє встановлений пакет.

## Завдання 2

```bash
sudo systemctl stop cron
ubuntu@ubuntu-VirtualBox:~$ systemctl is-active cron
inactive
ubuntu@ubuntu-VirtualBox:~$ sudo systemctl start cron
ubuntu@ubuntu-VirtualBox:~$ systemctl is-active cron
active
ubuntu@ubuntu-VirtualBox:~$ sudo systemctl enable cron
Synchronizing state of cron.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable cron
ubuntu@ubuntu-VirtualBox:~$ systemctl is-enabled cron
enabled

```

### Пояснення:
systemctl status cron — показує стан сервісу cron.
systemctl stop cron — зупиняє сервіс.
systemctl is-active cron — перевіряє, чи сервіс активний.
systemctl start cron — запускає сервіс.
systemctl enable cron — додає сервіс в автозавантаження.
systemctl is-enabled cron — перевіряє автозавантаження.

## Завдання 3

```bash

```

### Пояснення:


## Завдання 4

```bash

```

### Пояснення:
