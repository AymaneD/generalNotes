# Random Notes and tips...
random  notes
%%XX%% is a variable to be changed

# Linux 

#### lines that exists in a file but not the other , 

```
cat file1.txt file2.txt | sort | uniq --unique
```

#### Remove all files in current very large directory ( arguments list too long ) 

```
find . -maxdepth 1 -type f -exec rm -f {} \;
```

#### Burn ISO To USB Linux
###### Replace X with your usb device name , you can found it by runing this command  first : lsblk  , then : 

```
 sudo dd bs=4M if=ubuntu-20.04.2-desktop-amd64.iso  of=/dev/sdc conv=fdatasync

```





#### config Nginx and NodeJS 

```

```

#### Check Nginx config 

```
sudo nginx -t

```
#### PM2 Change default port for an app 

-> File : ecosystem.config.cjs ( cjs ext for apps using import modules ) // use process.env.PORT to get the port in your app

```
module.exports = {
  apps : [{
    name: "appNodeProccess",
    script: "./app.js",
    node_args : '--experimental-modules',
    autorestart: true,
    env: {
      PORT : 8888
    }
  }]
}
```
# GIT 

#### Remove all remotes

```
        git remote | xargs -n1 git remote remove
```

#### Add new remote 

```
        git remote add origin git@github.com:%%XX%%.git
 ```
 
#### Add new branch and switch to it 

```
        git checkout -b %%XX%%
```


#### remove/discard unstaged changes

```
        git checkout -- .
```

#### Delete remote branch
```
git push origin --delete %%XX%%
```

#### Config git merge tool 

( we are using  vim ) 

```
git config merge.tool vimdiff
```
```
git config merge.conflictstyle diff3
```
```
git config mergetool.prompt false

``` 

###### Choose a way to resolve the conflit

If you want to get changes from REMOTE

```
:diffg RE  
```
If you want to get changes from BASE
```
:diffg BA  
```
If you want to get changes from LOCAL
```
:diffg LO 
 ```
 
###### Save, Exit, Commit and Clean up after merge tool

```
:wqa  
```
```
git commit -m "resolving conflit"
```
```
git clean -i
```


# PHP 

#### Find a word in a string

```
 
        strpos($mystring, $wordToFind) === false ? 'Not Found' : 'Ok';
```

#### Call stored procedure 


```
$stmt = $dbh->prepare("CALL procedure_name(?)");
$stmt->bindParam(1, $return_value, PDO::PARAM_STR, 4000); 

$stmt->execute();

print "returned val: $return_value\n";
```


# Docker

##### Docker compose for sql server express

```
sqldata:
  image: mcr.microsoft.com/mssql/server:2017-latest
  environment:
    - SA_PASSWORD=YourStron@gPa@!!sWoord!
    - ACCEPT_EULA=Y
    - MSSQL_PID=Express
  ports:
    - "5434:1433"
```

# Symfony


# JS

#### Safely access nested object elements 

```
const   isset  = (fn , valToBeReturnOnError = undefined) => {
    let value;
    try {
        value = fn();
    } catch (e) {
        value = undefined;
    } finally {
        return value !== undefined ? value : valToBeReturnOnError;
    }
};


isset(() => window.test.testt[5].x  ) ; // it accept a second param that take a value to be returned in case of error else it will return undefined

```

####  get params from browser url 
```
function gup( name, url ) {
    if (!url) url = location.href;
    name = name.replace(/[\[]/,"\\\[").replace(/[\]]/,"\\\]");
    var regexS = "[\\?&]"+name+"=([^&#]*)";
    var regex = new RegExp( regexS );
    var results = regex.exec( url );
    return results == null ? null : results[1];
}
gup('q', 'https://github.com/?q=abc')
```

####  arrays :

reduce
filter
map
find





####  Converting js object to array 

 //function to be considered     
```
    Object.keys(%%XX%% ) – returns an array of keys.
    Object.values(%%XX%% ) – returns an array of values.
    Object.entries(%%XX%% ) – returns an array of [key, value] pairs.
  ```
  
    
# React

####  clearing interval in react hooks 

```
        useEffect(() => {
                  let intervalToBeCleared = setInterval(() => {
                         //proccess here
                  }, 6000);
           return () => {
           clearInterval(intervalToBeCleared);
          };
         }, []);
  ```
 #### Comment in JSX 
 ```
 {/*this is a comment*/}

 {
        //this is another way to  comment , dont forget to break line
 }
 ```
 #### Access .env vars  
 
 let's supose .env file contain a variable called : API_URL , you shoudl start it with REACT_APP_ , so : REACT_APP_API_URL
 
 ```
 ######### .env content ###########
 
 REACT_APP_API_URL=github.com
 
 ######### .env content ###########

 ```
 
 
 so we can access it using : 
 ```  
  process.env.REACT_APP_API_URL
 ```  
  
 
