Wercker Oracle Java 8 box
=========================

Wercker box with Oracle Java 8, maven, nodejs, compass, yeoman, grunt, bower, phantomjs and karma installed

Basic working example 
---------------------

To build simple application You just have to create ```wercker.yml``` file with following content and place in the root of your project:

```yml
box: palerique/java8-oracle-nodejs@0.0.1
build:
  steps:
    - script:
        name: Show base information
        code: |
          mvn -v
          echo $JAVA_HOME
          java -version
          javac -version
    - script: 
        name: Run maven
        code: |
          mvn clean install
```

More information http://sitedo.ph/
