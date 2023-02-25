Урок 7. Запуск веб-приложения из контейнеров

**Задание:**

**1. Переустановить операционную систему (по желанию, для дополнительной практики)**

	vboxuser@LINUX-VIRTUAL:~$ task1 % vagrant destroy && vagrant up

**2. Подключить репозиторий Docker.**

	vboxuser@LINUX-VIRTUAL:~$ docker -v
	Docker version 20.10.17, build 100c701

**3. Запустить контейнер с Ubuntu.**

	vboxuser@LINUX-VIRTUAL:~$ sudo docker pull ubuntu

	Using default tag: latest

	latest: Pulling from library/ubuntu

	405f018f9d1d: Pull complete

	Digest: sha256:b6b83d3c331794420340093eb706a6f152d9c1fa51b262d9bf34594887c2c7ac

	Status: Downloaded newer image for ubuntu:latest

	docker.io/library/ubuntu:latest

	vboxuser@LINUX-VIRTUAL:~$ sudo docker run -it ubuntu

	cat /etc/lsb-release

		DISTRIB_ID=Ubuntu

		DISTRIB_RELEASE=22.04

		DISTRIB_CODENAME=jammy

		DISTRIB_DESCRIPTION="Ubuntu 22.04 LTS"

**4. Используя Dockerfile, собрать связку nginx + PHP-FPM в одном контейнере. **

*4.1 Создаем Dockerfile со следующими инструкциями:*

	FROM alpine

	RUN apk update && apk upgrade

	RUN apk add nginx	

	RUN apk add php8 php8-fpm php8-opcache

	CMD php -v

*4.2 Собираем новый образ*

	vboxuser@LINUX-VIRTUAL:~$ sudo docker build -t alpine_php .

	Sending build context to Docker daemon   16.9kB

	Step 1/5 : FROM alpine

	 ---> e66264b98777

	Step 2/5 : RUN apk update && apk upgrade

	 ---> Using cache

	 ---> c03ba34da2f7

	Step 3/5 : RUN apk add nginx

	 ---> Using cache

	 ---> e5c2176da182

	Step 4/5 : RUN apk add php8 php8-fpm php8-opcache

	 ---> Running in 3397c1aeecc5

	(1/11) Installing php8-common (8.0.20-r0)

	(2/11) Installing argon2-libs (20190702-r1)

	(3/11) Installing ncurses-terminfo-base (6.3_p20220521-r0)

	(4/11) Installing ncurses-libs (6.3_p20220521-r0)

	(5/11) Installing libedit (20210910.3.1-r0)

	(6/11) Installing pcre2 (10.40-r0)

	(7/11) Installing xz-libs (5.2.5-r1)

	(8/11) Installing libxml2 (2.9.14-r0)

	(9/11) Installing php8 (8.0.20-r0)

	(10/11) Installing php8-fpm (8.0.20-r0)

	(11/11) Installing php8-opcache (8.0.20-r0)

	Executing busybox-1.35.0-r14.trigger

	OK: 28 MiB in 27 packages

	Removing intermediate container 3397c1aeecc5

	 ---> f9d7230686d1

	Step 5/5 : CMD php -v

	 ---> Running in 50403bc75250

	Removing intermediate container 50403bc75250

	 ---> b5c5c7f18b40

	Successfully built b5c5c7f18b40

	Successfully tagged alpine_php:latest

*4.3 Проверяем результат*

	vboxuser@LINUX-VIRTUAL:~$ sudo docker run -it alpine_php

	PHP 8.0.20 (cli) (built: Jun 10 2022 09:06:30) ( NTS )

	Copyright (c) The PHP Group

	Zend Engine v4.0.20, Copyright (c) Zend Technologies

	    with Zend OPcache v8.0.20, Copyright (c), by Zend Technologies
      