# Lodash 

#### import specifiq function only 

```
        import orderBy from "lodash/orderBy";
```
# React ANTD ( Ant Design )

#### import specifiq  icon only 

```
        import RollbackOutlined  from "@ant-design/icons/RollbackOutlined";
```
#### import specifiq item only

```
        import Modal from "antd/lib/modal";
        import 'antd/lib/modal/style/css';
```

#### Select default value not working inside Form , you should use the Form  initialValues attr

```
         <Form initialValues={{
            selectName: "defaultVal"
           }} />
  ```         
  
#### start day in ant design datepicker  // antd use moment under the hood so we can update moment to achieve this

```
        import moment from 'moment'
```
```
        moment.updateLocale('en', {
          weekdaysMin : [ "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" , "Sun"]
        });

```

# React Native


# Flutter / Dart



# Rust


# GoLang 

# Server config


#### Installing JS Dependencies offline 

1 -  install npm bundle -g in your first machien that have internet  https://github.com/majgis/npm-bundle
 ```
 npm install -g npm-bundle
  ```

2-  ``` npm-bundle %%XX%%  ```  // %%XX%%  = package name

3- you will see an archive package in the folder, get this file to your offline machine 

4 -  ``` npm i %%XX%%  ```  // %%XX%%  = archive name


# MYSQL


#### Creating read only user 

1. Log into MySQL as an admin
 ```
        mysql -u root -p 
 ```
2. Create a new MySQL user

```
        CREATE USER ‘$user‘@’127.0.0.1’ IDENTIFIED BY ‘$password‘;
```
3. Grant read-only permission to the MySQL user

```
        GRANT SELECT, SHOW VIEW ON $database_name.* TO $user@’127.0.0.1′ IDENTIFIED BY ‘$password‘;

        FLUSH PRIVILEGES;
``` 

If you want to use SSL connection, you can use the following instead
```
        GRANT SELECT, SHOW VIEW ON $database_name.* TO $user@’127.0.0.1′ IDENTIFIED BY ‘$password‘ REQUIRE SSL;
        FLUSH PRIVILEGES;

```

 

####  allowing remote connections :

1 - 

```
        sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```

2 - you should now look for the line :

```
        bind-adress = 127.0.0.1 
```

and change it to : 

```
        bind-address : 0.0.0.0
```

NB : 0.0.0.0  will allow any ip accessing mysql 


#### Triggers 

###### Show existing Triggers   
```
SHOW TRIGGERS ;
```

```
SHOW TRIGGERS
    [{FROM | IN} db_name]
    [LIKE 'pattern' | WHERE expr]
```


###### Drop/Delete/Remove a Trigger   
```
DROP TRIGGER trigger_name;
```
###### Create a trigger   
```
DELIMITER |
CREATE TRIGGER trigger_name BEFORE INSERT
ON table_name FOR EACH ROW
BEGIN
 
 
END |
DELIMITER ;
```



#### Stored Procedures / Functions

###### Show existing Procedures   
```
SHOW PROCEDURE STATUS;
```

```
 SHOW FUNCTION STATUS;
```
###### Drop/Delete/Remove  a stored procedure   
```
 DROP PROCEDURE procedure_name;
```
###### Create a stored procedure   
```
```

###### Call/Execute a procedure
```
CALL procedure_name('a param');

```


#### Views 

###### Show existing Views   
```
SHOW CREATE VIEW 'view_name'
```
OR 
```
SELECT VIEW_DEFINITION FROM INFORMATION_SCHEMA.VIEWS
   WHERE TABLE_NAME = 'view_name'

```
###### Drop/Delete/Remove  a view   
```

DROP VIEW view_name; 
```
###### Create a view   
(change select 1 by you query )
```
CREATE VIEW view_name
AS 
select 1
```

#### Import csv to mysql  

(change FILE_NAME , TABLE_NAME , and FIELDS_NAME , and also you can change the delimiter if it's not a coma etc... )

```
LOAD DATA LOCAL INFILE 'FILE_NAME'
 INTO TABLE TABLE_NAME
 FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"'
 LINES TERMINATED BY '\n'
 IGNORE 1 LINES
 (FIELD_NAME_1,FIELD_NAME_2)
 ```
 
 # SQL SERVER  
 
 # Oracle  
 
 # MongoDB  
 
 # Redis
