# Repo is updated (ERROR 1819 : Your password does not satisfy the current policy requirements)

login to you mysql in the Terminal
mysql -u root -p and then Enter your password

and if you want to set a password so quickly all you have to do is :

### mysql> set GLOBAL validate_password_policy=LOW;

and if you wanna set it to medium you should just change low to medium or the highest level.

and then create a user with a new password with the standard of that level.

mysql> create user 'mehdi'@'localhost' identified by 'your password'; 
mysql> exit

systemctl reload apache2.service
