# Установка и настройка Linux в рамках импортозамещения
<p># Администрирование локальных, виртуальных и облачных серверов.<br />
# Администрирование базы данных.<br />
# Разработка базы данных.<br />
# Написание Sql запросов.<br />
<strong>Task:</strong><br />Установить Hyper-V в Windows Server 2012 c помощью Shell<br /><strong>Decision:</strong><br />PS C:\Windows\system32&gt; Get-Module -ListAvailable<br />Каталог: C:\Windows\system32\WindowsPowerShell\v1.0\Modules<br />ModuleType Version&nbsp;&nbsp;&nbsp; Name&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ExportedCo<br />---------- -------&nbsp;&nbsp;&nbsp; ----&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ----------<br />...<br />Binary&nbsp;&nbsp;&nbsp;&nbsp; 1.1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Hyper-V&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {Add-VMDvd<br />...<br />PS C:\Windows\system32&gt; Import-Module -Name Hyper-V<br /><strong>Task:</strong><br />Развернуть виртуальную тестовую машину Redos в Hyber-v с помощью Powershell<br /><strong>Decision:</strong><br />PS C:\Windows\system32&gt; Get-VM<br />Name State CPUUsage(%) MemoryAssigned(M) Uptime&nbsp;&nbsp; Status<br />---- ----- ----------- ----------------- ------&nbsp;&nbsp; ------<br />Alt&nbsp; Off&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 00:00:00 Работает нормально<br />PS C:\Windows\system32&gt; $ram=1*1024*1024*1024<br />PS C:\Windows\system32&gt; $ram<br />1073741824<br />PS C:\Windows\system32&gt; $hdd=10*1024*1024*1024<br />PS C:\Windows\system32&gt; $hdd<br />10737418240<br />PS C:\Windows\system32&gt; NEW-VM -Name Redos -MemoryStartupBytes $ram -NewVHDPath 'C:\Data\VM\Redos\Redos.vhdx'-NewVHD<br />SizeBytes $hdd -Path 'C:\Data\VM\Redos'<br />Name State CPUUsage(%) MemoryAssigned(M) Uptime&nbsp;&nbsp; Status<br />---- ----- ----------- ----------------- ------&nbsp;&nbsp; ------<br />Redos Off&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 00:00:00 Работает нормально<br />PS C:\Windows\system32&gt; Get-VM<br />Name State CPUUsage(%) MemoryAssigned(M) Uptime&nbsp;&nbsp; Status<br />---- ----- ----------- ----------------- ------&nbsp;&nbsp; ------<br />Alt&nbsp; Off&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 00:00:00 Работает нормально<br />Redos Off&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 00:00:00 Работает нормально<br />PS C:\Windows\system32&gt; Start-VM -name Redos<br />PS C:\Windows\system32&gt; Get-VM<br />Name State&nbsp;&nbsp; CPUUsage(%) MemoryAssigned(M) Uptime&nbsp;&nbsp; Status<br />---- -----&nbsp;&nbsp; ----------- ----------------- ------&nbsp;&nbsp; ------<br />Alt&nbsp; Off&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 00:00:00 Работает нормально<br />Redos Running 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1024&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 00:00:16 Работает нормально<br />PS C:\Windows\system32&gt; Stop-VM Redos<br />Подтверждение<br />Hyper-V не удается завершить работу виртуальной машины Redos, так как служба интеграции по завершению работы недоступна.<br />&nbsp;Во избежание потенциальной потери данных вы можете приостановить виртуальную машину или сохранить ее состояние. Другим<br />&nbsp;вариантом является отключение виртуальной машины, но при этом возможна потеря данных.<br />[Y] Да - Y&nbsp; [N] Нет - N&nbsp; [S] Приостановить - S&nbsp; [?] Справка (значением по умолчанию является "Y"): y<br />PS C:\Windows\system32&gt; Get-VM<br />Name State CPUUsage(%) MemoryAssigned(M) Uptime&nbsp;&nbsp; Status<br />---- ----- ----------- ----------------- ------&nbsp;&nbsp; ------<br />Alt&nbsp; Off&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 00:00:00 Работает нормально<br />Redos Off&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 00:00:00 Работает нормально<br /><strong>Task:</strong><br />Установить и настроить дистрибутив Redos в виртуальной машине<br /><strong>Decision:</strong><br />выбираем Install - выбрать размер разделов - поменяем систему разметки LVM на Standart Portition - нажимаем на click here to create them autmaticaly - установщик автоматически разделит диск - уменьшить размер корневого раздела / и раздел /home - Меняю у них размеры - Done - интернет настроить в Network &amp; Host Name - Ethernet переключаем тумблер - Done - software Slection - minmal install- Done - запуск<br /><strong>Task:</strong><br /># dnf -y install kernel-devel-$(uname -r)<br />&nbsp;&nbsp;&nbsp; Last metadata expiration check: 0:52:33 ago on Thu 14 May 2020 03:36:35 AM EDT.<br />&nbsp;&nbsp;&nbsp; No match for argument: kernel-devel-4.18.0-147.el8.x86_64<br />&nbsp;&nbsp;&nbsp; Error: Unable to find a match: kernel-devel-4.18.0-147.el8.x86_64<br /><strong>Decision:</strong><br /># dnf -y install kernel-devel<br /><strong>Task:</strong> &nbsp;<br />Ввод компьютера в домен Windows и изменение имени хоста<br /><strong>Decision:</strong><br /># yum install join-to-domain<br /># join-to-domain.sh<br /># reboot<br /># hostname<br />&nbsp;&nbsp;&nbsp; thost1.tdomain.ru<br /># hostname thost2.tdomain.ru<br /># hostname<br />&nbsp;&nbsp;&nbsp; thost2.tdomain.ru<br /># vim /etc/hostname<br /># cat /etc/hostname<br />&nbsp;&nbsp;&nbsp; thost2.tdomain.ru<br /># vim /etc/hosts<br /># cat /etc/hosts<br />&nbsp;&nbsp;&nbsp; 127.0.0.1 localhost localhost.localdomain localhost4 localhost4.localdomain4<br />&nbsp;&nbsp;&nbsp; ::1 localhost localhost.localdomain localhost6 localhost6.localdomain6<br />&nbsp;&nbsp;&nbsp; 127.0.0.1 thost2.tdomain.ru thost2<br /><strong>Task:</strong><br />Установка Консультант Плюс и подключение сетевых директорий с использованием automount и механизма Kerberos<br /><strong>Decision:</strong><br />$ yum install wine winetricks<br /># winetricks riched30 winhttp<br />Wine -&gt; Wine Configuration -&gt; Графика -&gt; уберите галочку в пункте "Разрешить менеджеру окон декорировать окна". -&gt; Для запуска &laquo;Консультант Плюс&raquo; на рабочей станции подключите сетевой диск с &laquo;Консультантом&raquo; -&gt; Сделать это можно с помощью подключения сетевых директорий с использованием automount и механизма Kerberos<br />$ smbclient -L thost -k<br />Sharename Type Comment<br />--------- ---- -------<br />Consultant Disk<br />ConsultantR Disk<br />...<br />S Disk<br />Reconnecting with SMB1 for workgroup listing.<br />Server Comment<br />-------- -------<br />Wg M<br />--------- -------<br /># yum install cifs-utils autofs<br />$ klist<br />Ticket cache: FILE:/tmp/krb5cc_1<br />Default principal: tuser@tdomain.RU<br />Valid starting Expires service principal<br />31.08.2020 09:51:47 31.08.2020 19:51:47 krbtgt/tdomain.RU@tdomain.RU<br />renew until 31.08.2020 19:51:47<br /># vim /etc/auto.master<br /># cat /etc/auto.master<br />...<br />/mnt/.thost&nbsp;&nbsp;&nbsp; /etc/auto.samba&nbsp;&nbsp;&nbsp; --ghost<br /># vim /etc/auto.samba<br /># cat /etc/auto.samba<br />Consultant&nbsp;&nbsp;&nbsp; -fstype=cifs,multiuser,cruid=tuser,sec=krb5,domain=tdomain.RU,vers=2.1&nbsp;&nbsp;&nbsp;&nbsp; ://thost/Consultant<br />Students&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -fstype=cifs,multiuser,cruid=tuser,sec=krb5,domain=tdomain.RU,vers=2.1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ://thost/Students<br />Для подключения скрытых сетевых каталогов необходимо экранировать символ $<br />Consultant&nbsp;&nbsp;&nbsp; -fstype=cifs,multiuser,cruid=tuser,sec=krb5,domain=tdomain.RU,vers=2.1&nbsp;&nbsp;&nbsp;&nbsp; ://thost/Consultant\$<br />В файле /etc/krb5.conf нужно закомментировать строку (если она ещё не закомментирована)<br />#cat /etc/krb5.conf<br />...<br />default_ccache_name = KEYRING:persistent:%{uid}<br />...<br />#vim/etc/krb5.conf<br />#cat /etc/krb5.conf<br />...<br />default_ccache_name = FILE:/tmp/krb5cc_%{uid}<br />...<br /># systemctl start autofs.service<br /># systemctl enable autofs --now<br />Created symlink from /etc/systemd/system/multi-user.target.wants/autofs.service to /usr/lib/systemd/system/autofs.service.<br /># ls /mnt/.thost/Consultant/<br />... cons.exe ...<br />$ winecfg<br /># wine /mnt/.thost/Сonsultant/cons.exe /linux /yes<br /><strong>Task:</strong><br />Создать ярлык Консультант +<br /><strong>Decision:</strong><br /># vim /home/tuser@thost.ru/Рабочий\ стол/Consultant.desktop<br /># cat /home/tuser@thost.ru/Рабочий\ стол/Consultant.desktop<br />[Desktop Entry]<br />Name=ConsultantPlus<br />Exec=wine /mnt/.thost/Сonsultant/cons.exe<br />Type=Application<br />StartupNotify=true<br />Comment=ConsultantPlus<br />icon=43D4_Cons.0<br />StartupWMClass=c.exe<br /><strong>Task:</strong><br />В случае замедленной работы можно добавить ключ /sprocess=0 При нормальной работе, не добавляйте этот ключ. Ключ /yes необходим для подавления сообщения об ошибке [WNetGetUniversalName ...] : NO_NETWORK<br /><strong>Decision:</strong><br /># ln -s /mnt/.thost/S /home/tuser@thost.ru/Рабочий\ стол/S<br /><strong>Task:</strong><br />Создание ярлыка для сетевой директории<br /><strong>Decision:</strong><br /># ln -s /mnt/.thost/S /home/tuser@thost.ru/Рабочий\ стол/S<br /><strong>Task:</strong><br />После добавления сетевых папок через Kerberos на следующий месяц, все етевые папки на ПК перестали работать. Для решения проблемы нужно обновлять билеты через kdestroy и kinit:<br /><strong>Decision:</strong><br />$ smbclient -L thost -k<br />gse_get_client_auth_token: gss_init_sec_context failed with [ Miscellaneous failure (see text): encryption type 0 not supported](2529639062)<br />gensec_spnego_client_negTokenInit_step: gse_krb5: creating NEG_TOKEN_INIT for cifs/tusertsrvdoc failed (next[(null)]): NT_STATUS_LOGON_FAILURE<br />session setup failed: NT_STATUS_LOGON_FAILURE<br />$ klist<br />Ticket cache: FILE:/tmp/krb5cc_17<br />Default principal: tuser@tdomain.RU<br />Valid starting Expires Service principal<br />01.01.1970 08:00:00 01.01.1970 08:00:00 krbtgt/tdomain.RU@tdomain.RU<br />$ date<br />Вт окт 6 14:46:12 +08 2020<br />$ kdestroy<br />$ kinit<br />$ klist<br />Ticket cache: FILE:/tmp/krb5cc_17<br />Default principal: tuser@tdomain.RU<br />Valid starting Expires Service principal<br />06.10.2020 14:46:51 07.10.2020 00:46:51 krbtgt/tdomain.RU@tdomain.RU<br />renew until 13.10.2020 14:46:29<br /><strong>Decision:</strong><br />Проблема решена, но билет кеширования, нужно было обновлять постоянно. Поэтому, на мой взгляд, проще подключать сетевые папки через automount без Kerberos.<br /><strong>Task:</strong><br />Oграничение доступа к USB накопителям<br /><strong>Decision:</strong><br /># vim /etc/udev/rules.d/99-usb.rules<br /># cat /etc/udev/rules.d/99-usb.rules<br />ENV{ID_USB_DRIVER}=="usb-storage",ENV{UDISKS_IGNORE}="1"<br /># udevadm control --reload-rules<br /><strong>Task:</strong><br />Запрет создания ярлыков и файлов на рабочем столе<br /><strong>Decision:</strong><br />Проверить, поддерживает ли ваша файловая система ACL можно командой (вместо /dev/sda1 указать нужное имя дискового раздела):<br /># tune2fs -l /dev/sda1 | grep "Default mount options:"<br />Default mount options: user_xattr acl<br /># vim /home/tuser@thost.ru/.config/user-dirs.dirs<br /># cat /home/tuser@thost.ru/.config/user-dirs.dirs<br /># This file is written by xdg-user-dirs-update<br /># If you want to change or add directories, just edit the line you're<br /># interested in. All local changes will be retained on the next run<br /># Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped<br /># homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an<br /># absolute path. No other format is supported.<br />#<br />XDG_DESKTOP_DIR="$HOME/Рабочий стол"<br />XDG_DOWNLOAD_DIR="$HOME/Загрузки"<br />XDG_TEMPLATES_DIR="$HOME/Шаблоны"<br />XDG_PUBLICSHARE_DIR="$HOME/Общедоступные"<br />XDG_DOCUMENTS_DIR="$HOME/Документы"<br />XDG_MUSIC_DIR="$HOME/Музыка"<br />XDG_PICTURES_DIR="$HOME/Изображения"<br />XDG_VIDEOS_DIR="$HOME/Видео"<br /># ls -la /home/tuser@thost.ru/.config<br />...<br />-rw-------. 1 tuser &iuml;&icirc;&euml;&uuml;&ccedil;&icirc;&acirc;&agrave;&ograve;&aring;&euml;&egrave; &auml;&icirc;&igrave;&aring;&iacute;&agrave; 714 &agrave;&acirc;&atilde; 31 09:52 user-dirs.dirs<br />-rw-r--r--. 1 tuser &iuml;&icirc;&euml;&uuml;&ccedil;&icirc;&acirc;&agrave;&ograve;&aring;&euml;&egrave; &auml;&icirc;&igrave;&aring;&iacute;&agrave; 5 &agrave;&acirc;&atilde; 31 09:52 user-dirs.locale<br /># chown root:root /home/tuser@thost.ru/.config/user-dirs.dirs<br /># ls -la /home/tuser@thost.ru/.config<br />...<br />-rw-------. 1 root root 714 &agrave;&acirc;&atilde; 31 09:52 user-dirs.dirs<br />-rw-r--r--. 1 tuser &iuml;&icirc;&euml;&uuml;&ccedil;&icirc;&acirc;&agrave;&ograve;&aring;&euml;&egrave; &auml;&icirc;&igrave;&aring;&iacute;&agrave; 5 &agrave;&acirc;&atilde; 31 09:52 user-dirs.locale<br /># ls -la<br />...<br />drwxr-xr-x. 2 tuser &iuml;&icirc;&euml;&uuml;&ccedil;&icirc;&acirc;&agrave;&ograve;&aring;&euml;&egrave; &auml;&icirc;&igrave;&aring;&iacute;&agrave; 4096 &agrave;&acirc;&atilde; 31 09:52 'Рабочий стол'<br />...<br /># chown -R root:root /home/tuser@thost.ru/Рабочий\ стол/<br /># ls -la<br />...<br />drwxr-xr-x. 2 root root 4096 &agrave;&acirc;&atilde; 31 09:52 'Рабочий стол'<br />drwxr-xr-x. 2 tuser &iuml;&icirc;&euml;&uuml;&ccedil;&icirc;&acirc;&agrave;&ograve;&aring;&euml;&egrave; &auml;&icirc;&igrave;&aring;&iacute;&agrave; 4096 &agrave;&acirc;&atilde; 31 09:52 &Oslash;&agrave;&aacute;&euml;&icirc;&iacute;&ucirc;<br /><strong>Task:</strong><br />Как скрыть пользователей от экрана входа<br /><strong>Decision:</strong><br /># cat /var/lib/AccountsService/users/user<br />[User]<br />Language=<br />XSession=<br />SystemAccount=false<br /># vim /var/lib/AccountsService/users/user<br /># cat /var/lib/AccountsService/users/user<br />[User]<br />Language=<br />XSession=gnome<br />SystemAccount=true<br /><strong>Task:</strong><br />Добавление пользователя из доменной сети<br /><strong>Decision:</strong><br />[root@thost user]# vim /var/lib/AccountsService/users/tuser<br />[root@thost user]# cat /var/lib/AccountsService/users/tuser<br />[User]<br />Language=<br />XSession=<br />Icon=/home/tuser@thost.ru/.face<br />SystemAccount=false<br /><strong>Task:</strong><br />отключить сетевые принтеры<br /><strong>Decision:</strong><br /># vim /etc/avahi/avahi-daemon.conf<br />cat /etc/avahi/avahi-daemon.conf<br /># This file is part of avahi.<br />...<br />enable-dbus=no<br />...<br /># reboot<br /><strong>Task:</strong><br />Установка Gimp<br /><strong>Decision:</strong><br />yum provides gimp<br />Загружены модули: fastestmirror, langpacks<br />Loading mirror speeds from cached hostfile<br />2:gimp-2.8.22-2.el7.thost86 : GNU Image Manipulation Program<br />Источник: base<br />2:gimp-2.8.22-2.el7.x86_64 : GNU Image Manipulation Program<br />Источник: base<br /># yum list | grep gimp<br />gimp.thost86 2:2.8.22-2.el7 base<br /># yum -y install gimp<br /><strong>Task:</strong><br />Запись дисков Linux в терминале<br /><strong>Decision:</strong><br /># ls<br />13 'MyTestX Tests'<br /># pwd<br />/home/is@tdomain.RU/Documents<br /># mkisofs -o first.iso /home/is@tdomain.RU/Documents/13<br /># ls<br />13 first.iso 'MyTestX Tests'<br /># mkisofs -l -o first.iso /home/is@tdomain.RU/Documents/13<br /># ls<br />13 first.iso 'MyTestX Tests'<br /># mkisofs -D -l -o first.iso /home/is@tdomain.RU/Documents/13<br /># mkisofs -J -l -o first.iso /home/is@tdomain.RU/Documents/13<br />Warning: creating filesystem with Joliet extensions but without Rock Ridge<br />extensions. It is highly recommended to add Rock Ridge.<br />...<br />Joliet tree sort failed. The -joliet-long switch may help you.<br /># -joliet-long<br /># mkisofs -J -joliet-long -l -o first.iso /home/is@tdomain.RU/Documents/13<br />Warning: creating filesystem with Joliet extensions but without Rock Ridge<br />extensions. It is highly recommended to add Rock Ridge.<br />...<br />99.90% done, estimate finish Fri Jan 15 11:29:00 2021<br />Total translation table size: 0<br />Total rockridge attributes bytes: 0<br />Total directory bytes: 0<br />Path table size(bytes): 10<br />Max brk space used 0<br />545548 extents written (1065 MB# lsblk -d -o +MODEL<br />NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT MODEL<br />sda 8:0 0 111,8G 0 disk KINGSTON SA400S3<br />sr0 11:0 1 2K 0 rom CDDVDW SN-208BB<br />Если вы собираетесь записать образ на диск ubuntu DVD-RW/CD-RW необходимо сначала его очистить:<br />cdrecord -dev=/dev/sr0 -v blank=fast<br /># cd Documents/<br /># ls<br />13 first.iso 'MyTestX Tests'<br />Здесь и ниже /dev/sr0 - адрес файла вашего привода:<br /># cdrecord -dev=/dev/sr0 -speed=16 -eject -v first.iso<br />first.iso - это файл образа, 16 - скорость записи, а опция -eject - заставляет извлечь диск из привода после записи. Можно указывать скорость 4, 8 и 16. Желательно выбирать минимальную скорость, так диск запишется более качественно.<br /><strong>Task:</strong><br />Установка клиента 1С<br /><strong>Decision:</strong><br /># yum -y install webkitgtk3<br /># ls<br />1C_Enterprise83-client-8.3.14-17.x86_64.rpm<br />1C_Enterprise83-common-8.3.14-17.x86_64.rpm<br />1C_Enterprise83-server-8.3.14-17.x86_64.rpm<br /># yum -y install 1C_Enterprise83-*<br /><strong>Task:</strong><br />Установка аналога paint<br /><strong>Decision:</strong><br /># yum list | grep paint<br />kolourpaint.thost86 17.12.1-2.el7 base<br />kolourpaint.x86_64 17.12.1-2.el7 base<br />kolourpaint-libs.thost86 17.12.1-2.el7 base<br />kolourpaint-libs.x86_64 17.12.1-2.el7 base<br /># yum -y install kolourpaint<br /><strong>Task:</strong><br />Настройка оповещения и автоматического обновления пакетов в РЕД ОС с помощью yum-cron<br /><strong>Decision:</strong><br /># yum -y install yum-cron<br /># vim /etc/yum/yum-cron.conf<br /># cat /etc/yum/yum-cron.conf<br />[commands]<br /># What kind of update to use:<br /># default = yum upgrade<br /># security = yum --security upgrade<br /># security-severity:Critical = yum --sec-severity=Critical upgrade<br /># minimal = yum --bugfix update-minimal<br /># minimal-security = yum --security update-minimal<br /># minimal-security-severity:Critical = --sec-severity=Critical update-minimal<br />update_cmd = default<br /># Whether a message should be emitted when updates are available,<br /># were downloaded, or applied.<br />update_messages = yes<br /># Whether updates should be downloaded when they are available.<br />download_updates = yes<br /># Whether updates should be applied when they are available. Note<br /># that download_updates must also be yes for the update to be applied.<br />apply_updates = no<br /># Maximum amout of time to randomly sleep, in minutes. The program<br /># will sleep for a random amount of time between 0 and random_sleep<br /># minutes before running. This is useful for e.g. staggering the<br /># times that multiple systems will access update servers. If<br /># random_sleep is 0 or negative, the program will run immediately.<br /># 6*60 = 360<br />random_sleep = 360<br />...<br /># vim /etc/yum/yum-cron.conf<br /># cat /etc/yum/yum-cron.conf<br />[commands]<br /># What kind of update to use:<br /># default = yum upgrade<br /># security = yum --security upgrade<br /># security-severity:Critical = yum --sec-severity=Critical upgrade<br /># minimal = yum --bugfix update-minimal<br /># minimal-security = yum --security update-minimal<br /># minimal-security-severity:Critical = --sec-severity=Critical update-minimal<br />update_cmd = default<br /># Whether a message should be emitted when updates are available,<br /># were downloaded, or applied.<br />update_messages = yes<br /># Whether updates should be downloaded when they are available.<br />download_updates = yes<br /># Whether updates should be applied when they are available. Note<br /># that download_updates must also be yes for the update to be applied.<br />apply_updates = yes<br /># Maximum amout of time to randomly sleep, in minutes. The program<br /># will sleep for a random amount of time between 0 and random_sleep<br /># minutes before running. This is useful for e.g. staggering the<br /># times that multiple systems will access update servers. If<br /># random_sleep is 0 or negative, the program will run immediately.<br /># 6*60 = 360<br />random_sleep = 360<br />...<br /># systemctl enable yum-cron --now<br /><strong>Task:</strong> &nbsp;<br />Если не требуется обновлять определенные пакеты (как вручную, так и автоматически), то добавляем их в исключение. Например, kernel и php.<br /><strong>Decision:</strong><br />#nano /etc/yum.conf<br />exclude=kernel, php<br /><strong>Task:</strong> &nbsp;<br />Если не требуется обновлять пакеты ТОЛЬКО в автоматическом режиме, тогда в /etc/yum/yum-cron.conf , в раздел [base], добавляем следующую строку:<br />Decision<br /># nano /etc/yum/yum-cron.conf<br />exclude=kernel* php*<br /><strong>Task:</strong><br />Установка Anydesk<br /><strong>Decision:</strong><br /># tee /etc/yum.repos.d/AnyDesk-RHEL.repo &lt;&lt;EOF<br />&gt; [anydesk]<br />&gt; name=AnyDesk RHEL - stable<br />&gt; baseurl=http://rpm.anydesk.com/rhel/\$basearch/<br />&gt; gpgcheck=1<br />&gt; repo_gpgcheck=1<br />&gt; gpgkey=https://keys.anydesk.com/repos/RPM-GPG-KEY<br />&gt; EOF<br /># dnf makecache<br /># dnf install -y redhat-lsb-core<br /># dnf install anydesk<br /># rpm -qi anydesk<br /># systemctl status anydesk.service<br /># exit<br />$ anydesk<br /><strong>Task:</strong><br />Создание загрузочных носителей<br /><strong>Decision:</strong><br /># fdisk -l<br />...<br />Диск /dev/sdb: 3,61 GiB, 3880452096 байт, 7579008 секторов<br />Disk model: Silicon-Power4G<br />Единицы: секторов по 1 * 512 = 512 байт<br />Размер сектора (логический/физический): 512 байт / 512 байт<br />Размер I/O (минимальный/оптимальный): 512 байт / 512 байт<br />Тип метки диска: gpt<br />Идентификатор диска: 2BAC44AA-F36D-461C-B12A-D251E7E9373F<br />Устр-во&nbsp;&nbsp;&nbsp; начало&nbsp;&nbsp; Конец Секторы Размер Тип<br />/dev/sdb1&nbsp;&nbsp;&nbsp; 2048 7578974 7576927&nbsp;&nbsp; 3,6G Microsoft basic data<br /># ls<br />Zorin-OS-16.1-Core-64-bit.iso<br /># dd if=Zorin-OS-16.1-Core-64-bit.iso of=/dev/sdb1 bs=8MB status=progress oflag=direct<br />3058237440 байт (3,1 GB, 2,8 GiB) скопирован, 659 s, 4,6 MB/s<br />382+1 записей получено<br />382+1 записей отправлено<br />3058237440 байт (3,1 GB, 2,8 GiB) скопирован, 659,39 s, 4,6 MB/s<br /><strong>Task:</strong><br />Развернуть Pxe сервер для развертывания Redos с загрузкой в Uefi по сети<br /><strong>Decision:</strong><br /># ifconfig<br />enp2s0: flags=4163&lt;UP,BROADCAST,RUNNING,MULTICAST&gt;&nbsp; mtu 1500<br />&nbsp;&nbsp;&nbsp; inet IpAddr1&nbsp; netmask Mask1&nbsp; broadcast IpAddr.255<br />&nbsp;&nbsp; &nbsp;...<br /># dnf install dhcp tftp-server syslinux httpd dnf-plugins-core -y<br /># mkdir /var/lib/tftpboot/pxelinux.cfg<br /># mkdir /var/lib/tftpboot/uefi<br /># mkdir -p /var/lib/tftpboot/images/REDOS<br /># cp /usr/share/syslinux/{chain.c32,mboot.c32,memdisk,menu.c32,pxelinux.0,ldlinux.c32,libutil.c32} /var/lib/tftpboot/<br /># chmod 777 /var/lib/tftpboot/pxelinux.0<br /># dnf download shim-x64 grub2-efi-x64 --downloaddir=/root/<br /># cd /root/<br /># rpm2cpio shim-x64-*.rpm | cpio -dimv<br /># rpm2cpio grub2-efi-x64-*.rpm | cpio -dimv<br /># cp ./boot/efi/EFI/BOOT/BOOTX64.EFI /var/lib/tftpboot/uefi<br /># cp ./boot/efi/EFI/redos/grubx64.efi /var/lib/tftpboot/uefi<br /># chmod 777 /var/lib/tftpboot/uefi/*.*<br /># mount -t iso9660 -o loop redos-MUROM-7.3.2-20211027.0-Everything-x86_64-DVD1.iso /mnt/<br /># cp -vR /mnt/* /var/lib/tftpboot/images/REDOS/<br /># umount /mnt/<br /># vim /etc/dhcp/dhcpd.conf<br /># cat /etc/dhcp/dhcpd.conf<br />non-authoritative;<br />allow bootp;<br />option space pxelinux;<br />option pxelinux.magic code 208 = string;<br />option pxelinux.configfile code 209 = text;<br />option pxelinux.pathprefix code 210 = text;<br />option pxelinux.reboottime code 211 = unsigned integer 32;<br />option architecture-type code 93 = unsigned integer 16;<br />subnet IpAddr.0 netmask Mask1 {<br />option routers IpAddr1;<br />range IpAddr.70 IpAddr.80;<br />class "pxeclients" {<br />match if substring (option vendor-class-identifier, 0, 9) = "PXEClient";<br />next-server IpAddr1;<br />if option architecture-type = 00:07 {<br />filename "uefi/grubx64.efi";<br />} <br />else {<br />filename "pxelinux.0";<br />}<br />}<br />} <br /># systemctl enable dhcpd --now<br /># vim /var/lib/tftpboot/pxelinux.cfg/default<br /># cat /var/lib/tftpboot/pxelinux.cfg/default<br />default menu.c32<br />PROMPT 0<br />TIMEOUT 150<br />MENU TITLE PXE Menu<br />LABEL REDOS 7.3<br />MENU LABEL REDOS 7.3<br />KERNEL images/REDOS/images/pxeboot/vmlinuz<br />APPEND initrd=images/REDOS/images/pxeboot/initrd.img ramdisk_size=128000 ip=dhcp inst.repo=http://IpAddr1/images/REDOS/ <br /># vim /var/lib/tftpboot/uefi/grub.cfg <br /># cat /var/lib/tftpboot/uefi/grub.cfg <br />function load_video { <br />insmod efi_gop &nbsp;<br />insmod efi_uga <br />insmod video_bochs <br />insmod video_cirrus <br />insmod all_video <br />} <br />load_video <br />set gfxpayload=keep <br />insmod gzio <br />menuentry 'REDOS 7.3' { <br />linux images/REDOS/images/pxeboot/vmlinuz ip=dhcp inst.repo=http://IpAddr1/images/REDOS/ <br />initrd images/REDOS/images/pxeboot/initrd.img <br />} <br /><strong>Task:</strong><br />Используем web-сервер для публикации файлов дистрибутива РЕД ОС в локальной сети.<br /><strong>Decision:</strong><br /># vim /etc/httpd/conf.d/pxeboot.conf <br /># cat /etc/httpd/conf.d/pxeboot.conf <br />Alias /images /var/lib/tftpboot/images <br />&lt;Directory /var/lib/tftpboot/images&gt; <br />Options Indexes FollowSymLinks <br />Require ip 127.0.0.1 IpAddr.0/24 <br />&lt;/Directory&gt;<br /># systemctl enable httpd --now<br /><strong>Task:</strong><br />Настройка и запуск службы tftp.<br /><strong>Decision:</strong><br /># vim /usr/lib/systemd/system/tftp.service<br /># cat /usr/lib/systemd/system/tftp.service<br />...<br />[Install]:<br />WantedBy=multi-user.target <br />Also=tftp.socket<br />...<br /># vim /usr/lib/systemd/system/tftp.socket<br /># cat /usr/lib/systemd/system/tftp.socket<br />...<br />[Unit] <br />Description=Tftp Server Activation Socket <br />[Socket] <br />ListenDatagram=0.0.0.0:69 <br />[Install] <br />WantedBy=sockets.target <br />...<br /># systemctl daemon-reload<br /># systemctl enable tftp --now<br /># ausearch -c 'httpd' --raw | audit2allow -M my-httpd<br /># semodule -i my-httpd.pp<br /><strong>Task:</strong><br />Автоматизация развертывания (kickstart)<br />Создать файл кикстарта, Записать файл на локальный или удаленный носитель, Создать загрузочный диск, с которого будет запускаться установка, Предоставить доступ к установочной структуре, Начать процесс установки.<br /><strong>Decision:</strong><br /># dnf install pykickstart -y<br /># cp /root/anaconda-ks.cfg /var/lib/tftpboot<br /># mv /var/lib/tftpboot/anaconda-ks.cfg /var/lib/tftpboot/ks.cfg<br /># vim /var/lib/tftpboot/pxelinux.cfg/default<br /># cat /var/lib/tftpboot/pxelinux.cfg/default<br />...<br />APPEND initrd=images/REDOS/images/pxeboot/initrd.img ramdisk_size=128000 ip=dhcp method=http://IpAddr1/images/REDOS/ devfs=nomount inst.ks=http://IpAddr1/ks.cfg <br /># vim /var/lib/tftpboot/uefi/grub.cfg<br /># cat /var/lib/tftpboot/uefi/grub.cfg<br />... { <br />linux images/REDOS/images/pxeboot/vmlinuz ip=dhcp kernel vmlinuz inst.repo=http://IpAddr1/images/REDOS/ inst.ks=http://IpAddr1/ks.cfg <br />initrd images/REDOS/images/pxeboot/initrd.img<br />} <br /># vim /var/lib/tftpboot/ks.cfg<br /># cat /var/lib/tftpboot/ks.cfg<br /># Здесь указываем раскладку клавиатуры<br />keyboard --vckeymap=us --xlayouts='us','ru' --switch='grp:alt_shift_toggle'<br /># Системная локаль<br />lang ru_RU.UTF-8<br /># Информация о сетевом интерфейсе и имя машины<br />network&nbsp; --bootproto=dhcp --device=enp2s0 --noipv6 --activate<br />network&nbsp; --hostname=hostname1337<br /># Пароль Root представлен в виде хэш-суммы<br />rootpw --iscrypted $6$DUu0yyOYMRbGS8gL$9zHYPsxROGEZdDKG0wnf7h8SGnKOp3V272De6oGTVUsz2uBLmEeiR6T6cInRN5dyWcxNXh5fVluEUTQ/3rmzB0<br /># Настройка сервисов (в данном случае сервис по обновлению меток времени и дат)<br />services --enabled="chronyd"<br /># Настройка временной зоны<br />timezone Europe/Moscow --isUtc<br />#Настройка локального пользователя<br />user --groups=wheel --name=mekka --password=$6$83fyYZ7KMS7G9t6A$E5/99/ffOwjUOo8THr1ngqGDdKMimpTZf3IT9S/SI98BTV7dta7GksLYnQEZjtqqyZQrwibSRlvYccRqHB7m8/ --iscrypted --gecos="Mekka"<br /># Настройка xorg при загрузке<br />xconfig&nbsp; --startxonboot<br /># Указание загрузочного сектора и тип структуры<br />bootloader --location=mbr --boot-drive=sda<br /># Удаление всей информации с партиций для последующей установки<br />clearpart --none --initlabel<br /># Здесь указана вся разметка диска<br />part /boot --fstype="xfs" --onpart=sda2<br />part biosboot --fstype="biosboot" --noformat --onpart=sda4<br />part pv.31 --fstype="lvmpv" --noformat --onpart=sda3<br />part /boot/efi --fstype="efi" --onpart=sda1 --fsoptions="umask=0077,shortname=winnt"<br />volgroup ro --noformat --useexisting<br />logvol swap&nbsp; --fstype="swap" --useexisting --name=swap --vgname=ro<br />logvol /home&nbsp; --fstype="xfs" --noformat --useexisting --name=home --vgname=ro<br />logvol /&nbsp; --fstype="ext4" --useexisting --name=root --vgname=ro<br />#дополнительные пакеты для установки<br />%packages<br />@^mate-desktop-environment<br />@backup-client<br />@base<br />@branding<br />@core<br />@desktop-debugging<br />@dial-up<br />@directory-client<br />@fonts<br />@guest-agents<br />@guest-desktop-agents<br />@input-methods<br />@internet-applications<br />@internet-browser<br />@java-platform<br />@mate-desktop<br />@multimedia<br />@network-file-system-client<br />@print-client<br />@x11<br />chrony<br />%end<br />#настройка аварийных дампов памяти в случае сбоев (оставить как есть)<br />%addon com_redhat_kdump --enable --reserve-mb='auto'<br />%end<br />#настройка анаконды (оставить как есть)<br />%anaconda<br />pwpolicy root --minlen=6 --minquality=1 --notstrict --nochanges --notempty<br />pwpolicy user --minlen=6 --minquality=1 --notstrict --nochanges --emptyok<br />pwpolicy luks --minlen=6 --minquality=1 --notstrict --nochanges --notempty<br />%end<br /><strong>Task:</strong><br />Настройка установки РЕД ОС по PXE через VNC вместо Kickstart<br /><strong>Decision:</strong><br /># vim /var/lib/tftpboot/pxelinux.cfg/default<br /># cat /var/lib/tftpboot/pxelinux.cfg/default<br />...<br />APPEND initrd=images/REDOS/images/pxeboot/initrd.img ramdisk_size=128000 ip=dhcp method=http://IpAddr1/images/REDOS/ devfs=nomount inst.vnc inst.vncpassword=tpassword<br /># vim /var/lib/tftpboot/uefi/grub.cfg<br /># cat /var/lib/tftpboot/uefi/grub.cfg<br />... { <br />linux images/REDOS/images/pxeboot/vmlinuz ip=dhcp kernel vmlinuz inst.repo=http://IpAddr1/images/REDOS/ inst.vnc inst.vncpassword=tpassword<br />initrd images/REDOS/images/pxeboot/initrd.img<br />}<br /><strong>Source:</strong></p>
<ul>
<li><a href="https://redos.red-soft.ru/base/other-soft/other-other/consultant/?sphrase_id=53349">https://redos.red-soft.ru/base/other-soft/other-other/consultant/?sphrase_id=53349</a></li>
<li><a href="https://wtuseri.astralinuthost.ru/pages/viewpage.action?pageId=61574227">https://wtuseri.astralinuthost.ru/pages/viewpage.action?pageId=61574227</a></li>
<li><a href="https://askubuntu.ru/questions/21203/kak-skry-t-pol-zovatelej-ot-e-krana-vxoda-v-gdm">https://askubuntu.ru/questions/21203/kak-skry-t-pol-zovatelej-ot-e-krana-vxoda-v-gdm</a></li>
<li><a href="https://computingforgeeks.com/how-to-install-gimp-on-centos-rhel-8-desktop/">https://computingforgeeks.com/how-to-install-gimp-on-centos-rhel-8-desktop/</a></li>
<li><a href="https://ru.wtuserihow.com/%D1%81%D0%BE%D0%B7%D0%B4%D0%B0%D1%82%D1%8C-ISO-%D1%84%D0%B0%D0%B9%D0%BB-%D0%B2-Linux">https://ru.wtuserihow.com/%D1%81%D0%BE%D0%B7%D0%B4%D0%B0%D1%82%D1%8C-ISO-%D1%84%D0%B0%D0%B9%D0%BB-%D0%B2-Linux</a></li>
<li><a href="https://losst.ru/zapis-diskov-v-ubuntu">https://losst.ru/zapis-diskov-v-ubuntu</a></li>
<li><a href="https://losst.ru/luchshie-analogi-paint-dlya-linux">https://losst.ru/luchshie-analogi-paint-dlya-linux</a></li>
<li><a href="https://computingforgeeks.com/how-to-install-anydesk-on-centos-rhel-8/">https://computingforgeeks.com/how-to-install-anydesk-on-centos-rhel-8/</a></li>
</ul>
<strong>Task:</strong><br>
В компьютерном классе по 20 компьютеров и в каждом надо было установить Microsoft Office. Для этого я написал скрипты инсталлятор и конфигуратор, которые позволяют мне выбрать дистрибутив, в котором я установливаю, саму программу для установки и настройки (не только офис)<br>
<strong>Decision:</strong><br>
$ vim Linux-Installer.sh<br>
$ cat Linux-Installer.sh<br>
#!/bin/bash<br>
checkcmd(){<br>
if [ $? -eq 0 ]; then<br>
&nbsp;&nbsp; &nbsp;echo ! The command was executed successfully<br>
else<br>
&nbsp;&nbsp; &nbsp;echo ! The command was executed with an error<br>
fi<br>
}&nbsp;<br>
#echo YOUR-PASSWORD | sudo -S sudo dnf update<br>
#checkcmd<br>
# https://stackoverflow.com/questions/226703/how-do-i-prompt-for-yes-no-cancel-input-in-a-linux-shell-script<br>
while true; do<br>
&nbsp;&nbsp; &nbsp;read -p "Do you want to install the program? (y/n) " yn<br>
&nbsp;&nbsp; &nbsp;case $yn in<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;[Yy]* )&nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "Select the distribution where you want to install the program (Centos 9 - 1 / Ubuntu 22.04 - 2 / Redos 7.3 - 3): "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read choicedistr<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;case "$choicedistr" in<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;1|Centos)&nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo dnf -y update<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "Select a program (Test - 0 / Sublime Text - 1 / Postgresql - 2 / PgAdmin - 3 / Git - 4 / Kvm - 5 / nfts-3g - 6 / libreoffice - 7): "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read choiceprogr<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;case "$choiceprogr" in<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;0)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo dnf -y update<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;1)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;# https://www.sublimetext.com/docs/linux_repositories.html#dnf<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo rpm -v --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo dnf config-manager --add-repo https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo dnf -y install sublime-text<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;2)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;# https://www.postgresql.org/download/linux/redhat/<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo dnf install -y https://download.postgresql.org/pub/repos/yum/reporpms/EL-9-x86_64/pgdg-redhat-repo-latest.noarch.rpm<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo dnf -qy module disable postgresql<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo dnf install -y postgresql15-server<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo /usr/pgsql-15/bin/postgresql-15-setup initdb<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo systemctl enable postgresql-15<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo systemctl start postgresql-15<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;3)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;# https://www.pgadmin.org/download/pgadmin-4-rpm/<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo rpm -i https://ftp.postgresql.org/pub/pgadmin/pgadmin4/yum/pgadmin4-redhat-repo-2-1.noarch.rpm<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo yum install -y pgadmin4<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo yum install -y pgadmin4-desktop<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo yum install -y pgadmin4-web<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;sudo /usr/pgadmin4/bin/setup-web.sh<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo yum upgrade -y pgadmin4<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;4)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;# https://unixcop.com/how-to-install-git-on-centos-9-stream-fedora/<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo dnf -y install git<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;git --version<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;5)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;# https://technixleo.com/install-kvm-on-centos-alma-rhel-9/<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;egrep -c '(vmx|svm)' /proc/cpuinfo<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo dnf install -y qemu-kvm qemu-img libvirt virt-install libvirt-client virt-manager<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;lsmod | grep kvm<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo systemctl enable --now libvirtd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;sudo virt-host-validate&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;6)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;# https://itisgood.ru/2019/03/26/kak-smontirovat-disk-ntfs-na-centos-rhel-scientific-linux/<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo yum -y install epel-release<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo yum -y install ntfs-3g<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;7)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo dnf -y install libreoffice<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;esac<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;2|u|U|Ubuntu)&nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo apt -y update<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo apt -y upgrade<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "Select a program (Test - 0 / Net-Tools - 1 / Ssh - 2): "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read choiceprogr<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;case "$choiceprogr" in<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;0)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo apt-get -y update<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;1)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo apt-get install net-tools<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;2)#https://help.reg.ru/support/servery-vps/oblachnyye-servery/rabota-s-serverom/kak-ustanovit-i-nastroit-ssh<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo apt-get install ssh<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo apt-get install openssh-server<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;systemctl status ssh<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;esac<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;exit 0<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;3|r|R|Redos)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo yum -y update<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "Select a program (Test - 0 / Office - 1 / Playonlinux - 2): "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read choiceprogr<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;case "$choiceprogr" in<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;0)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo yum -y update<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;1)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo yum -y update<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;wine /LINKS/MS\ Office\ 2007-10-13/Office_Professional_Plus_2007_W32_Russia/SETUP.EXE<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd&nbsp;&nbsp; &nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;2)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo yum -y update<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo touch /etc/yum.repos.d/playonlinux.repo<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo echo '[playonlinux]<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;name=PlayOnLinux Official repository<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;baseurl=http://rpm.playonlinux.com/fedora/yum/base<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;enable=1<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;gpgcheck=0<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;gpgkey=http://rpm.playonlinux.com/public.gpg' &gt; /etc/yum.repos.d/playonlinux.repo<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;cat /etc/yum.repos.d/playonlinux.repo<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo yum -y install playonlinux nc jq<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo reboot&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;esac<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;*)&nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo "Nothing was entered."<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;esac&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;[Nn]* )&nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;exit<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;* )&nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo "Please answer yes or no."<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;esac<br>
done<br>
exit 0<br>
$ ./Linux-Installer.sh<br>
Do you want to install the program? (y/n) y<br>
Select the distribution where you want to install the program (Centos 9 - 1 / Ubuntu 22.04 - 2 / Redos 7.3 - 3): 1<br>
Select a program (Test - 0 / Sublime Text - 1 / Postgresql - 2 / PgAdmin - 3 / Git - 4 / Kvm - 5 / nfts-3g - 6 / libreoffice - 7): 0<br>
Do you want to install the program? (y/n) y<br>
Select the distribution where you want to install the program (Centos 9 - 1 / Ubuntu 22.04 - 2 / Redos 7.3 - 3): 2<br>
Select a program (Test - 0 / Net-Tools - 1 / Ssh - 2): 0<br>
$ vim Linux-Config.sh<br>
$ cat Linux-Config.sh<br>
#!/bin/bash&nbsp;<br>
checkcmd(){<br>
if [ $? -eq 0 ]; then<br>
&nbsp;&nbsp; &nbsp;echo ! The command was executed successfully<br>
else<br>
&nbsp;&nbsp; &nbsp;echo ! The command was executed with an error<br>
fi<br>
}<br>
# https://stackoverflow.com/questions/226703/how-do-i-prompt-for-yes-no-cancel-input-in-a-linux-shell-script<br>
while true; do<br>
&nbsp;&nbsp; &nbsp;read -p "Do you want to configure the program? (y/n) " yn<br>
&nbsp;&nbsp; &nbsp;case $yn in<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;[Yy]* )&nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "Select the distribution where you want to configure the program (Redhat - 1 / Debian - 2): "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read choicedistr<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;case "$choicedistr" in<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;1|r|R|Redhat)&nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo dnf -y update<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "Select a program (Test - 0 / Disabling Lamp - 1 / Starting Lamp - 2 / Add users in postgressql - 3 / Moving linux folders to another disk - 4): "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read choiceprogr<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;case "$choiceprogr" in<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;0)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo dnf -y update<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;1)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo service apache2 stop<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo service mysql stop<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;2)<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo service apache2 start<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo service mysql start<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;3) #https://www.dmosk.ru/miniinstruktions.php?mini=postgresql-users&amp;ysclid=lig0a2xuou515754413#create<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "Please come up with a new user: "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read userdb<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "Please come up with a new password: "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read passwdb<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;#echo YOUR-PASSWORD | sudo -S&nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;cd /tmp<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;sudo -u postgres -H -- psql -d template1 -c "CREATE USER $userdb WITH PASSWORD '$passwdb';"<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;#psql -U postgres -d template1 -c "CREATE USER tuser0 WITH PASSWORD 'Tpsswd';"<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "Please come up with a new base: "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read namedb<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;sudo -u postgres -H -- psql -d template1 -c "CREATE database $namedb;"<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;sudo -u postgres -H -- psql -d template1 -c "GRANT ALL PRIVILEGES ON DATABASE "$namedb" to $userdb;"<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;sudo -u postgres -H -- psql -d template1 -c "\c $namedb;"<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;sudo -u postgres -H -- psql -d template1 -c "GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO "$userdb";"<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;4) #http://sysengineering.ru/notes/peremeschenie-papok-linux-na-drugoy-disk?ysclid=lisfix46x1712981898<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;lsblk<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "USB device for moving the base (hint above): "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read mntusb<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo fdisk $mntusb<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;lsblk<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "USB device for moving the base (hint above): "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read mntusb1<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "Enter the file system type: "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read mntfs<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo mkfs -t $mntfs $mntusb1<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo mount $mntusb1 /mnt<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;shopt -s dotglob<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "Which directory do you need to move: "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read movedir<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo rsync -aulvXpogtr $movedir/* /mnt<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;ls -Zd $movedir<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;ls -Zd /mnt<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "Change the security settings of a new folder (hint above): "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read mntset<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo chcon -t $mntset /mnt<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;ls -Zd /mnt<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo umount /mnt<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo blkid<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo -n "Enter the UUID of the disk (hint above): "<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;read mntuid<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo sh -c "echo 'UUID=$mntuid&nbsp;&nbsp; $movedir&nbsp; $mntfs&nbsp; defaults,noatime,nofail 0 2' &gt;&gt; /etc/fstab"<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo cat /etc/fstab | grep $mntfs<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo mv $movedir $movedir.back<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo mkdir $movedir<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo YOUR-PASSWORD | sudo -S sudo mount -av<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;checkcmd<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;ls $movedir<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;lsblk&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;esac<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;2|d|D|Debian)&nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo "deb"<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;exit 0<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;*)&nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo "Nothing was entered."<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;esac&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;[Nn]* )&nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;exit<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;* )&nbsp;<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;echo "Please answer yes or no."<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;;;<br>
&nbsp;&nbsp; &nbsp;esac<br>
done<br>
exit 0<br>
$ ./Linux-Config.sh<br>
Do you want to configure the program? (y/n) y<br>
Select the distribution where you want to configure the program (Redhat - 1 / Debian - 2): 1<br>
Select a program (Test - 0 / Disabling Lamp - 1 / Starting Lamp - 2 / Add users in postgressql - 3 / Moving linux folders to another disk - 4): 0<br>
Do you want to configure the program? (y/n) n<br>
<strong>Task:</strong><br>
Столкнулся с такой проблемой, что маленький неттоп флешки не читает, он не был добавлен в домен и антивирус на нем не стоял. Убедимся на другой машине, в моем случае ноутбуке, что флешка спокойно видит на нем файлы.&nbsp;&nbsp; &nbsp;То есть это чистая флешка, не зараженная, и попробуем ее вставить в тот проблемный неттоп. Тут мы увидим, что во флешке другая информация будет. Как будто в самой флешке отображается сама флешка, и если ее открыть (что делать не стоит) тот там и будут наши файлы. на самом деле они будут зашифрованны и флешка заражена. Надо это исправлять. В тот момент у нас не было в неттопе никакого антивируса, поэтому я установил бесплатный антивирус Касперский FREE с официального сайта. И вот, он выдал в момент запуска после установки рекомендации по устранении проблм в компьютере. - Жмем устранить и перезагрузимся - В следующем запуске антивирус покажет информацию об устранении проблем, и можем сразу вставить флешку в неттопе. Тут мы увидим, что антвирус удалил какой-то файл (это и есть вирус) Открываем саму флешку после удаления вируса, а там пустой файл, хотя система показывает, что флешка заполнена. Он содержит зашифрованные файлы. Давайте попробуем их восстановить. Есть скрипт, который возвращает данные. Вставьте этот файл на флешку - запустите его - увидите файл и папку с файлами, которые ему удалось восстановить - Все готово, и неттоп мы подлечили, и данные со флешки восстановили, и антивирус бесплатный установили, и главное что этот бюджетный вариант с восстановлением вполне корректно работает.<br>
<strong>Decision:</strong><br>
$ vim Windows-FlashDriveRecovery.bat<br>
$ cat Windows-FlashDriveRecovery.bat<br>
dir /AS /B &gt; list.txt&nbsp;<br>
FOR /F "eol=# tokens=1* delims=:" %%i in (list.txt) do (&nbsp;<br>
attrib -s -h -r "%%i"&nbsp;<br>
)&nbsp;<br>
pause<br>
<strong>Task:</strong><br>
Администрирование локальных, виртуальных и облачных серверов. Установить виртуальный сервер AltLinux в Hyper-V<br>
<strong>Decision:</strong><br>
PS C:\Windows\system32&gt; $ram=1*1024*1024*1024<br>
PS C:\Windows\system32&gt; $ram<br>
1073741824<br>
PS C:\Windows\system32&gt; $hdd=10*1024*1024*1024<br>
PS C:\Windows\system32&gt; $hdd<br>
10737418240<br>
PS C:\Windows\system32&gt; NEW-VM -Name Alt -MemoryStartupBytes $ram -NewVHDPath 'C:\Data\VM\Alt\Alt.vhdx'-NewVHD<br>
SizeBytes $hdd -Path 'C:\Data\VM\Alt'<br>
PS C:\Windows\system32&gt; Start-VM -name Alt<br>
PS C:\Windows\system32&gt; Get-VM<br>
Name State&nbsp;&nbsp; CPUUsage(%) MemoryAssigned(M) Uptime&nbsp;&nbsp; Status<br>
---- -----&nbsp;&nbsp; ----------- ----------------- ------&nbsp;&nbsp; ------<br>
Alt&nbsp; Off&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 00:00:00 Работает нормально<br>
<strong>Task:</strong><br>
Администрирование локальных, виртуальных и облачных серверов. Set up an ActiveDirectory/Login<br>
<strong>Decision:</strong><br>
$ ssh -X tuser@thost1<br>
$ su -<br>
# apt-get install task-auth-ad-sssd<br>
# net time set -S thost.ru<br>
# system-auth write ad thost.ru thost1 thost 'tuser' 'tpassword'<br>
Using short domain name -- thost<br>
Joined 'thost1' to dns domain 'thost.ru'<br>
Successfully registered hostname with DNS<br>
failed to call wbcGetDisplayName: WBC_ERR_WINBIND_NOT_AVAILABLE<br>
Could not lookup sid S-1-5-21-965402400-3010625364-1855727791-513<br>
failed to call wbcGetDisplayName: WBC_ERR_WINBIND_NOT_AVAILABLE<br>
Could not lookup sid S-1-5-21-965402400-3010625364-1855727791-512<br>
# wbinfo -t<br>
checking the trust secret for domain thost via RPC calls succeeded<br>
# acc<br>
2 keyboards found<br>
qt.qpa.xcb: could not connect to display<br>
qt.qpa.plugin: Could not load the Qt platfothost plugin "xcb" in "" even though it was found.<br>
This applthostation failed to start because no Qt platfothost plugin could be initialized. Reinstalling the applthostation may fix this problem.<br>
Available platfothost plugins are: eglfs, linuxfb, minimal, minimalegl, offscreen, vnc, xcb.<br>
# exit<br>
$ exit<br>
$ ssh -X tuser@thost1<br>
$ su -<br>
# acc<br>
2 keyboards found<br>
QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/.private/root/runtime-root'<br>
libpng warning: thostCP: known incorrect sRGB profile<br>
libpng warning: thostCP: known incorrect sRGB profile<br>
libpng warning: thostCP: known incorrect sRGB profile<br>
libpng warning: thostCP: known incorrect sRGB profile<br>
libpng warning: thostCP: known incorrect sRGB profile<br>
WARNING: (alterator lookout evaluation): imported module (alterator presentation events) overrides core binding `when'<br>
libpng warning: thostCP: known incorrect sRGB profile<br>
libpng warning: thostCP: known incorrect sRGB profile<br>
libpng warning: thostCP: known incorrect sRGB profile<br>
libpng warning: thostCP: known incorrect sRGB profile<br>
# vim /etc/net/ifaces/eth0/resolv.conf<br>
# cat /etc/net/ifaces/eth0/resolv.conf<br>
nameserver IpAddr1<br>
# hostnamectl set-hostname thost1.thost.ru<br>
# cat /etc/resolv.conf<br>
# Generated by resolvconf<br>
# Do not edit manually, use<br>
# /etc/net/ifaces/&lt;interface&gt;/resolv.conf instead.<br>
search thost.ru<br>
nameserver 127.0.0.1<br>
# vim /etc/resolv.conf<br>
# cat /etc/resolvconf.conf<br>
# Configuration for resolvconf(8)<br>
# See resolvconf.conf(5) for details<br>
resolv_conf_head='# Do not edit manually, use\n# /etc/net/ifaces/&lt;interface&gt;/resolv.conf instead.'<br>
resolv_conf=/etc/resolv.conf<br>
# These interfaces will always be processed first.<br>
interface_order='lo lo[0-9]* lo.*'<br>
# These interfaces will be processed next, unless they have a metrthost.<br>
dynamthost_order='tap[0-9]* tun[0-9]* vpn vpn[0-9]* wg[0-9]* ppp[0-9]* ippp[0-9]*'<br>
#Configuration files for named subscriber.<br>
named_zones=/var/lib/bind/etc/resolvconf-zones.conf<br>
named_options=/var/lib/bind/etc/resolvconf-options.conf<br>
#Configuration files for dnsmasq subscriber.<br>
dnsmasq_conf=/etc/dnsmasq.conf.d/60-resolvconf<br>
dnsmasq_resolv=/etc/resolv.conf.dnsmasq<br>
name_servers=127.0.0.1<br>
# vim /etc/resolvconf.conf<br>
# cat /etc/resolvconf.conf<br>
# Configuration for resolvconf(8)<br>
# See resolvconf.conf(5) for details<br>
resolv_conf_head='# Do not edit manually, use\n# /etc/net/ifaces/&lt;interface&gt;/resolv.conf instead.'<br>
resolv_conf=/etc/resolv.conf<br>
# These interfaces will always be processed first.<br>
#interface_order='lo lo[0-9]* lo.*'<br>
interface_order='lo lo[0-9]* lo.* eth0'<br>
search_domains=thost.ru<br>
# These interfaces will be processed next, unless they have a metrthost.<br>
dynamthost_order='tap[0-9]* tun[0-9]* vpn vpn[0-9]* wg[0-9]* ppp[0-9]* ippp[0-9]*'<br>
#Configuration files for named subscriber.<br>
named_zones=/var/lib/bind/etc/resolvconf-zones.conf<br>
named_options=/var/lib/bind/etc/resolvconf-options.conf<br>
#Configuration files for dnsmasq subscriber.<br>
dnsmasq_conf=/etc/dnsmasq.conf.d/60-resolvconf<br>
dnsmasq_resolv=/etc/resolv.conf.dnsmasq<br>
#name_servers=127.0.0.1<br>
# resolvconf -u<br>
# cat /etc/resolv.conf<br>
# Generated by resolvconf<br>
# Do not edit manually, use<br>
# /etc/net/ifaces/&lt;interface&gt;/resolv.conf instead.<br>
search thost.ru<br>
nameserver IpAddr1<br>
...<br>
nameserver 8.8.8.8<br>
# hostname<br>
thost1.thost.ru<br>
# dig _kerberos._udp.thost.ru SRV | grep ^_kerberos<br>
_kerberos._udp.thost.ru. 600 IN SRV 0 100 88 M-1.thost.ru.<br>
...<br>
_kerberos._udp.thost.ru. 600 IN SRV 0 100 88 T-1.thost.ru.<br>
# dig _kerberos._tcp.thost.ru SRV | grep ^_kerberos<br>
_kerberos._tcp.thost.ru. 600 IN SRV 0 100 88 M-c.thost.ru.<br>
...<br>
_kerberos._tcp.thost.ru. 600 IN SRV 0 100 88 T-1.thost.ru.<br>
# cat /etc/krb5.conf | grep default_realm<br>
default_realm = thost.ru<br>
# default_realm = EXAMPLE.COM<br>
# cat /etc/krb5.conf | grep dns_lookup_realm<br>
dns_lookup_realm = false<br>
# cat /etc/krb5.conf | grep dns_lookup_kdc<br>
dns_lookup_kdc = true<br>
# exit<br>
$ ssh -X tuser@thost1<br>
# kinit tuser<br>
# klist<br>
Tthostket cache: KEYRING:persistent:0:krb_ccache_CCjHpN1<br>
Default principal: a-r@thost.ru<br>
Valid starting&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Expires&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Servthoste principal<br>
10.08.2022 12:30:34&nbsp; 10.08.2022 22:30:34&nbsp; krbtgt/thost.ru@thost.ru<br>
&nbsp;&nbsp; &nbsp;renew until 17.08.2022 12:30:32<br>
# apt-get install samba-client<br>
# cat /etc/samba/smb.conf | grep realm<br>
&nbsp;&nbsp; &nbsp;realm = thost.ru<br>
# cat /etc/samba/smb.conf | grep workgroup<br>
&nbsp;&nbsp; &nbsp;workgroup = thost<br>
# cat /etc/samba/smb.conf | grep netbios<br>
&nbsp;&nbsp; &nbsp;netbios name = thost1<br>
# cat /etc/samba/smb.conf | grep security<br>
&nbsp;&nbsp; &nbsp;security = ads<br>
# cat /etc/samba/smb.conf | grep method<br>
&nbsp;&nbsp; &nbsp;kerberos method = system keytab<br>
# cat /etc/samba/smb.conf | grep idmap<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;idmap config * : range = 200000-2000200000<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;idmap config * : backend = sss<br>
# vim /etc/samba/smb.conf<br>
# cat /etc/samba/smb.conf | grep idmap<br>
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;idmap config * : range = 200000-2000200000<br>
;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; idmap config * : backend = sss<br>
&nbsp;&nbsp; &nbsp;idmap config * : backend = tdb<br>
# testpathost<br>
Load smb config files from /etc/samba/smb.conf<br>
Loaded servthostes file OK.<br>
Weak crypto is allowed<br>
Server role: ROLE_DOMAIN_MEMBER<br>
Press enter to see a dump of your servthoste definitions<br>
# Global parameters<br>
[global]<br>
&nbsp;&nbsp; &nbsp;kerberos method = system keytab<br>
&nbsp;&nbsp; &nbsp;machine password timeout = 0<br>
&nbsp;&nbsp; &nbsp;realm = thost.ru<br>
&nbsp;&nbsp; &nbsp;security = ADS<br>
&nbsp;&nbsp; &nbsp;template homedir = /home/thost.ru/%U<br>
&nbsp;&nbsp; &nbsp;template shell = /bin/bash<br>
&nbsp;&nbsp; &nbsp;winbind use default domain = Yes<br>
&nbsp;&nbsp; &nbsp;workgroup = thost<br>
&nbsp;&nbsp; &nbsp;idmap config * : range = 200000-2000200000<br>
&nbsp;&nbsp; &nbsp;idmap config * : backend = tdb<br>
[share]<br>
&nbsp;&nbsp; &nbsp;comment = Commonplace<br>
&nbsp;&nbsp; &nbsp;path = /srv/share<br>
&nbsp;&nbsp; &nbsp;read only = No<br>
[homes]<br>
&nbsp;&nbsp; &nbsp;browseable = No<br>
&nbsp;&nbsp; &nbsp;comment = Home Directory for '%u'<br>
&nbsp;&nbsp; &nbsp;read only = No<br>
# net ads join -U tuser<br>
Enter tuser's password:<br>
Using short domain name -- thost<br>
Joined 'thost1' to dns domain 'thost.ru'<br>
No DNS domain configured for thost1. Unable to perfothost DNS Update.<br>
DNS update failed: NT_STATUS_INVALID_PARAMETER<br>
# cat /etc/hosts<br>
127.0.0.1&nbsp;&nbsp; localhost.localdomain localhost<br>
# vim /etc/hosts<br>
# cat /etc/hosts<br>
127.0.0.1&nbsp;&nbsp; localhost.localdomain localhost<br>
127.0.0.1&nbsp;&nbsp; thost1.thost.ru thost1<br>
# net ads join -U tuser<br>
Enter tuser's password:<br>
Using short domain name -- thost<br>
Joined 'thost1' to dns domain 'thost.ru'<br>
kerberos_kinit_password thost1$@thost.ru failed: Preauthentthostation failed<br>
DNS update failed: kinit failed: Preauthentthostation failed<br>
# vim /etc/hosts<br>
# cat /etc/hosts<br>
127.0.0.1&nbsp;&nbsp; thost1.thost.ru thost1<br>
# net ads join -U tuser<br>
Enter tuser's password:<br>
Using short domain name -- thost<br>
Joined 'thost1' to dns domain 'thost.ru'<br>
# klist -k -e<br>
Keytab name: FILE:/etc/krb5.keytab<br>
KVNO Principal<br>
---- --------------------------------------------------------------------------<br>
9 host/thost1.thost.ru@thost.ru (aes256-cts-hmac-sha1-96)<br>
9 host/thost1@thost.ru (aes256-cts-hmac-sha1-96)<br>
9 host/thost1.thost.ru@thost.ru (aes128-cts-hmac-sha1-96)<br>
9 host/thost1@thost.ru (aes128-cts-hmac-sha1-96)<br>
9 host/thost1.thost.ru@thost.ru (DEPRECATED:arcfour-hmac)<br>
9 host/thost1@thost.ru (DEPRECATED:arcfour-hmac)<br>
9 thost1$@thost.ru (aes256-cts-hmac-sha1-96)<br>
9 thost1$@thost.ru (aes128-cts-hmac-sha1-96)<br>
9 thost1$@thost.ru (DEPRECATED:arcfour-hmac)<br>
8 host/thost1.thost.ru@thost.ru (aes256-cts-hmac-sha1-96)<br>
8 host/thost1@thost.ru (aes256-cts-hmac-sha1-96)<br>
8 host/thost1.thost.ru@thost.ru (aes128-cts-hmac-sha1-96)<br>
8 host/thost1@thost.ru (aes128-cts-hmac-sha1-96)<br>
8 host/thost1.thost.ru@thost.ru (DEPRECATED:arcfour-hmac)<br>
8 host/thost1@thost.ru (DEPRECATED:arcfour-hmac)<br>
8 thost1$@thost.ru (aes256-cts-hmac-sha1-96)<br>
8 thost1$@thost.ru (aes128-cts-hmac-sha1-96)<br>
8 thost1$@thost.ru (DEPRECATED:arcfour-hmac)<br>
# apt-get install sssd-ad<br>
# cat /etc/sssd/sssd.conf<br>
[sssd]<br>
config_file_version = 2<br>
servthostes = nss, pam<br>
# Managed by system facility command:<br>
## control sssd-drop-privileges unprivileged|privileged|default<br>
user = _sssd<br>
# SSSD will not start if you do not configure any domains.<br>
domains = thost.ru<br>
[nss]<br>
[pam]<br>
[domain/thost.ru]<br>
id_provider = ad<br>
auth_provider = ad<br>
chpass_provider = ad<br>
access_provider = ad<br>
default_shell = /bin/bash<br>
fallback_homedir = /home/%d/%u<br>
debug_level = 0<br>
; cache_credentials = false<br>
ad_gpo_ignore_unreadable = true<br>
ad_gpo_access_control = pethostissive<br>
ad_update_samba_machine_account_password = true<br>
# vim /etc/sssd/sssd.conf<br>
# cat /etc/sssd/sssd.conf<br>
[sssd]<br>
config_file_version = 2<br>
servthostes = nss, pam<br>
# Managed by system facility command:<br>
## control sssd-drop-privileges unprivileged|privileged|default<br>
#user = _sssd<br>
user=root<br>
# SSSD will not start if you do not configure any domains.<br>
domains = thost.ru<br>
[nss]<br>
[pam]<br>
[domain/thost.ru]<br>
id_provider = ad<br>
auth_provider = ad<br>
chpass_provider = ad<br>
access_provider = ad<br>
;ldap_id_mapping = False<br>
default_shell = /bin/bash<br>
fallback_homedir = /home/%d/%u<br>
debug_level = 0<br>
;use_fully_qualified_names = True<br>
; cache_credentials = True<br>
ad_gpo_ignore_unreadable = true<br>
ad_gpo_access_control = pethostissive<br>
ad_update_samba_machine_account_password = true<br>
# grep sss /etc/nsswitch.conf<br>
passwd: files sss<br>
shadow: tcb files sss<br>
group: files [SUCCESS=merge] sss role<br>
# control system-auth sss<br>
# servthoste sssd status<br>
active<br>
# servthoste sssd start<br>
# getent passwd tuser<br>
tuser:*:1-9:1-3:в-н:/home/thost.ru/tuser:/bin/bash<br>
# id tuser<br>
uid=1-9(tuser) gid=1-3(пользователи домена) группы=1-3(пользователи домена),1-8(администраторы dhcp),1-0(I-s),11-0(пользователи филиалы),1-1(tusert_users),1-9(i-n)<br>
# net ads info<br>
LDAP server: IpAddr2<br>
LDAP server name: MOW-1.thost.ru<br>
Realm: thost.ru<br>
Bind Path: dc=thost,dc=RU<br>
LDAP port: 389<br>
Server time: Ср, 10 авг 2022 13:08:06 +08<br>
KDC server: IpAddr2<br>
Server time offset: 0<br>
Last machine account password change: Ср, 10 авг 2022 12:50:51 +08<br>
# net ads testjoin<br>
Join is OK<br>
# cat /etc/lightdm/lightdm.conf | grep greeter-hide-<br>
# greeter-hide-users = True to hide the user list<br>
#greeter-hide-users=false<br>
greeter-hide-users = true<br>
# cat /etc/lightdm/lightdm-gtk-greeter.conf | grep show-language<br>
show-language-selector = false<br>
# cat /etc/lightdm/lightdm-gtk-greeter.conf | grep show-indthostators<br>
# vim /etc/lightdm/lightdm-gtk-greeter.conf<br>
# cat /etc/lightdm/lightdm-gtk-greeter.conf | grep show-indthostators<br>
show-indthostators=~a11y;~power;~session;~language<br>
# vim /etc/lightdm/lightdm-gtk-greeter.conf<br>
# cat /etc/lightdm/lightdm-gtk-greeter.conf | grep enter-<br>
enter-username = true<br>
# reboot<br>
$ ssh -X tuser@thost1<br>
<strong>Decision:</strong><br>
$ su -<br>
# apt-get install libnss-role<br>
# groupadd -r localadmins<br>
groupadd: группа «localadmins» уже существует<br>
# groupadd -r remote<br>
groupadd: группа «remote» уже существует<br>
# control sshd-allow-groups enabled<br>
# sed -i 's/AllowGroups.*/AllowGroups = remote/' /etc/openssh/sshd_config<br>
# roleadd users cdwriter cdrom audio proc radio camera floppy xgrp scanner uucp fuse<br>
# roleadd localadmins wheel remote vboxusers<br>
# roleadd 'Domain Users' users<br>
Error 156: No such group<br>
# roleadd 'Пользователи домена' users<br>
# roleadd 'Администраторы домена' localadmins<br>
# rolelst<br>
users:cdwriter,cdrom,audio,proc,radio,camera,floppy,xgrp,scanner,uucp,fuse,video,vboxusers,vboxadd<br>
localadmins:wheel,remote,vboxusers,vboxadd<br>
пользователи домена:users<br>
администраторы домена:localadmins<br>
powerusers:remote,vboxadd,vboxusers<br>
vboxadd:vboxsf<br>
# id tuser<br>
uid=1-9(tuser) gid=1-3(пользователи домена) группы=1-3(пользователи домена),11-0(пользователи филиалы),1-9(i-n),1-0(I-s),1-1(tusert_users),1-8(администраторы dhcp),100(users),80(cdwriter),22(cdrom),81(audio),19(proc),83(radio),440(camera),71(floppy),466(xgrp),467(scanner),14(uucp),483(fuse),488(video),481(vboxusers),455(vboxadd),454(vboxsf)<br>
# roleadd 'I-s' localadmins<br>
# roleadd 'I-s' wheel<br>
# rolelst<br>
users:cdwriter,cdrom,audio,proc,radio,camera,floppy,xgrp,scanner,uucp,fuse,video,vboxusers,vboxadd<br>
localadmins:wheel,remote,vboxusers,vboxadd<br>
пользователи домена:users<br>
администраторы домена:localadmins<br>
I-s:localadmins<br>
powerusers:remote,vboxadd,vboxusers<br>
vboxadd:vboxsf<br>
# exit<br>
$ exit<br>
$ ssh -X tuser@thost1<br>
$ su -<br>
# id tuser<br>
uid=1-9(tuser) gid=1-3(пользователи домена) группы=1-3(пользователи домена),11-0(пользователи филиалы),1-9(i-n),1-0(I-s),1-1(tusert_users),1-8(администраторы dhcp),100(users),80(cdwriter),22(cdrom),81(audio),19(proc),83(radio),440(camera),71(floppy),466(xgrp),467(scanner),14(uucp),483(fuse),488(video),481(vboxusers),455(vboxadd),454(vboxsf),101(localadmins),10(wheel),110(remote)<br>
<strong>Task:</strong><br>
Администрирование локальных, виртуальных и облачных серверов. Добавить сетевые папки<br>
<strong>Decision:</strong><br>
# apt-get install autofs<br>
# vim /etc/auto.master<br>
# cat /etc/auto.master<br>
# Fothostat of this file:<br>
# mountpoint map options<br>
# For details of the fothostat look at autofs(8).<br>
/mnt/auto&nbsp;&nbsp; /etc/auto.tab&nbsp;&nbsp; -t 5<br>
/mnt/net&nbsp;&nbsp;&nbsp; /etc/auto.avahi -t 120<br>
/mnt/.tdirectory&nbsp; /etc/auto.samba --ghost<br>
# vim /etc/auto.samba<br>
# cat /etc/auto.samba<br>
s&nbsp;&nbsp;&nbsp; -fstype=cifs,multiuser,cruid=$USER,sec=krb5,domain=thost.ru,vers=1.0 ://thost/tdirectory1<br>
o&nbsp;&nbsp;&nbsp; -fstype=cifs,multiuser,cruid=$USER,sec=krb5,domain=thost.ru,vers=1.0 ://thost/tdirectory2<br>
# systemctl enable autofs<br>
# systemctl start autofs<br>
# ls -la /mnt/.tdirectory/<br>
drwxr-xr-x 4 root root&nbsp;&nbsp;&nbsp; 0 авг 11 14:09 .<br>
drwxr-xr-x 5 root root 4096 авг 11 14:09 ..<br>
d????????? ? ?&nbsp;&nbsp;&nbsp; ?&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ?&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ? o<br>
d????????? ? ?&nbsp;&nbsp;&nbsp; ?&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ?&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ? s<br>
<strong>Task:</strong><br>
Администрирование локальных, виртуальных и облачных серверов. Creating a Network Bridge interface<br>
<strong>Decision:</strong><br>
# mkdir /etc/net/ifaces/tethernet1<br>
# cp /etc/net/ifaces/tethernet/* /etc/net/ifaces/tethernet1<br>
# rm -f /etc/net/ifaces/tethernet/{i,r}*<br>
# ls /etc/net/ifaces/tethernet1/<br>
ipv4address&nbsp; options&nbsp; resolv.conf<br>
# cat /etc/net/ifaces/tethernet1/options<br>
BOOTPROTO=dhcp<br>
TYPE=eth<br>
NM_CONTROLLED=yes<br>
DISABLED=yes<br>
CONFIG_WIRELESS=no<br>
SYSTEMD_BOOTPROTO=dhcp4<br>
CONFIG_IPV4=yes<br>
SYSTEMD_CONTROLLED=no<br>
# vim /etc/net/ifaces/tethernet1/options<br>
# ls /etc/net/ifaces/<br>
default&nbsp; tethernet&nbsp; lo&nbsp; unknown&nbsp; tethernet1<br>
# vim /etc/net/ifaces/tethernet1/options<br>
# vim /etc/net/ifaces/tethernet1/options<br>
# cat /etc/net/ifaces/tethernet1/options<br>
BOOTPROTO=static<br>
CONFIG_WIRELESS=no<br>
CONFIG_IPV4=yes<br>
HOST='tethernet'<br>
ONBOOT=yes<br>
TYPE=bri<br>
# ls /etc/net/ifaces/tethernet/<br>
ipv4address&nbsp; options&nbsp; resolv.conf<br>
# service network restart<br>
<strong>Task:</strong><br>
Администрирование базы данных. Настройка сервера Postgresql+Pgadmin<br>
<strong>Decision:</strong><br>
# apt-get update<br>
# apt-get install postgresql12-server<br>
# /etc/init.d/postgresql initdb<br>
# systemctl start postgresql<br>
# systemctl enable postgresql<br>
# pg_isready<br>
<strong>Decision:</strong><br>
# psql -U postgres<br>
postgres=# CREATE USER tbuser WITH PASSWORD 'tbpassword';<br>
postgres=# CREATE DATABASE tbbase;<br>
postgres=# GRANT ALL PRIVILEGES ON DATABASE tbbase to tbuser;<br>
postgres=# psql -U postgres -c "\l+"<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Список баз данных<br>
&nbsp;&nbsp;&nbsp;&nbsp; Имя&nbsp;&nbsp;&nbsp;&nbsp; | Владелец | Кодировка | LC_COLLATE&nbsp; |&nbsp; LC_CTYPE&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp; Права доступа&nbsp;&nbsp;&nbsp;&nbsp; | Размер&nbsp; | Табл. пространство |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Опис<br>
ание&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;<br>
-------------+----------+-----------+-------------+-------------+-----------------------+---------+--------------------+----------------------<br>
----------------------<br>
&nbsp;tbbase | postgres | UTF8&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | ru_RU.UTF-8 | ru_RU.UTF-8 | =Tc/postgres&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; +| 8041 kB | pg_default&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | postgres=CTc/postgres+|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | tbuser=CTc/postgres&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
&nbsp;postgres&nbsp;&nbsp;&nbsp; | postgres | UTF8&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | ru_RU.UTF-8 | ru_RU.UTF-8 |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 8185 kB | pg_default&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | default administrativ<br>
e connection database<br>
...<br>
postgres=# \c tbbase<br>
tbbase=# GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO "tbuser";<br>
tbbase=# ALTER DATABASE tbbase OWNER TO tbuser;<br>
tbbase=# \q<br>
<strong>Task:</strong><br>
Администрирование базы данных. Сделаем так, чтобы с клиентской машины Redos мы могли подключаться к серверу AltLinux удаленно<br>
<strong>Decision:</strong><br>
# su - postgres -c "psql -c 'SHOW config_file;'"<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; config_file&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;<br>
-------------------------------------<br>
&nbsp;/var/lib/pgsql/data/postgresql.conf<br>
(1 строка)<br>
# echo "listen_addresses = 'IpAddr3, IpAddr2, thost1'" &gt;&gt; /var/lib/pgsql/data/postgresql.conf<br>
# cat /var/lib/pgsql/data/pg_hba.conf<br>
...<br>
# "local" is for Unix domain socket connections only<br>
local&nbsp;&nbsp; all&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; all&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; trust<br>
# IPv4 local connections:<br>
host&nbsp;&nbsp;&nbsp; all&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; all&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 127.0.0.1/32&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; trust<br>
...<br>
# vim /var/lib/pgsql/data/pg_hba.conf<br>
# cat /var/lib/pgsql/data/pg_hba.conf | grep '10.38.'<br>
# "local" is for Unix domain socket connections only<br>
local&nbsp;&nbsp; all&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; all&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; trust<br>
# IPv4 local connections:<br>
host&nbsp;&nbsp;&nbsp; tbbase&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; tbuser&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; IpAddr2/21&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; md5<br>
host&nbsp;&nbsp;&nbsp; all&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; all&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 127.0.0.1/32&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; trust<br>
# systemctl restart postgresql<br>
# systemctl status postgresql<br>
$ psql -d tbbase -U tbuser -h thost1<br>
<strong>Task:</strong><br>
Администрирование базы данных. Для работы с базой в графическом интерфейсе установим Pgadmin<br>
<strong>Decision:</strong><br>
# apt-get install pgadmin3<br>
# pgadmin3 &amp;<br>
&nbsp;&nbsp; &nbsp;add server - name - tbuser - host - thost1- password - tbpassword - ok<br>
# dnf install postgresql-server<br>
# postgresql-setup initdb<br>
# systemctl enable postgresql<br>
# systemctl start postgresql<br>
# pg_isready<br>
$ psql -d tbbase -U tbuser -h thost1<br>
tbbase=&gt; \du<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Список ролей<br>
&nbsp;Имя роли |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Атрибуты&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Член ролей<br>
----------+-------------------------------------------------------------------------+------------<br>
&nbsp;tbuser&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | {}<br>
&nbsp;postgres | Суперпользователь, Создаёт роли, Создаёт БД, Репликация, Пропускать RLS | {}<br>
<strong>Decision:</strong><br>
$ sudo dnf install pgadmin4 pgadmin4-qt<br>
$ pgadmin4-qt &amp;<br>
&nbsp;&nbsp; &nbsp;root's password - add server - name - tbuser - host - thost1- password - tbpassword - ok<br>
<strong>Task:</strong><br>
Разработка базы данных. Создать таблицы. В первой таблице отметим в каких зданиях находятся кабинеты.<br>
<strong>Decision:</strong><br>
CREATE TABLE offices (<br>
&nbsp; id SERIAL PRIMARY KEY,<br>
&nbsp; office VARCHAR,<br>
&nbsp; building VARCHAR<br>
);<br>
INSERT INTO offices (office, building)<br>
VALUES ('1', 'Улица1'),<br>
('2', 'Улица1'),<br>
('3', 'Улица1'),<br>
('4', 'Улица2'),<br>
('5', 'Улица2'),<br>
('6', 'Улица2'),<br>
('7', 'Улица2'),<br>
('8', 'Улица2'),<br>
('9', 'Улица2');<br>
SELECT * FROM offices;<br>
+====+========+===============+<br>
| id | office | building&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+====+========+===============+<br>
| 1&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp; | Улица1&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;|<br>
+----+--------+---------------+<br>
| 2&nbsp; | 2&nbsp;&nbsp;&nbsp;&nbsp; | Улица1&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;|<br>
+----+--------+---------------+<br>
| 3&nbsp; | 3&nbsp;&nbsp;&nbsp;&nbsp; | Улица1&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;|<br>
+----+--------+---------------+<br>
| 4&nbsp; | 4&nbsp;&nbsp;&nbsp; | Улица2&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;|<br>
+----+--------+---------------+<br>
| 5&nbsp; | 5&nbsp;&nbsp;&nbsp; | Улица2&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;|<br>
+----+--------+---------------+<br>
| 6&nbsp; | 6&nbsp;&nbsp;&nbsp; | Улица2&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;|<br>
+----+--------+---------------+<br>
| 7&nbsp; | 7&nbsp;&nbsp;&nbsp; | Улица2&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;|<br>
+----+--------+---------------+<br>
| 8&nbsp; | 8&nbsp;&nbsp;&nbsp; | Улица2&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;|<br>
+----+--------+---------------+<br>
| 9&nbsp; | 9&nbsp;&nbsp;&nbsp; | Улица2&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;|<br>
+----+--------+---------------+<br>
<strong>Task:</strong><br>
Разработка базы данных. Вторая таблица отвечает за названия оборудований<br>
<strong>Decision:</strong><br>
CREATE TABLE devices (<br>
&nbsp; id SERIAL PRIMARY KEY,<br>
&nbsp; device VARCHAR,<br>
&nbsp; title VARCHAR<br>
);<br>
INSERT INTO devices (device, title)<br>
VALUES ('Atc', 'Panasonic kx-tda100ru'),<br>
('Bидеокамера белая', NULL),<br>
('Интерактиная доска с короткофокусным проектором', 'Promethean activeboard i78 mount dlp'),<br>
('Колонки', 'Sven sps-605'),<br>
('Компьютер', 'Nuc'),<br>
('Программно-аапаратный комплекс', 'Vipnet coordinator hw 1000'),<br>
('Сетевой фильтр', 'Sven platinum'),<br>
('Маршрутизатор', 'Mtuserrottuser'),<br>
('Сетевой фильтр', 'Makel с заземлением mpg 137'),<br>
('Роутер', 'Mtuserrottuser browder rb9516'),<br>
('Dvd-плеер', 'Pioner dv-310-k'),<br>
('Акустическая система', 'Electrovoice'),<br>
('Коммутатор', 'Kramer'),<br>
('Масштабатор видео и графики', 'Kramer'),<br>
('Микрофон делегата настольный', NULL),<br>
('Микрофонная стойка', 'Qutuser lok a300'),<br>
('Мультимедийный проектор', 'Epson eb-965h'),<br>
('Пульт микшерский', 'Soundcraft epm8'),<br>
('Система вентилляции и кондиционирования', NULL),<br>
('Эран моторизированный', 'Projecta compact electrol'),<br>
('Ноутбук', 'Acer aspire as5560g-4333g32mn'),<br>
('Bидеокамера серая', NULL),<br>
('Микрофон', 'Shure sh58'),<br>
('Акустическая система', 'Mackie sr1530z'),<br>
('Сетевой фильтр', 'Sven optima'),<br>
('Сетевой фильтр', 'Surge protector'),<br>
('Мультимедийный проектор', 'Optima ex612'),<br>
('Экран настенный', 'Screenmedia economy-p'),<br>
('Колонки', 'Logitech s120'),<br>
('Компьютер', 'Nuc mini pc kit'),<br>
('Сетевой фильтр', 'Pc pet'),<br>
('Интерактиная доска', '80'),<br>
('Короткофокусный проектор', 'Benq'),<br>
('Колонки', 'Microlab solo 1'),<br>
('Акустическая система', 'Eurosound eg-26w 2*6'),<br>
('Микшерный пульт', 'Eurosound compact-802'),<br>
('Планшет графический', 'Wacom pl-1600'),<br>
('Телевизор плазменный', 'Lg 50pa6500'),<br>
('Усилитель мощности', 'Eurosound xz-400'),<br>
('8 port video splitter', NULL);<br>
SELECT * FROM devices;<br>
+====+=================================================+======================================+<br>
| id | device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | title&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+====+=================================================+======================================+<br>
| 1&nbsp; | Atc&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Panasonic kx-tda100ru&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 2&nbsp; | Bидеокамера белая&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | (null)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 3&nbsp; | Интерактиная доска с короткофокусным проектором | Promethean activeboard i78 mount dlp |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 4&nbsp; | Колонки&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Sven sps-605&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 5&nbsp; | Компьютер&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Nuc&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 6&nbsp; | Программно-аапаратный комплекс&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Vipnet coordinator hw 1000&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 7&nbsp; | Сетевой фильтр&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Sven platinum&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 8&nbsp; | Маршрутизатор&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Mtuserrottuser&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 9&nbsp; | Сетевой фильтр&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Makel с заземлением mpg 137&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 10 | Роутер&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Mtuserrottuser browder rb9516&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 11 | Dvd-плеер&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Pioner dv-310-k&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 12 | Акустическая система&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Electrovoice&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 13 | Коммутатор&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Kramer&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 14 | Масштабатор видео и графики&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Kramer&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 15 | Микрофон делегата настольный&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | (null)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 16 | Микрофонная стойка&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Qutuser lok a300&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 17 | Мультимедийный проектор&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Epson eb-965h&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 18 | Пульт микшерский&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Soundcraft epm8&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 19 | Система вентилляции и кондиционирования&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | (null)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 20 | Эран моторизированный&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Projecta compact electrol&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 21 | Ноутбук&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Acer aspire as5560g-4333g32mn&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 22 | Bидеокамера серая&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | (null)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 23 | Микрофон&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Shure sh58&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 24 | Акустическая система&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Mackie sr1530z&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 25 | Сетевой фильтр&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Sven optima&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 26 | Сетевой фильтр&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Surge protector&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 27 | Мультимедийный проектор&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Optima ex612&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 28 | Экран настенный&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Screenmedia economy-p&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 29 | Колонки&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Logitech s120&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 30 | Компьютер&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Nuc mini pc kit&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 31 | Сетевой фильтр&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Pc pet&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 32 | Интерактиная доска&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 80&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 33 | Короткофокусный проектор&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Benq&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 34 | Колонки&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Microlab solo 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 35 | Акустическая система&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Eurosound eg-26w 2*6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 36 | Микшерный пульт&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Eurosound compact-802&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 37 | Планшет графический&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Wacom pl-1600&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 38 | Телевизор плазменный&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Lg 50pa6500&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 39 | Усилитель мощности&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Eurosound xz-400&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
| 40 | 8 port video splitter&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | (null)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+----+-------------------------------------------------+--------------------------------------+<br>
<strong>Task:</strong><br>
Разработка базы данных. Третья таблица отвечает за инвентарные номера оборудований, кабинетов и даты изменения<br>
<strong>Decision:</strong><br>
CREATE TABLE inventories (<br>
&nbsp; id SERIAL PRIMARY KEY,<br>
&nbsp; inventory VARCHAR,<br>
&nbsp; device_id INT REFERENCES devices(id),<br>
&nbsp; office_id INT REFERENCES offices(id),&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;<br>
&nbsp; quantity INT,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;<br>
&nbsp; date TIMESTAMP<br>
);<br>
INSERT INTO inventories (inventory, device_id, office_id, quantity, date)<br>
VALUES ('457', '1', '1', '1', '2017-12-12 12:12:12'),<br>
(NULL, '2', '1', '1', '2017-12-12 12:12:12'),<br>
...<br>
('750', '30', '6', '1', '2021-09-12 12:12:12'),<br>
('707', '17', '6', '1', '2020-05-12 12:12:12'),<br>
('008', '4', '6', '1', '2020-09-12 12:12:12'),<br>
('010', '34', '9', '1', '2017-12-12 12:12:12'),<br>
('650', '5', '9', '1', '2017-12-12 12:12:12'),<br>
('556', '33', '9', '1', '2017-12-12 12:12:12'),<br>
('426', '32', '9', '1', '2017-12-12 12:12:12');<br>
SELECT * FROM inventories;<br>
+====+=============+===========+===========+==========+=====================+<br>
| id | inventory&nbsp;&nbsp; | device_id | office_id | quantity | date&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+====+=============+===========+===========+==========+=====================+<br>
| 1&nbsp; | 457&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 2&nbsp; | (null)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
...<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 62 | 750&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 30&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2021-09-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 63 | 707&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 17&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2020-05-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 64 | 008&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 4&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2020-09-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 65 | 010&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 34&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 66 | 650&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 5&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 67 | 556&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 33&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 68 | 426&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 32&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
<strong>Task:</strong><br>
Написание Sql запросов. Мне нужно вывести информацию, где в первом столбце будет инвентарные номера, во втором столбце, устройство и его название, а в третьем столбце вывести кабинеты, где находятся те самые оборудования<br>
<strong>Decision:</strong><br>
SELECT inventory, device, title, office<br>
FROM inventories<br>
INNER JOIN devices<br>
ON inventories.device_id = devices.id<br>
INNER JOIN offices<br>
ON inventories.office_id = offices.id<br>
WHERE office_id='6';<br>
+=============+=========================+=================+========+<br>
| inventory&nbsp;&nbsp; | device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | title&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | office |<br>
+=============+=========================+=================+========+<br>
| 008&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Колонки&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Sven sps-605&nbsp;&nbsp;&nbsp; | 6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+-------------+-------------------------+-----------------+--------+<br>
| 707&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Мультимедийный проектор | Epson eb-965h&nbsp;&nbsp; | 6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+-------------+-------------------------+-----------------+--------+<br>
| 750&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Компьютер&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Nuc mini pc kit | 6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+-------------+-------------------------+-----------------+--------+<br>
<strong>Task:</strong><br>
Написание Sql запросов. Заметил ошибку в таблице, есть лишнее оборудование в кабинете. его на самом деле нету в кабинете и значит не должно быть в таблице.<br>
<strong>Decision:</strong><br>
DELETE FROM inventories<br>
WHERE id='64';<br>
SELECT inventory, device, title, office<br>
FROM inventories<br>
INNER JOIN devices<br>
ON inventories.device_id = devices.id<br>
INNER JOIN offices<br>
ON inventories.office_id = offices.id<br>
WHERE office_id='6';<br>
+===========+=========================+=================+========+<br>
| inventory | device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | title&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | office |<br>
+===========+=========================+=================+========+<br>
| 707&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Мультимедийный проектор | Epson eb-965h&nbsp;&nbsp; | 6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+-----------+-------------------------+-----------------+--------+<br>
| 750&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Компьютер&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Nuc mini pc kit | 6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+-----------+-------------------------+-----------------+--------+<br>
SELECT * FROM inventories;<br>
+====+=============+===========+===========+==========+=====================+<br>
| id | inventory&nbsp;&nbsp; | device_id | office_id | quantity | date&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+====+=============+===========+===========+==========+=====================+<br>
| 1&nbsp; | 457&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 2&nbsp; | (null)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
...<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 62 | 750&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 30&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2021-09-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 63 | 707&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 17&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2020-05-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 65 | 010&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 34&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 66 | 650&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 5&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 67 | 556&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 33&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 68 | 426&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 32&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
<strong>Task:</strong><br>
Написание Sql запросов. Появилось новое обрудование, и нужно его внести в таблицу.<br>
<strong>Decision:</strong><br>
INSERT INTO inventories (inventory, device_id, office_id, quantity, date)<br>
VALUES ('testinv1', '39', '1', '1', '2017-12-12 12:12:12');<br>
SELECT * FROM inventories;<br>
+====+=============+===========+===========+==========+=====================+<br>
| id | inventory&nbsp;&nbsp; | device_id | office_id | quantity | date&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+====+=============+===========+===========+==========+=====================+<br>
| 1&nbsp; | 457&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 2&nbsp; | (null)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
...<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 68 | 426&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 32&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 69 | testinv1&nbsp;&nbsp;&nbsp; | 39&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
<strong>Task:</strong><br>
Написание Sql запросов. в предыдущей задаче не верные данные внес в таблицу, нужно подкорректировать.<br>
<strong>Decision:</strong><br>
UPDATE inventories<br>
SET inventory='testinv2', office_id='9'<br>
WHERE id='69';<br>
SELECT * FROM inventories;<br>
+====+=============+===========+===========+==========+=====================+<br>
| id | inventory&nbsp;&nbsp; | device_id | office_id | quantity | date&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+====+=============+===========+===========+==========+=====================+<br>
| 1&nbsp; | 457&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 2&nbsp; | (null)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
...<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 68 | 426&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 32&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
| 69 | testinv2&nbsp;&nbsp;&nbsp; | 39&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 2017-12-12 12:12:12 |<br>
+----+-------------+-----------+-----------+----------+---------------------+<br>
SELECT inventory, device, title, office<br>
FROM inventories<br>
INNER JOIN devices<br>
ON inventories.device_id = devices.id<br>
INNER JOIN offices<br>
ON inventories.office_id = offices.id<br>
WHERE office_id='9';<br>
+=============+==========================+==================+========+<br>
| inventory&nbsp;&nbsp; | device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | title&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | office |<br>
+=============+==========================+==================+========+<br>
| 650&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Компьютер&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Nuc&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+-------------+--------------------------+------------------+--------+<br>
| 426&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Интерактиная доска&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 80&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+-------------+--------------------------+------------------+--------+<br>
| 556&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Короткофокусный проектор | Benq&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+-------------+--------------------------+------------------+--------+<br>
| 010&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Колонки&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Microlab solo 1&nbsp; | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+-------------+--------------------------+------------------+--------+<br>
| testinv2&nbsp;&nbsp;&nbsp; | Усилитель мощности&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Eurosound xz-400 | 9&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |<br>
+-------------+--------------------------+------------------+--------+<br>
<strong>Source:</strong>
# <a href="https://www.altlinux.org/ActiveDirectory/Login#%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0_%D0%BF%D0%B0%D0%BA%D0%B5%D1%82%D0%BE%D0%B2">https://www.altlinux.org/ActiveDirectory/Login#%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0_%D0%BF%D0%B0%D0%BA%D0%B5%D1%82%D0%BE%D0%B2</a>
# <a href="https://www.altlinux.org/SSSD/AD">https://www.altlinux.org/SSSD/AD</a>
# <a href="https://www.altlinux.org/%D0%A1%D0%B5%D1%82%D0%B5%D0%B2%D0%BE%D0%B9_%D0%BC%D0%BE%D1%81%D1%82">https://www.altlinux.org/%D0%A1%D0%B5%D1%82%D0%B5%D0%B2%D0%BE%D0%B9_%D0%BC%D0%BE%D1%81%D1%82</a>
# <a href="https://www.altlinux.org/PostgreSQL#%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0_%D0%B8_%D0%BD%D0%B0%D1%87%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9_%D0%B7%D0%B0%D0%BF%D1%83%D1%81%D0%BA">https://www.altlinux.org/PostgreSQL#%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0_%D0%B8_%D0%BD%D0%B0%D1%87%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9_%D0%B7%D0%B0%D0%BF%D1%83%D1%81%D0%BA</a>
# <a href="https://www.tecmint.com/install-postgresql-and-pgadmin-in-ubuntu/">https://www.tecmint.com/install-postgresql-and-pgadmin-in-ubuntu/</a>
# <a href="https://o7planning.org/11353/install-pgadmin-on-ubuntu">https://o7planning.org/11353/install-pgadmin-on-ubuntu</a>
# <a href="https://redos.red-soft.ru/base/server-configuring/dbms/install-postgresql/?sphrase_id=53348">https://redos.red-soft.ru/base/server-configuring/dbms/install-postgresql/?sphrase_id=53348</a>
# <a href="https://redos.red-soft.ru/base/server-configuring/dbms/pgadmin4/">https://redos.red-soft.ru/base/server-configuring/dbms/pgadmin4/</a>
</p>