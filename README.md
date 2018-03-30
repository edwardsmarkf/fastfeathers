# FastFeathers

A collection of bash-shell scripts to run various [Feathers](https://feathersjs.com/) examples very quickly.

**Note**:  Please do not simply run these scripts without carefully reviewing this [excellent Feathers tutorial](https://docs.feathersjs.com/guides/readme.html).


All the Feathers examples utilize [Tcl-Expect](https://www.tcl.tk/man/expect5.31/expect.1.html) to automatically respond to the Feathers CLI questions.  It is not required to have a separate VPS environment for a database connection, but it does make it more interesting.  All database examples are using SSH connections.  Testing has been done on  [Centos 7](https://www.centos.org/) / [RHEL](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux).


### List Of Examples:

**feathers-initial-setup.bsh** - Installs and Initializes the feathers enviroment.  Required for every feathers example.

1) **chat-default.bsh** - this will quickly install the [feathers tutorial chat example](https://docs.feathersjs.com/guides/chat/readme.html). 

2) **chat-gmail.bsh** - rework of the **chat-default.bsh** example, except this uses a Gmail address to log in.

3) **chat-github.bsh** - rework of the **chat-default.bsh** example, except this uses a Github address to log in.

4) **gmail-login.bsh** - simple example of using gmail to log in rather than the default authentication (Local Storage NeDB).

5) **gmail-hook.bsh** - simple example of using **gmail-login.bsh**, but includes a hook to capture gmail information such as first name, etc

6) **gmail-service.bsh** - example of using both **gmail-login.bsh** and **gmail-hook.bsh**, but also includes an SQL service to save Gmail information such as first name, 

7) **github-login.bsh** - example of using Github to log in rather than the default authentication (Local Storage NeDB).

8) **github-hook.bsh** - example of using Github-login.bsh, but includes a hook to capture Gmail information such as first name, etc

9) **custom-service.bsh** - a very simple example of a custom service which reverses strings.

10) **jsgrid-sequelize.bsh** - Uses Js-grid.com as a front end example. Options include either [MariaDb](https://mariadb.com/) or [CockroachDB](https://cockroachlabs.com/).  The default is [CockroachDB](https://cockroachlabs.com/).

11) **test-all-hooks.bsh**   - used to test each and every possible hook to determine execution order.


### Databases

1) **init-mariadb-server.bsh** - Install/initialize the [MariaDB](https://mariadb.com/) server for examples which require MariaDB.

2) **init-mariadb-client.bsh** - (Optional) Install a [MariaDB](https://mariadb.com/) client for testing with **_init-mariadb-server.bsh_**

3) **init-cockroach-server.bsh** - Install/initialize the [CockroachDB](https://cockroachlabs.com/) server for examples which require CockroachDB or [PostgreSQL](https://www.postgresql.org).

4) **init-cockroach-client.bsh** - (Optional) install a [CockroachDB](https://cockroachlabs.com/) client for testing with **init-cockroach-server.bsh**


### Tested Environments

1)  [Digital Ocean](https://digitalocean.com) droplets (cent0s7)
2)  [Google Cloud](google.cloud.google.com) (centos7)  
3)  [Amazon EC2](https://console.aws.amazon.com/ec2) (RHEL)

### To Run:

1) Create a [VPS](https://en.wikipedia.org/wiki/Virtual_private_server), and optionally a second one for database usage.

2) Obtain a [Namecheap](https://namecheap.com) 99-cent domain name for testing Gmail login (Gmail login only, not required for Github login)

3) Point the "A" record of the VPS from step one to the IP address in the second step (Gmail login only, not required for Github login)

4) ```sudo yum --assumeyes install git;   git clone https://edwardsmarkf/fastfeathers ;```

5)  ```bash -vx  ./fastfeathers/init-XXXXX-server.bsh;```  Required for the database server for all examples requiring database access.

6) ```bash -vx  ./fastfeathers/feathers-initial-setup.bsh;``` Required for the feathers server.

7) (Optional) Edit your choice of examples for the following (Or edit your _./config/default.json_ file later)
      - HOST (Domain name required for [Google](https://console.developers.google.com/apis/credentials/oauthclient/) login)
      - Client_ID & Secret_ID  (required for [Google](https://console.developers.google.com/apis/credentials/oauthclient/) & [Github](https://github.com/settings/developers) Oath2 login)
      - IP (required for all examples that use a database)
      
8) ```bash  -vx  ./fastfeathers/XXXXXXX.bsh ;```   substitute XXXXXXX.bsh for your choice of examples.

9) Instructions to run the feathers example should now display on your terminal window.
