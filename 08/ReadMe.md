Урок 8. Скрипты Bash

Задание:
**1. Вывести на экран 3 раза имя пользователя, от которого запускается команда.**

	vboxuser@LINUX-VIRTUAL:~$ for x in {1..3}; do who | awk '{print $1}'; done

	vboxuser

	vboxuser

	vboxuser

	vboxuser@LINUX-VIRTUAL:~$ 

**2. Вывести с помощью цикла while все четные числа от 0 до 100 включительно.**

	Подготовил скрипт и сделал его исполняемым. Содержимое скрипта: 

		#!/bin/bash

		a=0

		while [ $a -ne 100 ]
		do
        		a=$(($a+2))
        		echo $a
		done


**3. Командой 'cut' вывести для текущей папки права доступа файлов (первая 
колонка вывода команды ‘ll’). Отсортировать этот вывод (команда ‘sort’). 
Удалить дубликаты (команда ‘uniq’). Использовать для решения конвейер 
обработки задач (pipeline - вертикальный слэш).**

*3.1 Выводим права доступа для папки*
	
vboxuser@LINUX-VIRTUAL:~$ ls -l /etc | cut -b 1-10

total 796
drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

-rw-r-----

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-rw-r-----

-rw-r-----

drwxr-xr-x

-rw-r--r--

-rw-r--r--

-rw-r--r--

-rw-r--r--

-rw-r--r--

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

-rw-r--r--

drwxr-xr-x

drwxrwxr-x

-rw-r--r--

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-rw-r--r--

-rw-r--r--

lrwxrwxrwx

drwxr-xr-x

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-r--r--r--

-rw-r--r--

-rw-r--r--

-rw-r--r--

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

lrwxrwxrwx

drwx------

-rw-r--r--

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

lrwxrwxrwx

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-rw-r--r--

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

lrwxrwxrwx

lrwxrwxrwx

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

-rw-r-----

-rw-r-----

-rw-r--r--

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

-rw-r--r--

-rw-r--r--

-rw-r--r--

-r--r-----

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

-rw-r--r--

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

drwxr-xr-x

lrwxrwxrwx

-rw-r--r--

-rw-r--r--

drwxr-xr-x

-rw-r--r--


*3.2 Отсортируем этот вывод (команда ‘sort’). Удалим дубликаты (команда ‘uniq’)*

vboxuser@LINUX-VIRTUAL:~$ ls -l /etc | cut -b 1-10 | sort | uniq 

-r--r-----

-r--r--r--

-rw-r-----

-rw-r--r--

drwx------

drwxr-xr-x

drwxrwxr-x

lrwxrwxrwx

total 796


**4.* Написать скрипт очистки директорий. На вход принимает путь к директории. 
Если директория существует, то удаляет в ней все файлы с расширениями .bak, 
.tmp, .backup. Если директории нет, то выводит ошибку.**

	mkdir testScript //создал директорию

	touch test.txt test2.bak test3.tmp test4.backup //создал файлы

	cat > testSc //создал файл с содержимым:

		#!/bin/bash
		if [ -d $1 ]
		then
		rm -r *.bak *.tmp *.backup
		echo "files with bak, tmp, backup extensions have been deleted"else
		echo "there is no such directory"
		fi
		directory=$1

	chmod +x testSc //добавил возможность исполнения

	bash testSc /home/may2/testScript/ //запустил скрипт, удалил файлы с расширениями .bak, .tmp, .backup
  
