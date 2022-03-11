# Web Server Workshop

This workshop is intended to students of EPITA SIGL specialization.

In this workshop you will:
- learn how to communicate with a remote server from your local host
- expose a web page using NGINX

## Step 0 - Create your Github project

From now on until the end of the course, you will code on your own github repository.
Only one repository is needed per pair of students

- Create a new project with the following name format `socra-group-XX` replacing XX by your group number (from 1 to 29)
  - keep 1 digit for groups 1 to 10 (e.g. `socra-group-1` for group 1)
  - make sure your repository is private
- Once created, add push a README.md file with your Group number and EPITA logins
```plain
// inside README.md
# SOCRA Group 30

Owners:
- fauchi_f <florent.fauchille@epita.fr>
- boisse_l <lucas.boisserie@epita.fr>
```
- And add teachers as collaborators:
  - lucas: [LucasBoisserie](https://github.com/LucasBoisserie)
  - florent: [ffauchille](https://github.com/ffauchille)

## Step 1 - Connect to your remote server

This step is only to make sure you have understood how to access your remote server from your local host.

To do so:
- Download your SSH key provided by your teachers
- Once downloaded, type the following commands to connect remotely:
```sh
# From your favourite terminal session

# SSH KEY path can be relative or absolute
$ ssh -i <path_to_your_ssh_key> sigl@group-XX.socra-sigl.fr

# Accept the prompt message (only happens on first SSH connection)
# You should be connected remotely
```
- Add an `AUTHORS.txt` in sigl's user home with your logins:
```plain
# Inside AUTHORS.txt
* fauchi_f
* boisse_l
```

## Step 2 - Deploy your first web application

In this last step, you will deploy a very minimal first web application on internet.
It will be a simple `html` page with your group and logins.

- Connect to your remote server via ssh
- Install [nginx](https://ubuntu.com/tutorials/install-and-configure-nginx#2-installing-nginx):
```sh
sudo apt update
sudo apt install nginx
```
- Make sure you can see the default `Welcome to nginx!` page from your browser by visiting your group's address http://group-XX.socra-sigl.fr (replace XX by your group number)
- On your local host, create a new `index.html` file with:
```html
<!doctype html>
<html>
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>SOCRA Group XX</title>
  </head>
  <body>
    <h1>Group XX</h1>
    <ul>
      <li>fauchi_f</li>
      <li>boisse_l</li>
    </ul>
  </body>
</html>

``` 
- Make sure to replace `XX` by your group number
- Make sure to replace list's logins (fauchi_f and boisse_l) by logins member of your pair

Make sure your HTML displays correctly on your browser (simply open your html file with your browser)

Deploy your index.html file by replacing default's NGINX html file on your remote server:
```sh
# from your local host
$ scp -i <path_to_your_ssh_key> <path_to_your_index.html> sigl@group-XX.socra-sigl.fr:/usr/share/nginx/html/index.html
```
- You should be all set! 
- Visits your group's address and you should see your group's participants

Congratulation, you just deployed your first version of SOCRA on internet!

