Урок 4. Подключение сторонних репозиториев, ручная установка пакетов

Задание:
1. Подключить дополнительный репозиторий на выбор: Docker, Nginx, Oracle MySQL. Установить любой пакет из этого репозитория.

	vboxuser@LINUX-VIRTUAL:~$ sudo su
	root@LINUX-VIRTUAL:/home/vboxuser# apt update
	root@LINUX-VIRTUAL:/home/vboxuser# apt install -y nginx


2. Установить и удалить deb-пакет с помощью dpkg.

	wget https://download.virtualbox.org/virtualbox/7.0.4/virtualbox-7.0_7.0.4-154605~Ubuntu~jammy_amd64.deb
	ll
	dpkg -i virtualbox-7.0_7.0.4-154605~Ubuntu~jammy_amd64.deb
	apt -f install
	dpkg -l | grep jammy
	dpkg -r virtualbox-7.0

3. Установить и удалить snap-пакет. 

	snap find chromium
	snap install chromium
	snap list
	snap remove chromium

4. Добавить задачу для выполнения каждые 3 минуты (создание директории, запись в файл).

	apt install cron
	systemctl enable cron
	crontab -e
4.1 Создает и удаляет один файл в домашней директории
	*/3 * * * * touch testfilecron
	*/3 * * * * rm testfilecron

5. * Подключить PPA-репозиторий на выбор. Установить из него пакет. Удалить PPA из системы.

	sudo add-apt-repository ppa:thomas-schiex/blender
	sudo apt-get install blender
	sudo add-apt-repository --remove ppa:thomas-schiex/blender
