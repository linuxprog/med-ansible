Playbook MS Ansible role
=========

An Ansible playbook for automated deployment of java application as linux services.


Requirements
------------

Automatically install Java role

Clone this repo into your roles directory:

    $ git clone https://git.label-factory.ma/software-factory/automation/ansible-roles/java.git roles/app

Usage
-----

    ansible-playbook playbooks/site.yml -e @group_vars/dev --tags application

You can also use the role as a playbook. You will be asked which hosts to provision, and you can further configure the play by using `--extra-vars`.

    $ ansible-playbook -i inventory/$ENV.inv playbooks/site.yml  -e @group_vars/$ENV  -e app_jar=$APP_JAR  --tags application

Author Information
------------------

Mohamed BOUTGOURINE <>