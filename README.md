Если тилиты repo еще нет в вашей системе, то необходимо ее установить и пропистаь в PATH.
http://source.android.com/source/downloading.html#installing-repo

Если вкратце, то 
    $ mkdir ~/bin
    $ PATH=~/bin:$PATH
    $ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    $ chmod a+x ~/bin/repo

Кратко алгоритм сборки:

    $ repo init -u https://github.com/macros64/yocto-starterkit.git
    $ repo sync

    $ source setup-environment <имя сборочной папки>


Редактируем <рабочая папка>/conf/local.conf
и в первую строчку вписываем нашу плату: MACHINE ??= 'sk-imx6q'

В папке сборки запускаем сборку системы: 
bitbake sk-image-core

Это минимальный консольный рабочий образ системы.
После окончания сборки (несколько часов) результат можно будет найти в <рабочая папка>/tmp/deploy/images/

Пока не до конца разобрался как делать образ .sdcard, он почему-то нулевой получается. Можно тестировать файловую систему с ядром, но только после того ,как в /boot положить dtb файл для платы с правильным именем.
