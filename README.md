## Microservices sample project ##

This _Github_ repository features a small microservices sample, using the following libraries:

* __Spring Boot__: together with _Jetty_ as application runner within the _Docker_ containers.
* __Docker__ and __Docker compose__: _Docker_ images are generated and composed in order to run this example.
* __Spring Cloud__: abstract _Netflix OSS_ tooling with the Spring Cloud suite.
* __Netflix OSS__ libraries:
  * __Zuul proxy__: Used to unify all access to services.
  * __Eureka Discovery__: Used to keep track of alive service instances.
  * __Ribbon__: Used to load balance on the client (or invoker) side.
  * __Hystrix__: Used to monitor failure and short-circuit in case it's needed.
  * __Turbine__: Used to monitor service status on a distributed fashion.
* __Angular2__: Used to create a simple front application that consumes the exposed _REST_ services. This application includes _lazy loading_ and _ahead of time (AOT)_ compilation.
* __Webpack__: Used to package the _Angular2_ application and deliver the distributable objects into the microservice.

### Content ###

On top of the mentioned libraries, this sample provides two services:

* Authors-service: service which contains a very simple authors repository.
* Books-service: service which contains a very simple books repository.
* Releases-service: service which contains a very simple releases repository.
* Front-service: service which contains a very simple _Angular2_ front application.

The books service uses the authors service in order to retrieve authors data, serving as a sample of service communication within _Docker_ containers.  
The front service publishes  a frontend application which consumes and manipulates the data exposed by the services.


### Running the sample ###

I've ran this test with the following _Ubuntu_, _Docker_ and _Docker compose_ versions:

* __Ubuntu__: 16.04
* __Docker API__: 1.25
* __Docker Version__: 1.13.0
* __NPM version__: 3.10.10
* __Node version__: 6.9.4
* __Webpack__: 2.2.0
* __Angular 2__: 2.4.6

You ought to follow these steps in order to run this sample on your local machine.

1. Compile the images and get them into your local Docker registry:

On the parent project folder, execute a _Maven_ package command:

```bash
sudo mvn clean install -P docker
```

2. Run the generated images using _Docker compose_:

After you've compiled the projects, you should be able to see the images on your local registry:

```bash
sudo docker images
```

In order to execute the example, run the _docker-compose.yml_ file using the following command at the parent project folder:

```bash
sudo docker-compose up
```

_Optional_: You may want to redirect the console output generated into a file. In this case, use the following command instead:

```bash
sudo docker-compose up > yourfilename.log
```