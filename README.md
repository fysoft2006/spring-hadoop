The [Spring for Apache Hadoop](http://projects.spring.io/spring-hadoop/) project provides extensions to [Spring](http://projects.spring.io/spring-framework/), [Spring Batch](http://projects.spring.io/spring-batch/), and [Spring Integration](http://projects.spring.io/spring-integration/) to build manageable and robust pipeline solutions around Hadoop.

Spring for Apache Hadoop extends Spring Batch by providing support for reading from and writing to HDFS, running various types of Hadoop jobs (Java MapReduce, Streaming, [Hive](http://hive.apache.org),  [Pig](http://pig.apache.org)) and [HBase](http://hbase.apache.org). An important goal is to provide excellent support for non-Java based developers to be productive using Spring Hadoop and not have to write any Java code to use the core feature set.

Spring for Apache Hadoop also applies the familiar Spring programming model to Java MapReduce jobs by providing support for dependency injection of simple jobs as well as a POJO based MapReduce programming model that decouples your MapReduce classes from Hadoop specific details such as base classes and data types.

# Docs

You can find out more details from the [user documentation](http://docs.spring.io/spring-hadoop/docs/current/reference/html/) or by browsing the [javadocs](http://docs.spring.io/spring-hadoop/docs/current/api/). If you have ideas about how to improve or extend the scope, please feel free to contribute.

# Artifacts

For build dependencies to use in your own projects see our [Quick Start](http://projects.spring.io/spring-hadoop/#quick-start) page.

# Building

Spring for Apache Hadoop uses Gradle as its build system. To build the system simply run:

    gradlew

from the project root folder. This will compile the sources, run the tests and create the artifacts. Note that the tests by default tries to access a localhost single-node Hadoop cluster. 

## Supported distros

By default Spring for Apache Hadoop compiles against the Apache Hadoop 2.5.x stable relase (hadoop25) *.

The following distros and versions are also supported:

- Apache Hadoop 2.4.x (hadoop24) *
- Pivotal HD 2.1 (phd21) *
- Cloudera CDH5 (cdh5) *
- Hortonworks HDP 2.0 (hdp20) *
- Hortonworks HDP 2.1 (hdp21) *

\* The distributions noted with and asterisk will include spring-yarn support in the build.

* For anyone using older distros and versions we recommend using either Spring for Apache Hadoop 1.0.x which is maintained here: https://github.com/spring-projects/spring-hadoop/tree/1.0.x or Spring for Apache Hadoop 2.0.x which is maintained here: https://github.com/spring-projects/spring-hadoop/tree/2.0.x

To compile against a specific distro version pass the `-Pdistro=<label>` project property, like so:

    gradlew -Pdistro=hadoop24 build

Note that the chosen distro is displayed on the screen:

    Using Apache Hadoop 2.4.x [2.4.1]

In this case, the specified Hadoop distribution (above Apache Hadoop 2.4.x) is used to create the project binaries.

# CI Builds

The results for CI builds are available at [Spring Data Hadoop: Project Summary - Spring CI](https://build.spring.io/browse/SPRINGDATAHADOOP)

We are currently running tests against the following distributions:
* Apache Hadoop 2.5.1
* Cloudera CDH5
* Hortonworks HDP 2.1
* Pivotal HD 2.1

# Testing

For its testing, Spring for Apache Hadoop expects a pseudo-distributed/local Hadoop instalation available on `localhost` configured with a port of `8020` for HDFS. The `local` Hadoop setup allows the project classpath to be automatically used by the Hadoop job tracker. These settings can be customized in two ways:

* Build properties

From the command-line, use `hd.fs` for the file-system (to avoid confusion, specify the protocol such as 'hdfs://', 's3://', etc - if none is specified, `hdfs://` will be used), `hd.rm` for the YARN resourcemanager, `hd.jh` for the jobhistory and `hd.hive` for the Hive host/port information, to override the defaults. For example to run against HDFS at `dumbo:8020` one would use:

    gradlew -Phd.fs=hdfs://dumbo:8020 build

* Properties file

Through the `test.properties` file under `src/test/resources` folder (further tweaks can be applied through `hadoop-ctx.xml` file under `src/test/resources/org/springframework/data/hadoop`).

## Enabling Hbase/Hive/Pig/WebHdfs Tests
Note that by default, only the vanilla Hadoop tests are running - you can enable additional tests (such as Hive or Pig) by adding the tasks `enableHBaseTests`, `enableHiveTests`, `enablePigTests` or `enableWebHdfsTests` (or `enableAllTests` in short). Use `test.properties` file for customizing the default location for these services as well.

## Disabling test execution
You can disable all tests by skipping the `test` task:

    gradlew -x test


# Contributing

Here are some ways for you to get involved in the community:

* Get involved with the Spring community on StackOverflow using the [spring-data-hadoop](http://stackoverflow.com/questions/tagged/spring-data-hadoop) tag to post and answer questions.
* Create [JIRA](https://jira.springframework.org/browse/SHDP) tickets for bugs and new features and comment and vote on the ones that you are interested in.
* Watch for upcoming articles on Spring by [subscribing](http://spring.io/blog.atom) to the Spring Blog.

Github is for social coding: if you want to write code, we encourage contributions through pull requests from [forks of this repository](http://help.github.com/forking/). If you want to contribute code this way, read the Spring Framework [contributor guidelines] (https://github.com/spring-projects/spring-framework/blob/master/CONTRIBUTING.md).

# Staying in touch

Follow the project team ([Mark](http://twitter.com/markpollack), [Thomas](http://twitter.com/trisberg)) or [Janne](https://twitter.com/tunebluez)) on Twitter.

In-depth articles can be found at the Spring [blog](http://spring.io/blog), and releases are announced via our [news feed](http://spring.io/blog/category/news).
