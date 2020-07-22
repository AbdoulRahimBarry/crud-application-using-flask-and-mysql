# crud-application-using-flask-and-mysql
A simple CRUD application using Flask and MySQL

[![Build Status](http://ec2-54-161-240-27.compute-1.amazonaws.com/buildStatus/icon?job=crud-application-using-flask-and-mysql-ci)](http://ec2-54-161-240-27.compute-1.amazonaws.com/job/crud-application-using-flask-and-mysql-ci/)

### Built With.

* Python
* Python Libraries: flask and pymysql
* MySQL
* AdminLTE 2

### Running on Docker

```
docker-compose up -d
```

After executing, you will have 2 running cointainers on your Docker host: `phonebook-app` and `phonebook-mysql`. For accessing the web application, open your browser and go to http://your-docker-host-ip-address:8181

To destroy the containers, execute:

```
docker-compose down --rmi all
```.....
