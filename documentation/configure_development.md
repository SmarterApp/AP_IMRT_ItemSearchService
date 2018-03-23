# Development - Getting Started

This project requires certain pieces of software to run. Below is the list and recommended order to install those pieces of software.  

* [Getting Started For Mac](getting_started_mac.md)

## Create database and users

Please refer to the "Create database and users" section within 

## Building with Gradle

The database tests that are part of the build require access to the test database on your local machine. 
Before you can run them you need to export the following environment variables:

```
export SPRING_DATASOURCE_USERNAME=test
export SPRING_DATASOURCE_PASSWORD=<password>
```

You can then run:

```
./gradlew build
```

The standard gradle "build" target will build the source code, run findbugs, and run all unit and integration tests.
If findbugs discovers any issues, the build will fail.

```
./gradlew jacocoTestReport
```

The JaCoCo plugin is enabled, so if you want to generate code coverage reports, just run the standard "jacocoTestReport" gradle task


Test, findbugs, and code coverage reports will be generated in the default location:

```
.projectDir/build/jacocoHtml
```

During development, you may wish to run just unit tests, rather than the full suite of unit and integration tests. There is a gradle task "unitTest" configured for that. 
To support this, all integration tests must follow the naming convention `XxxIntegrationTest.java`

```./gradlew unitTest```

Finally, to disable findbugs, you must use the '-x' argument to gradle to prevent the 2 findbugs tasks from running, for example:

```
./gradlew build -x findBugsMain -x findBugsTest
```

## Docker Support
The project uses the [https://github.com/bmuschko/gradle-docker-plugin] to provide docker support.

To build the docker image locally, run
```
./gradlew dockerBuildImage
```

You will need to set environment variables containing the username and password for your database:

```
export SPRING_DATASOURCE_USERNAME=imrt_ingest
export SPRING_DATASOURCE_PASSWORD=<password>
```

Once all the variables are set, run:
```
cd build/docker
docker-compose up
```

As well as standing up the IMRT ISS service, docker-compose up will also bring up a Spring Cloud Configuration Service.
The configuration service is configured to look in the directory $USER_HOME/sbac/imrt-config-repo for a git based configuration.
For example:

```
mkdir -p ~/sbac/
git clone https://gitlab.com/fairwaytech/imrt-config-repo.git
```

# Command Line Execution

The easiest way to test changes to ISS via the command line is to first use docker-compose to bring up all the containers.
Now use docker stop to kill off ISS. Make sure you have all the required environment variables as described above,
and then run 

```
./gradlew bootRun
```

# Running within an IDE

To execute unit tests within an IDE, make sure that an appropriate `SPRING_DATASOURCE_USERNAME` and `SPRING_DATASOURCE_PASSWORD` are configured.

To execute ISS from with an IDE, make sure the datasource environment variables are set.

