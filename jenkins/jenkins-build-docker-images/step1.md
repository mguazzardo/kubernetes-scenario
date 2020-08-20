### Инициализируем **Docker File**

Мы подготовим среду с сервером **Jenkins**, работающим как **Docker Container**.

1\. Сначала мы запускаем **container**  в автономном режиме с **tail** к **log file** , который мы создадим и будем использовать позже:

`docker run -d -u root --rm --name jenkins \
    -p 8080:8080 -p 50000:50000 \
    --entrypoint bash \
    jenkins:2.46.2-alpine \
    -c "tail -F /jenkins.log"`{{execute}}

2\. Этот класс не покрывает **Docker**, но для подтверждения успешного выполнения предыдущей команды выполните следующую команду, чтобы убедиться, что контейнер **jenkins** запущен.

`docker ps`{{execute}}

3\. With the next command, we clone a Jenkins Home directory into the container, before we start the Jenkins application. The Jenkins Home directory has been prepared  allow us using Jenkins without any login:

`docker exec -d jenkins \
    bash -c 'git clone https://github.com/oveits/jenkins_home_alpine \
        && export JENKINS_HOME=$(pwd)/jenkins_home_alpine \
        && java -jar /usr/share/jenkins/jenkins.war 2>&1 1>/jenkins.log '`{{execute}}

4\. Wait a moment and run the following command, which will confirm that `jenkins.war` has indeed started:

`docker exec jenkins ps -ef`{{execute}}

> If the process isn't listed, please wait another moment and try again.

5\. Be sure to exit out of the process, before moving on to the next step!

#### Load Dashboard

1\. You can load the Jenkins' dashboard either by clicking the Dashboard tab on the right of Terminal, or clicking the URL: https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/

In the next steps, you'll use the dashboard to configure the plugins and start building Docker Images.