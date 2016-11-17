# pdo_informix-php7
Installation of pdo_informix for PHP 7
```
wget https://pecl.php.net/get/PDO_INFORMIX-1.3.2.tgz

tar -xvf PDO_INFORMIX-1.3.2.tgz

cd PDO_INFORMIX-1.3.2/

/usr/bin/phpize7.0

./configure --with-pdo-informix=/opt/IBM/informix --with-php-config=/usr/bin/php-config7.0
```
On error: 
checking for PDO includes... configure: error: Cannot find php_pdo_driver.h.
add the following to ./configure in line 3918:
```
  elif test -f $prefix/include/php/20151012/ext/pdo/php_pdo_driver.h; then
    pdo_inc_path=$prefix/include/php/20151012/ext
```
and try again

```
make

make install

echo "extension=pdo_informix.so" > /etc/php/7.0/mods-available/pdo_informix.ini

ln -s /etc/php/7.0/mods-available/pdo_informix.ini /etc/php/7.0/fpm/conf.d/20-pdo_informix.ini

service php7.0-fpm restart
```
