# 4Wheels - React Example With PHP & MySQL By Matan Aviav


This repository contains an example of a full responsive dynamic React system with PHP & MySQL, built by me (Matan Aviav).

## Table of contents:
1. Introduction

2. Tools I used in this project

3. Originality

4. Security

5. Live demo

<br/><br/>
## 1. Introduction:
I wanted to build an example of a full responsive dynamic React web system with PHP & MySQL database. <br/>
Finally, I decided to build a full 'Cars Selling' web system named ***4 Wheels.*** <br/>The idea is similar to websites like Yad2, WinWin and more.<br/>


### Screenshots of the system:
![GitHub Logo](https://i.ibb.co/HY0mwB1/1.png)

<br />

![GitHub Logo](https://i.ibb.co/vvcmXYw/2.png)

<br />

![GitHub Logo](https://i.ibb.co/4SbxLYY/3.png)

<br />

![GitHub Logo](https://i.ibb.co/t4J0S0J/4.png)

<br />

![GitHub Logo](https://i.ibb.co/9m016Lc/5.png)

<br />

![GitHub Logo](https://i.ibb.co/4VKLbc3/6.png)

<br />

![GitHub Logo](https://i.ibb.co/SJKLzP7/7.png)




<br />



## 2. Tools I used in this project:


To write the code I used Visual Studio Code.
To run React I used Node.js server environment for Win64 and to run PHP (version 7.2) I used WampServer with built-in MySQL server.
In this project I used: React, Redux, Axios, FontAwsome, GoogleChart API, jQuery, JavaScript, Bootstrap 4, CSS, HTML5, PHP, SQL.

* ***React & Redux:***<br/>
React is the dominant tool in this project. I built the whole project according it. Mainly, I used React to navigate between pages instead of reload pages in every request, and for using complex components. Of course, I exploited the main feature that React offers: asynchronic code. In order to send POST/GET requests, I decided to use 'Axios' module. In order to navigate between components, I used 'react-router-dom' module. Redux is used in order to manage global state.

* ***jQuery & Vanilla JavaScript:***<br/>
I used jQuery in order to apply some animated effects during the use in the website. Vanilla JavaScript has many uses. For example: to add input validators to show the user the rules for any input, in real-time. Another example: to make 'Drag & Drop' pictures uploading process.

* ***Bootstrap 4 & CSS:***<br/>
I used Bootstrap 4 in order to style the website.

* ***PHP & SQL:***<br/>
I used PHP (version 7.2) in order to handle all requests from client-side like: login, show all posts, show filters and a lot more. PHP is the core of the backend here. The idea is simple: when the user perform an action then React send a POST or GET request to the backend (PHP). When a specific PHP file get the request, it handles it and return the result back to React. According to the result returned, React performs a specific action. I used PHP to connect to MySQL server, and to write/get data to/from the database. I decided to use PDO PHP class to connect to MySQL server. SQL, of course, is used to prepare SQL statements in order to get data and to insert data. 

  MySQL tables structures:<br />
  ```
    CREATE TABLE `cars` (
      `id` bigint(20) UNSIGNED NOT NULL AUTO_INCREMENT,
      `manuId` bigint(20) NOT NULL,
      `modelId` bigint(20) NOT NULL,
      `typeId` smallint(2) NOT NULL,
      `gearId` tinyint(2) NOT NULL,
      `year` mediumint(4) NOT NULL,
      `km` int(7) NOT NULL,
      `hand` tinyint(2) NOT NULL,
      `engineId` tinyint(2) NOT NULL,
      `engineVol` smallint(5) NOT NULL,
      `pictures` mediumtext,
      `des` mediumtext,
      `prevOwnerId` bigint(20) NOT NULL,
      `nowOwnerId` bigint(20) NOT NULL,
      `carNumber` int(9) NOT NULL,
      `price` int(9) NOT NULL,
      `date` date NOT NULL,
      `testUntil` date NOT NULL,
      `isSold` tinyint(1) NOT NULL,
      `isHidden` tinyint(1) NOT NULL,
      `saleDate` date DEFAULT NULL,
      PRIMARY KEY (`id`),
      FOREIGN KEY (`manuId`) REFERENCES `manus` (`id`) ON DELETE CASCADE,
      FOREIGN KEY (`modelId`) REFERENCES `models` (`id`) ON DELETE CASCADE,
      FOREIGN KEY (`typeId`) REFERENCES `types` (`id`) ON DELETE CASCADE,
      FOREIGN KEY (`gearId`) REFERENCES `gears` (`id`) ON DELETE CASCADE,
      FOREIGN KEY (`engineId`) REFERENCES `engines` (`id`) ON DELETE CASCADE,
      FOREIGN KEY (`prevOwnerId`) REFERENCES `hands` (`id`) ON DELETE CASCADE,
      FOREIGN KEY (`nowOwnerId`) REFERENCES `hands` (`id`) ON DELETE CASCADE
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;

    CREATE TABLE `engines` (
      `id` bigint(20) UNSIGNED NOT NULL AUTO_INCREMENT,
      `name` varchar(35) NOT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;

    CREATE TABLE `gears` (
      `id` bigint(20) UNSIGNED NOT NULL AUTO_INCREMENT,
      `name` varchar(35) NOT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;

    CREATE TABLE `hands` (
      `id` bigint(20) UNSIGNED NOT NULL AUTO_INCREMENT,
      `name` varchar(35) NOT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;

    CREATE TABLE `manus` (
      `id` bigint(20) UNSIGNED NOT NULL AUTO_INCREMENT,
      `name` varchar(35) NOT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;

    CREATE TABLE `models` (
      `id` bigint(20) UNSIGNED NOT NULL AUTO_INCREMENT,
      `manuId` bigint(20) NOT NULL,
      `typeId` tinyint(2) NOT NULL,
      `name` varchar(35) NOT NULL,
      `fromYear` smallint(4) NOT NULL,
      `toYear` smallint(4) NOT NULL,
      PRIMARY KEY (`id`),
      FOREIGN KEY (`manuId`) REFERENCES `manus` (`id`) ON DELETE CASCADE,
      FOREIGN KEY (`typeId`) REFERENCES `types` (`id`) ON DELETE CASCADE
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;

    CREATE TABLE `types` (
      `id` bigint(20) UNSIGNED NOT NULL AUTO_INCREMENT,
      `name` varchar(35) NOT NULL,
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;

    CREATE TABLE `users` (
      `id` bigint(20) UNSIGNED NOT NULL AUTO_INCREMENT,
      `username` varchar(35) NOT NULL,
      `pass` varchar(255) NOT NULL,
      `isAdmin` tinyint(1) NOT NULL,
      PRIMARY KEY (`id`),
    ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8;
  ```
  
* ***HTACCESS:***<br/>
In order to complete a good deployment process, I had to create a .HTACCESS file in order to change the server configuration.
The reason for that: any React route is not considered as a valid path by the server, because for any route there is no an existing file,
and when the user try to navigate to any route directly from the url, then he will get a 404 error.

  The following .HTACCESS code solves the problem:
  ```
  RewriteEngine On
  # If an existing asset or directory is requested go to it as it is
  RewriteCond %{DOCUMENT_ROOT}%{REQUEST_URI} -f [OR]
  RewriteCond %{DOCUMENT_ROOT}%{REQUEST_URI} -d
  RewriteRule ^ - [L]

  # If the requested resource doesn't exist, use index.html
  RewriteRule ^ /index.html
  ```
Another use of HTACCESS is to manage permissions to files and directories on the server. I used Options, Deny & Allow, FilesMatch and more features.


<br />


## 3. Originality:
All PHP files and JavaScript files have written by me (MatanAviav). I wanted to keep on originality during the whole project process.



<br />


## 4. Security:
In order to secure the system, I needed to take control on the data the user insert to the database, and also take control on the data that comes from the database. In addition, I had to find a way to make the user authentication method secure and to find a way to secure sensitive user data like passwords.

  1. *User Authentication:<br />*
  In order to make a secure user authentication, I decided to use a token-based authentication with JWT (JSON Web Tokens). In every successful login, the system take a specific action according to the user choice if to save the connection or not. If the user decided NOT to save the connection then all of his connections details will be saved in SERVER SESSION. If the user DID decided to save the connection then an unique JWT token will be created and will be saved in a httpOnly cookie. The decision to save the cookie as httpOnly is to prevent the access to document.cookie by hackers in case of XSS attack. When the user closes the browser and come back to the system, then the system automatically check the validity of the JWT token. Simple.
 
  2. *User Input (XSS and SQL Injection):<br />*
  In order to secure user input, I started with JavaScript validators (based on regular expressions) for any input. But that way is not enough, of course, because any user can edit the code and remove the validators because the code is on client-side. To solve that, I had to add my own validators to the backend. In PHP files that receive POST/GET data from any a React request, I took any input and checked whether its valid or not, using regular expressions and other techniques. That way, I took control of the user input but I it's still not enough. In order to fully secure user input when insert/get data to/from the database, I had to prevent SQL INJECTION. So, in order to prevent SQL INJECTION, I used prepared statements instead of regular queries. That way, I took full control of the user input. Of course, every problematic operation with the database, input rules, or working with files - is wrapped with try & catch blocks.
  
  3. *Data Comes From The Database (XSS):<br />*
  In order to prevent XSS, I had to take control of any type of script stored in the database that wish to be shown. I did not have to do almost anything here. The reason for that: by default, React does it automatically in render() function. Note that I don't use 'dangerouslySetInnerHTML'.
  
  4. *User Password:<br />*
  In order to secure user password in the database, I decided to use password_hash() PHP function, according to the recommendation in the official PHP documentation. I used this function in order to hash the password, with 2 SALT strings, and when the user try to login I used password_verify() PHP function to verify the password. The advantage of this technique is that password_hash() function does not create a CONSTANT hash - it can change in every function call.

  5. *Prevent CSRF Attacks:<br />*
  In order to prevent CSRF attakcs, I built a token-based mechanism to provide the user a token for any protected action he does in the website. The process is simple: the user gets a token from the backend, and when the user try to send a request from the client-side to the backend, the token will be sent automatically as an argument in the request. Then, when React gets the response, a new token fetched from the it (the response) and save it in Redux's store for the next request. That way, there is no possible way a hacker can manipulate a user to do any malicious action, because a hacker can't guess the token. That way, I can know for sure what is the source of the request.
  
  6. *Prevent Server Flooding:<br />*
  In order to prevent a lot of requests in very short time period (requests flooding), I built a mechanism to handle that. I wanted to block clients and logged users from sending too many requests to the backend. Note that the mose expensive operations are related to the database jobs. I had to save information about any client/user in order to recognize the client/user. I thought about saving their details in the database, but I wanted to prevent database flooding too. Finally, I decided to use files for that: for every suspicious client/user, I create a file and save into it an IP address or an user id number. In addition to that detail, I also save the time of the last request. In short: the mechanism works great.
  
  7. *Unrestricted File Upload:<br />*
  In the control panel, a user can add pictures for any car he want. In order to secure the process, I had to deal with many problems. The major problem is to identity if the picture the user want to upload is valid. To know that, I used PHP 'finfo' class, that check 'Magic Numbers'. Of course, I checked the suffix and the MIMETYPE of every file. In addition, at runtime I used chmod() function to give the only write/read permissions to every file, and with HTACCESS I force the response to be image/png or image/jpeg only. The access to .php files is forbidden.
  

<br />

## 5. Live demo:
To see a live demo of the system, please go to: http://4wheels.myartsonline.com



