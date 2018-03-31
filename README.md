# FastFeathers

A collection of bash-shell scripts to install and run various [Feathers](https://feathersjs.com/) examples very quickly.

**Note**:  Please do not simply run these scripts without carefully reviewing this [excellent Feathers tutorial](https://docs.feathersjs.com/guides/readme.html).


All the Feathers examples utilize [Tcl-Expect](https://www.tcl.tk/man/expect5.31/expect.1.html) to automatically respond to the Feathers CLI questions.  It is not required to have a separate VPS environment for a database connection, but it does make it more interesting.  All database examples are using SSH connections.  Testing has been done on  [Centos 7](https://www.centos.org/) / [RHEL](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux).


### List Of Examples:

**feathers-initial-setup.bsh** - Installs and Initializes the feathers enviroment.  Required for every feathers example.

1) **chat-default.bsh** - this will quickly install the [feathers tutorial chat example](https://docs.feathersjs.com/guides/chat/readme.html). 

2) **chat-gmail.bsh** - rework of the **chat-default.bsh** example, except this uses a Gmail address to log in.

3) **chat-github.bsh** - rework of the **chat-default.bsh** example, except this uses a Github address to log in.

4) **gmail-login.bsh** - simple example of using gmail to log in rather than the default authentication (Local Storage NeDB).

5) **gmail-hook.bsh** - simple example of using **gmail-login.bsh**, but includes a hook to capture gmail information such as first name, etc

6) **gmail-service.bsh** - example of using both **gmail-login.bsh** and **gmail-hook.bsh**, but also includes an SQL service to save Gmail information such as first name.  This one has a very crude user-interface using the browser-console.

7) **github-login.bsh** - example of using Github to log in rather than the default authentication (Local Storage NeDB).

8) **github-hook.bsh** - example of using Github-login.bsh, but includes a hook to capture Gmail information such as first name, etc

9) **custom-service.bsh** - a very simple example of a custom service which reverses strings.

10) **jsgrid-sequelize.bsh** - Uses [Js-grid.com](http://js-grid.com/) as the front end user-interface. Options include either [MariaDB](https://mariadb.com/) or [CockroachDB](https://cockroachlabs.com/).  The default is [CockroachDB](https://cockroachlabs.com/).

11) **test-all-hooks.bsh**   - used to test each and every possible hook to help determine execution order.  Creates 42 hooks.


### Databases

1) **init-mariadb-server.bsh** - Install/initialize the [MariaDB](https://mariadb.com/) server for examples which require MariaDB.

2) **init-mariadb-client.bsh** - (Optional) Install a [MariaDB](https://mariadb.com/) client for testing with **_init-mariadb-server.bsh_**

3) **init-cockroach-server.bsh** - Install/initialize the [CockroachDB](https://cockroachlabs.com/) server for examples which require CockroachDB or [PostgreSQL](https://www.postgresql.org).

4) **init-cockroach-client.bsh** - (Optional) install a [CockroachDB](https://cockroachlabs.com/) client for testing with **init-cockroach-server.bsh**


### Tested Environments

1)  [Digital Ocean](https://digitalocean.com) droplets [Centos 7](https://www.centos.org/)
2)  [Google Cloud](google.cloud.google.com) VM instances [Centos 7](https://www.centos.org/)
3)  [Amazon EC2](https://console.aws.amazon.com/ec2) -- [RHEL](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux)
4)  [123systems.net](https://123systems.net) -- [Centos 7](https://www.centos.org/)

### To Run:

1) Create a [VPS](https://en.wikipedia.org/wiki/Virtual_private_server), and optionally a second one for database usage.

2) (Gmail login examples only, suggested but not required for Github login) Obtain a [Namecheap.com](https://namecheap.com) 99-cent domain name for testing Gmail login and point the "A" record of the IP of the VPS from the previous step.

3) Gmail login:  Visit the [Google Oauth2 credentials](https://console.developers.google.com/apis/credentials/oauthclient/) page to create your credentials and get your _**Client ID**_ and _**Client secret**_ values. You will need to fill in _**Authorized Javascript origins**_ (example: http;//fastfeathers.com:3030) and _**Authorized redirect URIs**_ (example: http;//fastfeathers.com:3030/auth/google/callback) using your own domain name in the [Oauth2 credentials](https://console.developers.google.com/apis/credentials/oauthclient/) page.

4) Github login:  Visit the [Oauth Apps](https://github.com/settings/developers) page to create your credentials to get your _**Client ID**_ and _**Client secret**_ values.  You will need to fill in your _**Authorized callback URL**_ (example: http;//123.123.123.123:3030/auth/github/callback) using your own IP number (or domain name) in the[Oauth Apps](https://github.com/settings/developers) page.

5) ```sudo yum --assumeyes install git;   git clone https://edwardsmarkf/fastfeathers ;```

6)  ```bash -vx  ./fastfeathers/init-YOUR_DB_CHOICE-server.bsh;```  Required database server installation for all examples requiring database access.  Optionally install and run the _**./feathers/init-YOUR_DB_CHOICE-client.bsh**_ on the Feathers server to make sure connectivity is working properly.

7) ```bash -vx  ./fastfeathers/feathers-initial-setup.bsh;``` Required for the feathers server.

8) (Optional) Edit your choice of examples for the following (Or edit your _./config/default.json_ file after completion.)
      - HOST -- Domain name required for [Google Oath2 login](https://console.developers.google.com/apis/credentials/oauthclient/) or IP number (or domain name) required for [Github Oath2 login](https://github.com/settings/developers).
      - Client_ID & Secret_ID  -- required for [Google](https://console.developers.google.com/apis/credentials/oauthclient/) & [Github](https://github.com/settings/developers) Oath2 login.
      - DB_USER, DB_PASS, DB_NAME, SERVER_IP -- required for all examples that use a database, values are displayed after DB installation.
      
9) ```bash  -vx  ./fastfeathers/YOUR_CHOICE.bsh ;```   substitute YOUR_CHOICE.bsh for your choice of examples.

10) Instructions to run the feathers example will display on your terminal window.
