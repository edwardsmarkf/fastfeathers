# FastFeathers

A collection of bash-shell scripts to run various feathers examples very quickly

Note:  Please do not simply run these without going through the excellent feathers tutorial here:  https://docs.feathersjs.com/guides/readme.html

All the Feathers examples all use tcl-expect to answer the CLI questions.


List Of Examples:

feathers-initial-setup.bsh - this will install the feathers enviroment.  required for every feathers example.


chat-default.bsh - this will quickly install the chat example here: https://docs.feathersjs.com/guides/chat/readme.html.  its entirely written from this site and the results should be indentical.

chat-gmail.bsh - a rework of the chat-default.bsh example, except this uses a gmail address to log in.

chat-github.bsh - a rework of the chat-default.bsh example, except this uses a github address to log in.

gmail-login.bsh - a very simple example of using gmail to log in rather than the default authentication (Local Storage).

gmail-hook.bsh - a very simple example of using gmail-login.bsh, but includes a hook to capture gmail information such as first name, etc

gmail-service.bsh - a very simple example of using gmail-login.bsh and gmail-hook.bsh, but also includes an SQL service to save gmail information such as first name, 

github-login.bsh - a very simple example of using github to log in rather than the default authentication (Local Storage).

github-hook.bsh - a very simple example of using github-login.bsh, but includes a hook to capture gmail information such as first name, etc

custom-service.bsh - a very simple example of a custom service which reverses strings.

jsgrid-sequelize - Uses Js-grid.com as a front end example.


## Databases

init-mariadb-server.bsh - install & initialize the mariadb server for examples which require mariadb SQL

init-mariadb-client.bsh - install a mariadb client for testing with init-mariadb-server.bsh

init-cockroach-server.bsh - install & initialize the cockroach server for examples which require cockroach SQL

init-cockroach-client.bsh - install a cockroach client for testing with init-cockroach-server.bsh





These scripts has been tested on the following:
1)  digitalocean droplets (cent0s7)
2)  google.cloud.google.com (centos7)  
3)  amazon-ec2 (RHEL)

