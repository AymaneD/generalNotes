# generalNotes
random  notes
%%XX%% is a variable to be changed

# GIT 

=> remove all remotes

        git remote | xargs -n1 git remote remove

=> add new remote 

        git remote add origin git@github.com:%%XX%%.git
 
=> add new branch and switch to it 

        git checkout -b %%XX%%

# PHP 

#find a word in a string

 
strpos($mystring, $wordToFind) === false ? 'Not Found' : 'Ok';

# Symfony


# JS

=> get params from browser url 

=> arrays :

reduce
filter
map

# Flutter / Dart



# Rust


# GoLang 

# Server config


=> Installing JS Dependencies offline 

1 -  install npm bundle -g in your first machien that have internet  https://github.com/majgis/npm-bundle

2- npm-bundle %%XX%%  // %%XX%%  = package name

3- you will see an archive package in the folder, get this file to your offline machine 

4 - npm i %%XX%% // %%XX%%  = archive name


# MYSQL


=> Creating read only user 

1. Log into MySQL as an admin
 
        mysql -u root -p 
 
2. Create a new MySQL user


        CREATE USER ‘$user‘@’127.0.0.1’ IDENTIFIED BY ‘$password‘;

3. Grant read-only permission to the MySQL user


        GRANT SELECT, SHOW VIEW ON $database_name.* TO $user@’127.0.0.1′ IDENTIFIED BY ‘$password‘;

        FLUSH PRIVILEGES;

If you want to use SSL connection, you can use the following instead

        GRANT SELECT, SHOW VIEW ON $database_name.* TO $user@’127.0.0.1′ IDENTIFIED BY ‘$password‘ REQUIRE SSL;

FLUSH PRIVILEGES;


=> allowing remote connections :

1 - 

        sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf

2 - you should now look for the line :

        bind-adress = 127.0.0.1 

and change it to : 

        bind-address : 0.0.0.0

NB : 0.0.0.0  will allow any ip accessing mysql 



