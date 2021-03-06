
Как перенести WordPress сайт с хостинга в Яндекс.Облако?
========================================================

Олег Иванов

14 марта 2019 г.

*   Туториалы[](/blog?tags=tutorial)

На платформе Яндекс.Облако тысячи пользователей решают свои задачи. Мы рады, что многие охотно делятся своим опытом. Нам присылают дополнения и уточнения для документации, идеи и даже самостоятельные руководства.

Мы, со своей стороны, обещаем оценивать и поощрять такой контент, размещать и продвигать его в наших каналах. Авторы опубликованных кейсов, уточнений к документации и сценариев использования платформы получат от нас приятные подарки и приглашения на мероприятия. Скоро мы расскажем подробности, а пока — публикуем руководство по переносу сайта на систему WordPress в Яндекс.Облаке, присланное пользователем Олегом Ивановым. Спасибо за такой детальный материал! Автору мы вручим набор редких сувениров Яндекс.Облака и подписку на Яндекс.Плюс. Если вы хотите поделиться своим контентом по использованию Облака, пишите нам на [\[email protected\]](/cdn-cgi/l/email-protection#53303f3c26377e313f3c34132a323d37362b7e2736323e7d2126).

Спектр применения облачных ресурсов достаточно широк: в нем можно хранить данные, выполнять облачные вычисления, а также делать вполне обыденные задачи, к примеру разместить веб-сайт.

Я буду описывать весь процесс миграции сайта на базе WordPress в Яндекс.Облако пошагово, от начала и до самого конца, включая все трудности, которые будут возникать, с учётом того, что вы можете быть различного уровня знаний и подготовки. Обращаю внимание, что я все нижеописанные действия выполняю на Mac OS X. Я постараюсь приводить альтернативы ПО для Windows, когда это потребуется.

[](#podgotovka-k-perenosu-polnyj-bekap)Подготовка к переносу. Полный бекап
--------------------------------------------------------------------------

Итак, к делу. У нас есть WordPress сайт с базой данных размещенных на хостинге у провайдера Reg.ru, а также домен, который находится у другого регистратора Webnames.ru.

Для начала необходимо подготовить сайт к переносу, а именно сделать полный бекап файлов сайта, а также базы данных (БД). Выполнить это можно несколькими способами, выбор за вами:

*   С помощью различных плагинов для WordPress (BackWPup или Updraft Plus и т. п.).
*   С помощью встроенных средств в панели управления хостингом Reg.ru.
*   Скопировать все файлы на свой жесткий диск через FTP-клиент, а БД экспортировать через панель phpmyadmin. Данный вариант занимает чуть больше по времени, поскольку сайт имеет множество мелких файлов и копирование займёт от 5 до 20 минут, в зависимости от количества файлов вашего сайта.

Я решил воспользоваться встроенным средством создания бекапов из панели управления хостингом REG.ru. Заходим в личный кабинет, переходим в «Мои хостинг и услуги», напротив своего хостинга нажимаем «Войти», далее попадаете в панель управления хостингом. У меня установлена панель Plesk, у вас может быть другая. Панель разделена на 3 колонки, в самой правой находим раздел «Дополнительные услуги» — > «Резервные копии», нажимаем и переходим в автоматическую систему подготовки бекапов. Можно сформировать бекап сайта за последние 30 дней, что очень удобно. Нажимаем сформировать архив напротив пунктов «Файлы сайта» и «База данных». Они формируются последовательно друг за другом в течении пары минут. Далее нажимаете скачать и сохраняете у себя на жестком диске.

![Резервные копии reg.ru](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_files.png "Резервные копии reg.ru")  
_Скриншот: Подготовка файлов бекапа в панели управления хостингом Reg.ru_

[](#sozdanie-akkaunta-v-yandeksoblake)Создание аккаунта в Яндекс.Облаке
-----------------------------------------------------------------------

Переходим [на сайт Яндекс.Облака](https://cloud.yandex.ru). Нажимаем «Подключиться». Здесь нужно будет воспользоваться существующим аккаунтом Яндекса или создать новый.

![Главная страница Яндекс.Облако](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_mainpage.png "Главная страница Яндекс.Облако")

Допустим мы создаем аккаунт с нуля и нажимаем «Зарегистрироваться»:

![Вход Яндекс.Облако](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_signin.png "Вход Яндекс.Облако")

Заполняем необходимые учетные данные и подключаем свой номер телефона. СМС с кодом подтверждения придёт к вам на телефон в течении минуты, подтвердите его и нажмите зарегистрироваться.

![Регистрация Яндекс.Облако](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_registration.png "Регистрация Яндекс.Облако")  
_Скриншот: Регистрация аккаунта в Яндекс.Облаке._

После приветствия нажимаем «Войти» и попадаем в консоль управления Яндекс.Облака.

![Вход в Яндекс.Облако](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_welcome.png "Вход в Яндекс.Облако")  
_Скриншот: вход в Яндекс.Облако_

![Консоль Яндекс.Облако](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_console1.png "Консоль")  
_Скриншот: Консоль управления Яндекс.Облака._

[](#sozdanie-virtualьnoj-mashiny-v-yandeksoblake)Создание виртуальной машины в Яндекс.Облаке
--------------------------------------------------------------------------------------------

Для того, чтобы создать WordPress сайт необходимо прежде создать виртуальную машину (ВМ), для этого переходим в консоль управления Яндекс.Облака. В правом верхнем углу нажимаем «Создать ресурс» -> «Виртуальная машина».

![Создание виртуальной машины в Яндекс.Облаке](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_createvm.png "Создание виртуальной машины в Яндекс.Облаке")  
_Скриншот: Создание ВМ в Яндекс.Облаке_

Для создания виртуальной машины Яндекс.Облако потребует от вас привязать карточку к вашему аккаунту, поскольку вы начинаете пользоваться вычислительными мощностями облака. Тут как не крути необходимо это сделать, иначе дальше мы не продвинемся, нажимаем «Создать» привязку.

![Создание платёжного аккаунта Яндекс.Облако](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_nopaid.png "Создание платёжного аккаунта Яндекс.Облако")  
_Скриншот: Создание платежного аккаунта_

Забегая вперед, скажу, что в течении пробного периода вы будете пользоваться подаренным грантом в 4000 рублей. После трат вы будете платить услуги с привязанной карты.

Если вы отвяжите карту раньше окончания пробного периода, то ваши сервисы будут остановлены, и когда вы захотите снова воспользоваться грантом, то вам необходимо будет перейти на платную версию и пополнить счёт на небольшую сумму, тогда подаренный грант вновь будет активирован, но уже будет применяться в качестве скидки по вашим услугам.

После сообщения об успешной привязке нажимаем «Активировать».

![Создание платёжного аккаунта Яндекс.Облако](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_paid.png "Создание платёжного аккаунта Яндекс.Облако")  
_Скриншот: успешная привязка карты_

Переходим к выбору параметров виртуальной машины (ВМ). Выберите каталог и в правом верхнем углу «Создать ресурс» «Виртуальная машина».

![Создать виртуальную машину Яндекс.Облако](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_createvm.png "Создать виртуальную машину Яндекс.Облако")

Задаем параметры нашей ВМ. Вводите название ВМ, а также ее описание, если это необходимо. Переходим к зоне доступности, по сути это является выбором одного из трёх дата-центров облачной платформы, дата-центры изолированы друг от друга и позже нельзя будет перенести свою ВМ в другую зону. Поскольку пояснений по территориальному признаку тут нет, то выбираем любую из них.

Далее переходим к выбору одному из готовых образов из списка каталога. Для нашего веб-сайта необходимо выбрать LAMP-образ, который включает в себя всё необходимое: ОС Linux, веб-сервер Apache, СУБД MySQL и интерпретатор PHP.

![Образ LAMP Яндекс.Облако](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_images.png "Образ LAMP Яндекс.Облако")

Переходим к следующим параметрам ВМ:

**Диски**. Выбираем тип диска HDD (Обычный) или NVme (SSD-скоростной), а также размер диска с небольшим запасом на будущее. Если у вас обычный сайт без высоких требований к производительности и скорости, то я рекомендую выбрать HDD.

**Вычислительные ресурсы**. Выбираем тип виртуальной машины. Для обычного WordPress сайта вполне хватит «Легкой ВМ» с одним процессором и 1ГБ оперативной памяти. Обращаю внимание, что в этом разделе есть такой параметр как «Прерываемая», это дает большую скидку на вычислительные мощности, но при этом ваш сайт будет иногда недоступен. Пока неясно насколько часто это будет происходить, думаю стоит потестировать эту возможность. Если 1-2 раза в месяц и на очень короткое время, то это может оказаться хорошим вариантом сэкономить. Объясню почему: многие российские провайдеры и так отключают вычислительные мощности для технического обслуживания или решения технических сбоев, у некоторых это происходит довольно частенько, только скидки от этого вы не получаете.

**Сетевые настройки**. Нажимаем «Добавить сеть» и оставляем всё по умолчанию. Яндекс выделит нам IP-адрес, в будущем вы сможете его закрепить за собой на постоянной основе, если это потребуется. Но за это придётся немного доплатить. Нажимаем «Выбрать».

**Доступ**. На этом шаге требуется задать логин для входа на ВМ, а также SSH ключ. Как его сделать?

Нам необходимо сгенерировать пары ключей SSH для подключения к самой виртуальной машине. Для этого воспользуемся [справкой Яндекс.Облака](/docs/compute/operations/vm-connect/ssh), где расписаны действия для каждой ОС.

В моем случае я использую Mac OS X, открываем Терминал и вводим команду:

    $ ssh-keygen -t rsa -b 2048
    

После вам будет предложено ввести имя файла для ключа, здесь **очень рекомендую ничего не вводить** и просто нажать Enter, иначе после могут возникнуть проблемы с подключением.

На следующем шаге необходимо ввести кодовую фразу для файла ключей (Обязательно запомните её она пригодится. В дальнейшем рекомендую любые пароли, которые вы будете вводить сохранять в отдельном текстовом файле).

Готово, файлы сгенерированы и будут храниться в Mac OS X в папке: `/Users/<имя_пользователя>/.ssh/`.

В Windows 10: `C:\Users\<имя_пользователя>\.ssh\`.

Пример успешного создания ключа:

    MacBook-Pro-Oleg:~ oleg$ ssh-keygen -t rsa -b 2048 
    Generating public/private rsa key pair. 
    Enter file in which to save the key (/Users/oleg/.ssh/id_rsa): 
    Enter passphrase (empty for no passphrase): 
    Enter same passphrase again: 
    Your identification has been saved in /Users/oleg/.ssh/id_rsa. 
    Your public key has been saved in /Users/oleg/.ssh/id_rsa.pub. 
    The key fingerprint it SHAESG:WW0d1wKSkPubgE43dsgyh00sPcOOF7dr0896c9appo [email protected]
    The key's randomart image is: 
    +---[RSA 2048)----+
    ...
    MacBook-Pro-Oleg:~ oleg$ 
    

Папка `.ssh` будет по умолчанию скрыта, поэтому перейдите в папку `/Users/Username/.ssh/` предварительно открыв Finder, используем сочетание горячих клавиш CMD+Shift+G, где `Username` заменяем на свое имя пользователя в системе Mac OS X. Открываем файл `id_rsa.pub` в блокноте или любом текстовом редакторе и копируем все содержимое за исключением имени вашего компьютера в самом конце.

Пример сгенерированного ключа:

    ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD3A17BITfm+AbSKTpH3mFXVH0kGeYHHKUnDvhZ4AOL4iNJ3CdLmLJeZQy14hKKzmHt8mkMFwWQ6fiU5elXOgzCWEKptjbwxOUULPwB0izbqgfIbuGnjEHzfA+vApngqwXj2bFpO9F+0rfMF1DNb7tXFM8vYqoT8EJYTEk1W7x53UuwCIwCrnHp9i1nyOCFQpxNjkmh9e+sAYpzDHxvTuOcpg8Zx2/89yij76nR/XUhj7QZ96ZS1UATvBEWp0FtXqsmO7RP9CUHJ+lxz00yTQmQGZ3I7l5Q8jRqmxU8/fsJXiuaMi6c8oBCXAF+LFf4sbF/Hs+RCv7CRUX6WU29m4b1
    

Справа мы будем видеть предварительный расчет по ВМ по мере того, как вы будете выбирать параметры.

![Предварительный расчет Яндекс.Облако](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_console3.png "Предварительный расчет Яндекс.Облако")

На этом этапе создание ВМ завершено, но в процессе переноса файлов сайта на ВМ машину нам еще придется сделать некоторые манипуляции по ее окончательной настройке.

[](#podklyuchenie-k-virtualьnoj-mashine-v-yandeksoblake)Подключение к виртуальной машине в Яндекс.Облаке
--------------------------------------------------------------------------------------------------------

Выбираете созданную ВМ и переходите к пункту «Сеть». Найдите поле «Публичный IPv4» — это общедоступный IP-адрес вашего сайта. Копируем в буфер.

![Публичный IP-адрес Яндекс.Облако](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_console4.png "Публичный IP-адрес Яндекс.Облако")  
_Скриншот: Публичный IPv4 адрес_

Переходим в Терминал и вводим следующую команду:

    ssh <имя_пользователя>@<публичный_IP-адрес_виртуальной машины>
    

В моем случае это:

    $ ssh [email protected]
    

Поскольку мы подключаемся к ВМ первый раз то увидим предупреждение, необходимо будет набрать «yes» и нажать «Enter». Если вы все сделали правильно на этапе генерации ключа, то увидите нечто похожее.

Пример успешного подключения к ВМ:

    MacBook-Pro-Oleg: oleg$ ssh [email protected] 
    The authenticity of host '84.201.133.90 (84.201.133.90)' can't be established. 
    ECDSA key fingerprint is SHA256: JZVioubc6mgvS3Vr6DESJnnXWAEJUSQrqxROJtDWF/W. 
    Are you sure you want to continue connecting (yes/no)? y 
    Please type 'yes' or 'no': yes 
    Warning: Permanently added '84.201.133.90' (ECDSA) to the list of known hosts. 
    Identity added: /Users/oleg/.ssh/id_rsa ((null)) 
    Welcome to Ubuntu 16.04.5 LTS (GNU/Linux 4.4.0-131-generic x86_64)
    
    * Documentation: https://help.ubuntu.com
    * Management: https://landscape.canonical.com
    * Support: https://ubuntu.com/advantage
    
    
    #################################################################
    This instance runs Yandex.cloud Marketplace product 
    You can view generated credentials in /root/default_passwords.txt
    
    Only 80, 443 and 22 tcp ports are open by default 
    To view all network permissions exec "sudo iptables-save" and "sudo iptables-save"
    
    Documentation for Yandex Cloud Marketplace images available at https://cloud.yandex.ru/docs
    
    #################################################################
    
    
    The programs included with the Ubuntu system are free software; 
    the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/ copyright.
    
    Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.
    

Прежде чем перейти к переносу файлов, необходимо сделать следующее:

*   Установить и настроить phpMyAdmin для работы с базой данный нашего сайта, к сожалению по умолчанию он не установлен в LAMP-образе.
*   Установим текстовый редактор Nano, он потребуется нам для внесения правок в некоторые файлы конфигурации.

### [](#ustanovka-redaktora-nano)Установка редактора nano

Данное действие необходимо выполнить перед установкой phpMyAdmin, поскольку мы будем изменять несколько файлов конфигурации сервера.

В Терминале выполняем:

    $ sudo apt install nano
    

Дождитесь завершения операции. Переходим к установке phpMyAdmin.

### [](#ustanavlivaem-i-nastraivaem-phpmyadmin)Устанавливаем и настраиваем phpMyAdmin

Открываем Терминал и вводим следующие команды:

    $ sudo apt-get update
    $ sudo apt-get install phpmyadmin php-mbstring php-gettext
    

В процессе установки появятся несколько диалогов, на которые необходимо будет дать ответы.

Первый диалог — выбор сервера, на который мы устанавливаем phpMyAdmin. Будьте очень внимательны на данном шаге, необходимо подсветить Apache2 и нажать ПРОБЕЛ, чтобы выбрать его. Напротив Apache2 появится звёздочка. Нажимаем «Enter».

![Конфигурация phpMyAdmin - Выбор http-сервера](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_myadmin1.png "Конфигурация phpMyAdmin - Выбор http-сервера")  
_Скриншот: Выбор http-сервера для установки phpMyAdmin_

Второй диалог предлагает нам настроить доступ к БД, выбираем «Yes» и задаем пароль администратора.

![Конфигурация phpMyAdmin - dbconfig-common](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_myadmin2.png "Конфигурация phpMyAdmin - dbconfig-common")  
_Скриншот: Настройка доступа dbconfig-common для phpMyAdmin_

В моём случае данный пароль не подошёл при входе в phpMyAdmin, поскольку при установке LAMP образа на виртуальную машину он уже был сгенерирован системой, но все-таки лучше задать его при установке phpMyAdmin на всякий случай.

Чтобы получить пароль сгенерированный при установке LAMP-образа введите команду в Терминале:

    $ sudo cat /root/default_passwords.txt
    

И получаем примерно следующий результат (копируем в текстовый файлик, чтобы не забыть):

    [email protected]:~$ sudo cat /root/default_passwords.txt 
    MYSQL_PASS=DOEC21WECnhF1 
    MYSQL_ROOT_PASS=KjZKrQV7efFGk 
    MYSQL_USER=wordpress 
    MYSQL_DB=wordpress
    
    Apache Web Auth:
      login: admin 
      password: ***************
    

Далее в терминале вводим следующие команды для включения расширения PHP:

    $ sudo phpenmod mcrypt
    $ sudo phpenmod mbstring
    

Чтобы применить все сделанные изменения необходимо перезапустить Apache.

    $ sudo systemctl restart apache2
    

Теперь вы можете открыть phpMyAdmin зайдя в браузере на публичный адрес вашего сайта и добавив к нему /phpmyadmin:

http://0.0.0.0/phpmyadmin

По умолчанию используем пользователя root с паролем, который записали в текстовый файл.  
![Вход phpMyAdmin](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_myadmin3.png "Вход phpMyAdmin")  
_Скриншот: Вход в phpMyAdmin_

### [](#delaem-phpmyadmin-bolee-bezopasnym)Делаем phpMyAdmin более безопасным

phpMyAdmin подвергается большому количеству сетевых атак, поэтому для их предотвращения необходимо предпринять действия, а именно зададим дополнительный пароль для входа в панель.

Включим возможность использования файла `.htaccess` в нашей конфигурации. Для этого необходимо отредактировать файл `phpmyadmin.conf`.

В терминале вводим:

    $ sudo nano /etc/apache2/conf-available/phpmyadmin.conf
    

и добавляем директиву: `AllowOverride All` в указанном месте:

    <Directory /usr/share/phpmyadmin>
        Options FollowSymLinks
        DirectoryIndex index.php
        AllowOverride All
    

Нажимаем Ctrl+O и Enter для сохранения и Ctrl+X для выхода из файла.

Далее перезапускаем Apache для применения изменений используя команду:

    $ sudo systemctl restart apache2
    

После того, как мы разрешили использовать файл `.htaccess` для нашего сервиса, перейдем к непосредственному созданию самого файла:

Выполняем в Терминале:

    $ sudo nano /usr/share/phpmyadmin/.htaccess
    

и добавляем следующий код:

    AuthType Basic
    AuthName "Restricted Files"
    AuthUserFile /etc/phpmyadmin/.htpasswd
    Require valid-user
    

Нажимаем Ctrl+O и Enter, далее Ctrl+X для выхода.

И раз уж мы указали файл `.htpasswd`, то необходимо его также создать:

    $ sudo htpasswd -c /etc/phpmyadmin/.htpasswd username
    

Вместо username придумываем пользователя и вводим сложный пароль два раза, записывайте всё в блокнот.

Далее перезапускаем Apache для применения изменений:

    $ sudo systemctl restart apache2
    

Краткая справка:

*   `.htpasswd` — файл, содержащий пароли для доступа к ресурсу у веб-сервера Apache.
*   `.htaccess` — файл, который дает возможность конфигурировать работу сервера в отдельных директориях (папках), не предоставляя доступа к главному конфигурационному файлу.

Наконец переходим по адресу:

http://0.0.0.0/phpmyadmin

(вписываете свой публичный IP-адрес сайта). Теперь при входе в утилиту phpMyAdmin вы дополнительно защищены от злоумышленников.

![Авторизация phpMyAdmin - Логин пароль](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_myadmin4.png "Авторизация phpMyAdmin - Логин пароль")  
_Скриншот: Окно ввода пароля для утилиты phpMyAdmin_

[](#importiruem-bazu-dannyh-cherez-phpmyadmin-v-yandeksoblako)Импортируем базу данных через phpMyAdmin в Яндекс.Облако
----------------------------------------------------------------------------------------------------------------------

Для начала необходимо открыть файл конфигурации WordPress вашего веб-сайта. Разархивируйте архив сайта в отдельную папку и найдите wp-config.php. Он должен находится в корневой папке. Здесь нам нужны значения трёх параметров:

    define('DB_USER', 'UsernameTEST');
    define('DB_NAME', 'database_wordpress');
    define('DB_PASSWORD', 'MySecretPassword');
    

Копируем имя пользователя UsernameTEST (не закрывайте файл wp-config.php).

Переходим в браузер и заходим (не забываем менять на свой IP):

http://0.0.0.0/phpmyadmin

Переходим в пункт «Учетные записи пользователей» и добавляем учетную запись пользователя с параметрами:

**Имя пользователя**: Вставляем скопированное значение из `wp-config.php`.

**Имя хоста**: Оставляем %.

**Пароль** (2 раза): Опять переходим в `wp-config.php` и копируем значение после `DB_Password`, вставляем в phpMyAdmin в поле «Пароль».

**Глобальные привилегии**: Делаем отметку «Отметить все» и переходим в самый низ, нажимаем «Вперед» сохраняя нашего пользователя.

Все остальные параметры при создании пользователя оставляем по умолчанию.

Переходим в пункт: «Базы данных». Из файла `wp-config.php` копируем значение после `DB_Name` и вставляем в поле «Имя базы данных» в phpMyAdmin, кодировку выбираем `utf8_general_ci`, нажимаем «Создать».

База данных создалась, теперь нужно импортировать БД из бекапа в вновь созданную базу. Выбираем в левой колонке созданную базу данных, вверху нажимаем «Импорт» и выбираем наш бекап базы данных.

Готово, база данных импортирована.

![Импорт phpMyAdmin](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_success_import.png "Импорт phpMyAdmin")  
_Скриншот: Успешный импорт БД в Яндекс.Облаке_

Довольно часто случается, что бекап БД превышает установленный лимит по умолчанию в 2МБ и мы получаем ошибку, импорт не удается совершить. Эту проблему можно решить отредактировав файл конфигурации `php.ini`, где задано данное ограничение.

Открываем Терминал и вводим команду:

    $ sudo nano /etc/php/7.0/apache2/php.ini
    

Откроется файл, в котором нам нужно отредактировать два параметра:

*   `upload_max_filesize` — максимальный размер загружаемого файла.
*   `post_max_size` — максимальный размер сообщения методом POST.

Поскольку файл достаточно большой и в нем содержится много параметров, то предлагаю воспользоваться переходом к строке содержащие данные параметры, в моем случае: горячая клавиша Ctrl и «-» (знак тире или минус) и вводим номер строки: 809 и «Enter».

Устанавливаем `upload_max_filesize = 80M`.

Переходим через сочетание клавиш Ctrl и «-» к строке номер: 656 и ставим нужный нам размер, я ввёл `post_max_size = 80M`.

Сохраняем файл Ctrl+O и Enter, выходим через Ctrl+X.

Чтобы применить все сделанные изменения необходимо перезапустить Apache.

    $ sudo systemctl restart apache2
    

Снова переходим http://0.0.0.0/phpmyadmin и повторяем операцию импорта БД. На этот раз всё должно пройти идеально.

В данной статье мы использовали phpMyAdmin лишь для демонстрации процесса установки и настройки самой утилиты, а также работы с базой данных веб-сайта, поскольку данная утилита является весьма распространённой при работе с веб-хостингом, но не является самой безопасной.

Раз уже все основные действия в phpMyAdmin мы уже выполнили и, вероятно, в ближайшем будушем утилита больше не потребуется, то её лучше отключить, чтобы не подвергать сайт сетевым атакам извне.

Отключение phpMyAdmin выполняется следующими командами в Терминале при подключении к ВМ:

Отключение phpMyAdmin:

    $ sudo a2disconf phpmyadmin.conf && sudo /etc/init.d/apache2 restart
    

Включение phpMyAdmin (если потребуется):

    $ sudo a2enconf phpmyadmin.conf && sudo /etc/init.d/apache2 restart
    

Работать с БД лучше с помощью различных mysql-клиентов, таких как MySQL Workbench или же просто из Терминала (или PowerShell) с помощью команд MySQL. Примеры таких команд приведены ниже:

Вход в MySQL из Терминала (потребует ввода пароля root пользователя, он у нас в блокноте):

    $ mysql -u root –p
    

Создание БД с кодировкой UTF8.

    mysql> CREATE DATABASE 'ИМЯ_БАЗЫ' CHARACTER SET utf8 COLLATE utf8_general_ci;
    

Создание нового пользователя и предоставление ему доступа к БД.

    mysql> GRANT ALL PRIVILEGES ON 'ИМЯ_БАЗЫ'.* TO 'ИМЯ_ПОЛЬЗОВАТЕЛЯ'@'localhost' IDENTIFIED BY 'user_password';
    

Наиболее часто используемые команды MySQL, которые вам могут пригодиться в будущем вы можете найти [здесь](https://gist.github.com/hofmannsven/9164408).

[](#perenosim-fajly-sajta-v-yandeksoblako)Переносим файлы сайта в Яндекс.Облако
-------------------------------------------------------------------------------

Для переноса файла бекапа на виртуальную машину рекомендую воспользоваться FTP-клиентом [FileZilla](https://filezilla-project.org) (доступен для как для Mac OS X, так и для Windows).

Открываем FileZilla, далее переходим «Файл» — «Менеджер сайтов» и добавляем новый сайт. Выбираем SFTP протокол, вводим публичный IP-адрес нашего сайта без http, тип входа выбираем «файл с ключом». Теперь необходимо выбрать файл ключа. Он находится в той самой папке /Users/Username/.ssh/, но поскольку FileZilla не видит скрытой папки по умолчанию, то мы переходим в саму папку в Finder через сочетание клавиш CMD+Shift+G и копируем файл `id_rsa` БЕЗ разрешения `pub`. Скопируйте файл на рабочий стол.

![SSH ключи MacOs](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_keys.png "SSH ключи MacOs")  
_Скриншот: выбор файла ключей для FTP-клиента_

Далее в FileZilla выбираете данный файл с ключом, при этом FileZilla может сказать, что файл не поддерживается и предложит переконвертировать в подерживаемый программой формат, нажимаете «Да» и сохраняете переконвертированный файл на рабочем столе. Нажимаем «Подключиться», тут FileZilla спросит нас кодовую фразу, которую я вам настоятельно рекомендовал запомнить или записать в текстовый файл в самом начале статьи, введите её и вы попадаете на ВМ.

После подключения найдите папку `/var/www/html` на виртуальной машине. К сожалению просто так не получится скопировать файл архива сайта с жесткого диска в папку `html`, по умолчанию для этой папки заданы права 755, что дает право только владельцу копировать/изменять файлы. Файл с ключом же не дает нам право доступа от имени владельца. Поправить это легко. Переходим в терминал к нашей ВМ и вводим команду:

    $ sudo chmod 777 /var/www/html
    

Права получены. Можете копировать файл бекапа в указанную папку через FileZilla. Не забываем удалить `index.html` — он нам больше не нужен.

Поскольку файл бекапа сайта находится в архиве, то необходимо его разархивировать. Переходим опять в терминал к ВМ и вводим команду:

    $ cd /var/www/html
    $ tar -xvf FILENAME.tar.gz
    

Вместо FILENAME указываем название файла с архивом сайта.

Все ваши файлы должны разархивироваться в корневую директорию html, но никак не в поддиректорию `/var/www/html/wordpress`, иначе ваш сайт просто не откроется, проследите за этим. Несколько секунд и файл разархивирован. Далее удаляем файл архива командой в терминале, чтобы он не занимал места:

    $ rm FILENAME.tar.gz
    

После завершения копирования файла бекапа и его распаковки надо не забыть вернуть права для папки `html` и вложенных папок — 755 и отдельно для всех файлов внутри `html` — 644, а для `wp-config.php` отдельно уровень доступа — 600. Набираем в терминале нашей ВМ:

    $ cd var/www/
    $ sudo find ./ -type d -exec chmod 0755 {} \;
    $ sudo find ./ -type f -exec chmod 0644 {} \;
    $ sudo chmod 600 wp-config.php
    

Параметр `f` — ищет все файлы внутри директорий.  
Параметр `d` — ищет все директории внутри `html`.

Если вы все сделали правильно, то перейдя по IP-адресу вашего сайта вы увидите работающий сайт:

![Проверка работы сайта](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_tehnolend.png "Проверка работы сайта")  
_Скриншот: Проверка работоспособности веб-сайта_

Осталось дело за малым, настроить DNS, чтобы сайт открывался через доменное имя.

[](#nastraivaem-dns-dlya-wordpress-sajta-v-yandeksoblake)Настраиваем DNS для WordPress сайта в Яндекс.Облаке
------------------------------------------------------------------------------------------------------------

В моём примере домен зарегистрирован у регистратора WebNames.ru, а сам сайт хранится на Reg.ru. Для начала заходим в личный кабинет регистратора Webnames.ru. Переходим в «Мои домены и услуги» «Управление доменом» «DNS-серверы». У меня прописаны DNS — ns1.hosting.reg.ru, ns2.hosting.reg.ru. Удаляем их и выбираем: «Неймсерверы регистратора (по умолчанию)». После чего переходим в «Управление зоной» и добавляем всего две записи:

Запись A:  
Субдомен: @  
Адрес: указываю публичный IP-адрес виртуальной машины в Яндекс.Облаке.

Запись CNAME:  
Субдомен: www  
Адрес: имя домена с точкой на конце.

Получается вот так:

![Записи DNS webnames](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_dns1.png "Записи DNS webnames")

Для REG.ru вы проделываете почти все тоже самое. Инструкция для Reg.ru [находится здесь](https://cloud.yandex.ru/docs/solutions/web/lamp-lemp#configure-dns).

Отлично, домен привязан к Яндекс.Облаку и сайт открывается!

После этого не будет лишним установить SSL-сертификат для сайта, к тому же делается это абсолютно бесплатно и быстро.

[](#sozdanie-ssl-sertifikata-dlya-sajta-c-pomoshьyu-lets-encrypt-v-yandeksoblake)Создание SSL-сертификата для сайта c помощью Let’s Encrypt в Яндекс.Облаке
-----------------------------------------------------------------------------------------------------------------------------------------------------------

SSL-сертификат позволяет шифровать трафик между пользователем и сайтом и помогает избежать кражи персональных данных при их вводе на сайте. Также сертификат увеличивает уровень доверия пользователя к сайту.

Поисковые системы отлично воспринимают https протокол и негавтивного влияния на SEO он точно не будет оказывать, более того, поисковые системы при прочих равных отдадут предпочтение сайту с сертификатом нежели без него.

Что такое Let’s Encrypt? Это центр сертификации, предоставляющий бесплатные SSL-сертификаты, которые так же безопасны, как и платные сертификаты.

И так перейдём к получению сертификата для сайта. Начнем с обновления списков пакетов и установки общих свойств программного обеспечения.

**Шаг 1. Установка клиент Let’s Encrypt**

В Терминале вводим команду (& & между командами обеспечивает последовательное выполнение одной команды следом за другой):

    $ sudo apt-get update && sudo apt-get install software-properties-common
    

Далее мы добавим репозитории `unverse` and `certbot`:

    $ sudo add-apt-repository universe && sudo add-apt-repository ppa:certbot/certbot
    

Нажмите «Enter», когда потребуется.

Далее установим сам клиент Let’s Encrypt с помощью команды:

    $ sudo apt-get update && sudo apt-get install certbot python-certbot-apache
    

Подтвердите действие нажав «Y» и «Enter».

**Шаг 2. Получение SSL-сертификата**

Вводим в Терминале:

    $ sudo certbot --apache
    

Введите название вашего домена: example.com или www.example.com

В следующем диалоге нужно определиться перенаправлять все страницы с http на https при открытии веб-сайта или нет. Выбираем 2 — перенаправить на https.

Поздравляю, вы получили сертификат и привязали его к вашему домену, протестировать ваш сайт можно с помощью URL (example.com — заменяете на свой домен):

https://www.ssllabs.com/ssltest/analyze.html?d=example.com

![SSL Report](https://storage.yandexcloud.net/cloud-www-assets/blog-assets/ru/posts/2019/03/assets/wp_ssl.png "SSL Report")  
_Скриншот: Установка SSL сертификата с помощью Let’s Encrypt._

**Шаг 3. Автообновление**

Единственное, что вам потребуется в дальнейшем — это обновлять свой сертификат, поскольку он выдаётся лишь на 90 дней. Эта задача решается установкой задачи для планировщика Cron:

    $ sudo crontab -e
    

В диалоге выберите 1й пункт из списка.

И добавим в самый конец строчку кода:

    30 2 * * 1 /usr/bin/certbot renew >> /var/log/le-renew.log
    

В итоге у нас будет запланирована регулярная задача с выполнением каждый понедельник в 2:30 ночи, а результат выполнения будет записан в лог-файл, таким образом вы не пропустите обновление SSL-сертификата.

[](#problemy-pri-perenose-ne-otkryvayutsya-vnutrennie-stranicy-wordpress-sajta-chto-delatь?)Проблемы при переносе. Не открываются внутренние страницы WordPress сайта. Что делать?
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Последнее с чем вы можете столкнуться при переносе сайта от хостера к хостеру это проблема открытия внутренних ссылок. У WordPress иногда возникает данная проблема при переходе от одного хостинга к другому.

Первое, что вам необходимо сделать это проверить существует ли файл `.htaccess` в корневой папке вашего сайта, а именно `/var/www/html/.htaccess`

Если его нет, то вам необходимо его создать через Терминал, вводим команду:

    $ sudo nano /var/www/html/.htaccess
    

и добавляем следующий код:

    <IfModule mod_rewrite.c>
         RewriteEngine On
         RewriteBase /
         RewriteRule ^index\.php$ - [L]
         RewriteCond %{REQUEST_FILENAME} !-f
         RewriteCond %{REQUEST_FILENAME} !-d
         RewriteRule . /index.php [L]
    </IfModule>
    

Сохраняем Ctrl+O и «Enter», Ctrl+X — выход.

Проверяем сайт, если все открывается, отлично. Если нет, то значит в Apache отключена поддержка `.htaccess` файла и надо это исправить:

В терминале вводим команду (в моей версии именно там хранится нужный файл, у вас может отличаться):

    $ sudo nano /etc/apache2/sites-available/000-default.conf
    

и добавляем через CMD+C CMD+V указанный ниже код, сохраняем Ctrl+O и «Enter», Ctrl+X — выходим:

    <Directory /var/www/html>
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
    

Получаем такой результат:

    <VirtualHost *:80 [::]:80>
        ServerAdmin [email protected]
        DocumentRoot /var/www/html
          <Directory /var/www/html>
           AllowOverride All
           Order allow,deny
           allow from all
          </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>
    

Перегружаем конфигурацию Apache для применения изменений:

    $ sudo service apache2 restart
    

Наконец-то после выполнения всех шагов всё заработало! Наслаждаемся результатом работы и оцениваем, как работает Яндекс.Облако!

Надеюсь данная статья помогла вам в решении вашей задачи, удачи вам!
