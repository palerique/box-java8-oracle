Wercker Oracle Java 8 box
=========================

Wercker box with Oracle Java 8, maven, nodejs, compass, yeoman, grunt, bower, phantomjs and karma installed

Basic working example 
---------------------

To build simple application You just have to create ```wercker.yml``` file with following content and place in the root of your project:

```yml
box: palerique/java8-oracle-nodejs@0.0.7
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
        name: Reown directories
        code: |
          sudo chown -R `whoami` /usr/local/lib/node_modules
          sudo chown -R `whoami` ~/.npm
          sudo chown -R `whoami` /home/ubuntu/.npm/
    - script: 
        name: Run Xvfb
          sudo start-stop-daemon --start --quiet --pidfile /tmp/xvfb_99.pid --make-pidfile --background --exec /usr/bin/Xvfb -- :99 -screen 0 1024x768x24 -ac +extension GLX +render -noreset
          sleep 5
          export DISPLAY=:99.0
    - script: 
        name: Run maven
        code: |
          mvn clean install
```

More information http://sitedo.ph/
