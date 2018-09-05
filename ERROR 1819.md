# Repo is updated (ERROR 1819 : Your password does not satisfy the current policy requirements)

login to you mysql in the Terminal

`mysql -u root -p and then Enter your password`

and if you want to set a password so quickly all you have to do is :

#### `mysql> set GLOBAL validate_password_policy=LOW;`

and if you wanna set it to medium you should just change low to medium or the highest level.

and then create a user with a new password with the standard of that level.

##### `mysql> create user 'mehdi'@'localhost' identified by 'your password';`

and exit the mysql by typing this:

`mysql> exit`

and then restart the apache:

`systemctl reload apache2.service`

## Another Error in mysql called 1698 Access denied for user 'root'@'localhost'
 something that you can do is to create another user as i said it before in this article (in line 15).<br />
 the reason is that your plugin has been sets to auth_socket in the mysql. and you can see that by typing this piece of code : 
<br />

`mysql> use mysql;` <br />
`mysql> SELECT User, Host, plugin FROM mysql.user;` <br />

and you will see a table and in the plugin section you'll see that root has been sets to auth-socket right?
we have two options but I'll tell that i know is so easy to do.
You can set the root user to use the mysql_native_password plugin : <br />

`$ sudo mysql -u root # I had to use "sudo" since is new installation` <br />

`mysql> USE mysql;`<br />
`mysql> UPDATE user SET plugin='mysql_native_password' WHERE User='root';`<br />
`mysql> FLUSH PRIVILEGES;`<br />
`mysql> exit;`<br />

`$ service mysql restart`<br />


