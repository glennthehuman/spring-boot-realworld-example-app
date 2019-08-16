# ![RealWorld Example App using Kotlin and Spring](example-logo.png)

> ### Spring boot + MyBatis codebase containing real world examples (CRUD, auth, advanced patterns, etc) that adheres to the [RealWorld](https://github.com/gothinkster/realworld-example-apps) spec and API.

This codebase was created to demonstrate a fully fledged fullstack application built with Spring boot + Mybatis including CRUD operations, authentication, routing, pagination, and more.

For more information on how to this works with other frontends/backends, head over to the [RealWorld](https://github.com/gothinkster/realworld) repo.

# How it works

The application uses Spring boot (Web, Mybatis).

* Use the idea of Domain Driven Design to separate the business term and infrastructure term.
* Use MyBatis to implement the [Data Mapper](https://martinfowler.com/eaaCatalog/dataMapper.html) pattern for persistence.
* Use [CQRS](https://martinfowler.com/bliki/CQRS.html) pattern to separate the read model and write model.

And the code organize as this:

1. `api` is the web layer to implement by Spring MVC
2. `core` is the business model including entities and services
3. `application` is the high level services for query with the data transfer objects
4. `infrastructure`  contains all the implementation classes as the technique details

# Security

Integration with Spring Security and add other filter for jwt token process.

The secret key is stored in `application.properties`.

# Database

It uses a H2 in memory database (for now), can be changed easily in the `application.properties` for any other database.

# Opening project in Eclipse IDE

At the top of your build.gradle I recommend that you add the eclipse and intellij plugins.

    apply plugin: 'eclipse'
    apply plugin: 'idea'

These plugins function to generate the .project and .classpath files that the eclipse IDE uses (it does the same for IntelliJ, but I don't really know what those files are; *.iml maybe?).

Then from the command line you just do...

    gradle eclipse

...and it figures out the dependencies, pulls the JARs over, and generates the .classpath and .project. If you have eclipse open while you are doing this, refresh the project and Voila. Every time you add a dependency in the build.gradle you do this workflow again. It works like a champ for me.

There is probably some Eclipse plugin to allow you to just do this whole thing from within the IDE. I've been doing it from the commandline for a while now because its just simple.

# Configuring Lombok annotations in Eclipse/STS

Double-click lombok.jar (downloadable from this site, or from your maven repository; it's the same jar). This starts the eclipse installer which will find eclipse (and eclipse variants as listed above), and offers to install lombok into these eclipse installations. The same tool can also uninstall lombok.

You can check if your eclipse installation is lombok-enabled in eclipse's about dialog. The lombok version will be listed at the end of the copyright text.

Please make sure to add below entry into the STS.ini file, if its not already there.

-vmargs -javaagent:lombok.jar

Note: After doing all this if this doesn't worked then make sure to change the workspace and build the code again. It will work

# Getting started

You need Java installed.

    ./gradlew bootRun
    open http://localhost:8888/articles

# Try it out with [Docker](https://www.docker.com/)

You need Docker installed.
	
	docker-compose up -d

# Run test

The repository contains a lot of test cases to cover both api test and repository test.

    ./gradlew test

# Help

Please fork and PR to improve the code.