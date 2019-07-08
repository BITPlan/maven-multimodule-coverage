see
- https://blog.doubleslash.de/code-coverage-reports-mit-maven-in-multi-modul-projekten/
- http://wiki.bitplan.com/index.php/Jacoco_maven_multi_module_code_coverage

[![Travis (.org)](https://img.shields.io/travis/BITPlan/maven-multimodule-coverage.svg)](https://travis-ci.org/BITPlan/maven-multimodule-coverage)
[![codecov](https://codecov.io/gh/BITPlan/maven-multimodule-coverage/branch/junit-4/graph/badge.svg)](https://codecov.io/gh/BITPlan/maven-multimodule-coverage/branch/junit-4)

[![BITPlan](http://wiki.bitplan.com/images/wiki/thumb/3/38/BITPlanLogoFontLessTransparent.png/198px-BITPlanLogoFontLessTransparent.png)](http://www.bitplan.com)

# Coverage-Reports with Maven in Multi-Modul-Projects

This is an example configuration for the generation of coverage reports in a maven project consisting of
multiple modules. Coverage reports are generated for unit and integration tests which are aggregated over all modules.
aggregiert sind.

You also get an overall - report showing the total test coverage over unit and integration tests.

To measure the test coverage the
[JaCoCo-Maven-Plugin](http://www.eclemma.org/jacoco/trunk/doc/maven.html) is used.

## Enviroment ##
The project was created and tested with the following environment:

- Maven 3.5
- JUnit 4

Another version of this project for JUnit 5 is available in the
[master branch (german)](https://github.com/doubleSlashde/maven-multimodule-coverage/tree/master).

## Creation of the reports ##
The reports are automatically created during the test execution. An aggregated report for all modules is
created running the Unit-Tests during maven's `test`-phase, by giving the command `mvn test`.

The reports for the integration tests and the aggregated report are created  during the  `verify`-Phase by e.g. starting the  `mvn verify` command. This is also true for later phases after `verify`
e.g.  `mvn install` or `mvn deploy`.

## Storagepath for Reports ##

The Coverage-Reports (HTML) are located in the  `site`-folder as a subfolder of `target` of the module `coverage`:
- `coverage/target/site/jacoco-aggregate-ut/index.html`: Coverage-Report of Unit-Tests
- `coverage/target/site/jacoco-aggregate-it/index.html`: Coverage-Report of Integrationtests
- `coverage/target/site/jacoco-aggregate-all/index.html`: Aggregated Totalreport of Unit- and Integrationstests

## Important when adding modules! ##
The modules you'd like to get reports for needed to be declared as dependencies in the  `pom.xml` of the `coverage`-Module.
Otherwise the module's coverage report will not be integrated into the aggregated report.
