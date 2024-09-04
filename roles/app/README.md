# Ansible Java

Deploy Java applications as linux services.

## Requirements

Your Java application should be previously packaged as a fully executable jar as explained here :

https://docs.spring.io/spring-boot/docs/current/reference/html/deployment-install.html#deployment-script-customization-conf-file

## Role Variables

| Variable     | Default       | Description    |
| ------------ | ------------- | -------------- |
| project_name |               | The name of the project the application belongs to. |
| app_name     |               | The name of the Java application. |
| app_folder   | /opt/{{ app_name }} | The directory where the application will be installed. By default, it is set to /opt/{{ app_name }}. | 
| app_layer    |               | The layer of the application (e.g., frontend, backend, etc).         |
| app_jar      |               | The name of the JAR file for the Java application.                   |
| app_config   |               | The path to the configuration file for the application.              |
| aws_packages_bucket |        | The name of the S3 bucket where the application packages are stored. |
| java_install | true          | A boolean value indicating whether or not Java should be installed on the server. |
| java_cmd     |               | The command used to run Java. |
| app_user     |  springboot   | Linux user to run Java application |
| app_group    |  springboot   | Linux group to run Java application |

## Example Playbook

  playbook :

    - hosts: all
      vars:
        project_name : project-name
        app_name: spring-boot-sample
        app_layer : microservices
        app_jar: spring-boot-sample.jar
        app_config : application.yml
        aws_packages_bucket : bucket-name
        java_install : true
        java_cmd : /usr/bin/java -Dspring.cloud.bootstrap.location={{ app_folder }}/{{ app_config }} -jar {{ app_folder }}/{{ app_jar }}
      roles:
        - role: java
  
Author Information
------------------

