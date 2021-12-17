# Blockonomics Payment Button API Demo in Laravel

This demo uses the Payment Button API provided by Blockonomics to receive Bitcoin payments. It can be easily integrated with your online store. The video tutorial for this demo can be found [here]( https://www.youtube.com/watch?v=1sE2r5tDkNY).

## Installing Guide

<details open>
<summary> Cloning Repository </summary>

* `git clone https://github.com/AJ-54/Blockonomics_Payment_Button_Demo.git`
* `cd Blockonomics_Payment_Button_Demo`

</details>

<details>
<summary> Installing dependencies </summary>

* `composer install`
* `npm install`
* `cp .env.example .env`
* `php artisan key:generate`
* By now, you have installed all the dependencies and also created copy of the .env file.

</details>

<details>
<summary> Setting up Environment Configurations </summary>

* In the .env file, add database information to allow Laravel to connect to the database, fill in the `DB_HOST`, `DB_PORT`, `DB_DATABASE`, `DB_USERNAME`, and `DB_PASSWORD` options to match the credentials of the local database you created. 
* Place your Blockonomics API Key in the `Blockonomics_API` field. This will allow us to run migrations in the next step.

</details>

<details>
<summary> Migration Code </summary>

* `php artisan migrate`
* `php artisan storage:link`

</details>

<details>
<summary> Blockonomics Website Setup </summary>

* Create your Blockonomics Account- [here](https://www.blockonomics.co/merchants?ref=hPga3rGcrDj45w1C2jzkDMUPGBkCRYxNE6)
* Create your payment button from [here](https://www.blockonomics.co/merchants) by going to PAYMENT BUTTONS/URL tab. Get the button code to paste in the html page from step 01.
* Head to [this line](https://github.com/AJ-54/Blockonomics_Payment_Button_Demo/blob/main/resources/views/home.blade.php#L44) and replace the payment button code with your code.
* Go to `OPTIONS` in the PAYMENT BUTTONS/URL tab on [this page](https://www.blockonomics.co/merchants#/page3). You need to setup the `ORDER HOOK URL` and `Redirection URL`.
* To test the code locally, follow instructions from [this](https://www.youtube.com/watch?v=6Ydk32avIgo) video and make sure to place the `<domain>/receive` as your order hook url and `<domain>/home` as redirection url. Here `<domain>` is the domain you get from reverse proxy (Ngrok/localtunnel).
* Please make sure you are using `http` and not `https`. Your domain would be in `https` but place `http` URL in the order hook url and redirection url. 
* Make sure to save your changes!

</details>

<details>
<summary> The Last Line! </summary>

* `php artisan serve`

<p> Now you are all set to locally run the demo! </p>

</details>


### My Install Log

Blockonomics_Payment_Button_Demo

#### Composer
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-composer-on-ubuntu-20-04
```
$ sudo apt update
$ sudo apt install php-cli unzip
$ sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```
#### Install Log
```
$ composer install
$ composer update
```
 Install or enable PHP's dom extension
 ```
 $ sudo apt install php-xml
 $ composer update
 $ composer install
 $ npm install
 $ cp .env.example .env
 ```
#### MariaDB
```
$ sudo apt update
$ sudo apt install mariadb-server
$ sudo mysql_secure_installation
$ sudo mysqladmin version
```
#### Access denied
```
$ mysql -u root -p
Access denied for user 'root'@'localhost'
```

#### Solution for Access denied
```
> FLUSH PRIVILEGES;
> ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_password';
```

#### Create Database
```
$ CREATE DATABASE metvndb;
$ SHOW DATABASES;
$ CREATE USER 'metvnuser'@'localhost' IDENTIFIED BY 'rainbow8*';
$ GRANT ALL PRIVILEGES ON metvndb.* TO 'metvnuser'@'localhost';
$ FLUSH PRIVILEGES;
$ SHOW GRANTS FOR 'metvnuser'@'localhost';
```

#### Installation LOg 2
Illuminate\Database\QueryException  : could not find driver (SQL: select * from information_schema.tables where table_schema = metvndb and table_name = migrations and table_type = 'BASE TABLE')
```
$ sudo apt install php-mysql
```

#### SMTP 
```
$ sudo apt install postfix
System mail name: metvn.com
$ sudo dpkg-reconfigure postfix
```
* Internet Site
* metvn.com
* metvn
* metvn.com, localhost.localdomain, localhost
* No
* 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 
* 0
* +
* all
```
$ sudo postconf -e 'home_mailbox= Maildir/'
$ sudo postconf -e 'virtual_alias_maps= hash:/etc/postfix/virtual'
$ sudo nano /etc/postfix/virtual
```
```
metvn@metvn.com metvn
```
```
$ sudo postmap /etc/postfix/virtual
$ sudo systemctl restart postfix
$ sudo ufw allow Postfix
$ echo 'export MAIL=~/Maildir' | sudo tee -a /etc/bash.bashrc | sudo tee -a /etc/profile.d/mail.sh
$ source /etc/profile.d/mail.sh
$ sudo apt install s-nail
$ sudo vim /etc/s-nail.rc
```
```
. . .
set emptystart
set folder=Maildir
set record=+sent
```
```
$ echo 'init' | s-nail -s 'init' -Snorecord metvn
$ ls -R ~/Maildir
$ s-nail
$ vim ~/test_message
$ cat ~/test_message | s-nail -s 'Test email subject line' -r contact@example.com user@email.com

```
