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
buntu@ubuntu-VirtualBox:~$ cd /var/log
ubuntu@ubuntu-VirtualBox:/var/log$ ls
alternatives.log       boot.log.4     dpkg.log.1       kern.log.3.gz
alternatives.log.1     boot.log.5     dpkg.log.2.gz    lastlog
alternatives.log.2.gz  bootstrap.log  faillog          openvpn
apt                    btmp           fontconfig.log   private
auth.log               btmp.1         gdm3             speech-dispatcher
auth.log.1             cups           gpu-manager.log  syslog
auth.log.2.gz          dist-upgrade   hp               syslog.1
auth.log.3.gz          dmesg          installer        syslog.2.gz
boot.log               dmesg.0        journal          syslog.3.gz
boot.log.1             dmesg.1.gz     kern.log         ubuntu-advantage.log
boot.log.2             dmesg.2.gz     kern.log.1       unattended-upgrades
boot.log.3             dpkg.log       kern.log.2.gz    wtmp
ubuntu@ubuntu-VirtualBox:/var/log$ tail -n 10 syslog
May 25 00:04:51 ubuntu-VirtualBox google-chrome.desktop[2373]: [2367:2367:0525/000451.198469:ERROR:extensions/browser/api/web_request/extension_web_request_event_router.cc:1919] AddEventListener: 0x3ba400625480 extension_id: gighmmpiobklfepjocnamgkkbiglidom extension_name: AdBlock — найкращий блокувальник реклами event_name: webRequest.onErrorOccurred sub_event_name: webRequest.onErrorOccurred/s5 render_process_id: 322 web_view_instance_id: 0 worker_thread_id: 1 service_worker_version_id: 7
May 25 00:04:51 ubuntu-VirtualBox google-chrome.desktop[2373]: [2367:2367:0525/000451.

```

### Пояснення:
cd /var/log — перехід у каталог системних журналів.
tail -n 10 syslog — показує останні 10 рядків журналу syslog.
journalctl -p err -n 20 — показує останні помилки системного журналу.
journalctl -u cron -n 20 — показує записи журналу для сервісу cron.

## Завдання 4

```bash
on): session o>
тра 24 23:17:01 ubuntu-VirtualBox CRON[4655]: (root) CMD (   cd / && run-parts >
тра 24 23:17:01 ubuntu-VirtualBox CRON[4654]: pam_unix(cron:session): session c>
тра 24 23:30:01 ubuntu-VirtualBox CRON[4945]: pam_unix(cron:session): session o>
тра 24 23:30:01 ubuntu-VirtualBox CRON[4945]: pam_unix(cron:session): session c>
тра 24 23:50:02 ubuntu-VirtualBox systemd[1]: Stopping Regular background progr>
тра 24 23:50:02 ubuntu-VirtualBox systemd[1]: cron.service: Deactivated success>
тра 24 23:50:02 ubuntu-VirtualBox systemd[1]: Stopped Regular background progra>
тра 24 23:51:08 ubuntu-VirtualBox systemd[1]: Started Regular background progra>
тра 24 23:51:08 ubuntu-VirtualBox cron[6838]: (CRON) INFO (pidfile fd = 3)
тра 24 23:51:08 ubuntu-VirtualBox cron[6838]: (CRON) INFO (Skipping @reboot job>
ubuntu@ubuntu-VirtualBox:/var/log$ nano ~/myscript.sh
ubuntu@ubuntu-VirtualBox:/var/log$ chmod +x ~/myscript.sh
ubuntu@ubuntu-VirtualBox:/var/log$ sudo nano /etc/systemd/system/myscript.service
[sudo] пароль до ubuntu: 
ubuntu@ubuntu-VirtualBox:/var/log$ sudo systemctl daemon-reload
ubuntu@ubuntu-VirtualBox:/var/log$ sudo systemctl start myscript.service
ubuntu@ubuntu-VirtualBox:/var/log$ systemctl status myscript.service
● myscript.service - My Date Script Service
     Loaded: loaded (/etc/systemd/system/myscript.service; disabled; vendor pre>
     Active: active (running) since Mon 2026-05-25 00:16:09 EEST; 15s ago
   Main PID: 8133 (myscript.sh)
      Tasks: 2 (limit: 7010)
     Memory: 592.0K
        CPU: 127ms
     CGroup: /system.slice/myscript.service
             ├─8133 /bin/bash /home/ubuntu/myscript.sh
             └─8181 sleep 1

тра 25 00:16:09 ubuntu-VirtualBox systemd[1]: Started My Date Script Service.
ubuntu@ubuntu-VirtualBox:/var/log$ tail -n 10 /home/ubuntu/mydate.log
понеділок, 25 травня 2026 00:16:40 +0300
понеділок, 25 травня 2026 00:16:41 +0300
понеділок, 25 травня 2026 00:16:42 +0300
понеділок, 25 травня 2026 00:16:43 +0300
понеділок, 25 травня 2026 00:16:44 +0300
понеділок, 25 травня 2026 00:16:45 +0300
понеділок, 25 травня 2026 00:16:46 +0300
понеділок, 25 травня 2026 00:16:47 +0300
понеділок, 25 травня 2026 00:16:48 +0300
понеділок, 25 травня 2026 00:16:49 +0300
ubuntu@ubuntu-VirtualBox:/var/log$ sudo systemctl enable myscript.service
Created symlink /etc/systemd/system/multi-user.target.wants/myscript.service → /etc/systemd/system/myscript.service.
ubuntu@ubuntu-VirtualBox:/var/log$ 

```

### Пояснення:
myscript.sh — bash-скрипт, який щосекунди записує поточну дату у файл mydate.log.
chmod +x — надає скрипту право на запуск.
myscript.service — systemd unit-файл для запуску скрипта як сервісу.
systemctl daemon-reload — перечитує конфігурації systemd.
systemctl start — запускає сервіс.
systemctl status — перевіряє стан сервісу.
tail -n 10 — показує останні записи у файлі журналу скрипта.
systemctl enable — додає сервіс в автозавантаження.

