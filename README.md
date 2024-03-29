Role Name
=========

Ansible role for Gitlab installation & configuration.


Requirements
------------

RHEL7-based OS

The following modules are used:
 - community.general.gitlab_user
 - community.general.gitlab_project

Name of gitlab-server in inventory file:

inventory_hostname == "gitlab"

Name of gitlab-runner in inventory file:

inventory_hostname == "runner"


Role Variables
--------------

| Name                      | Description                                            | Type   | Default Value                                                                       |
|------                     |-------------                                           |------  |---------                                                                            |
| ***defaults/main.yml***                                                                                                                                                           |
| arch                      | architecture                                           | string | linux-amd64                                                                         |
| bin_path                  | path to binary                                         | string | /usr/local/bin                                                                      |
| tmp_path                  | temporary path                                         | string | /tmp                                                                                |
| ***yum_gitlab.yml, yum_runner.yml***                                                                                                                                              |
| ce_url                    | gitlab CE repo URL                                     | string | https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh     |
| runner_url                | gitlab runner repo URL                                 | string | https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.rpm.sh |
| ***gitlab.yml***                                                                                                                                                                  |
| gitlab_conf               | path to gitlab config file                             | string | /etc/gitlab/gitlab.rb                                                               |
| gitlab_root_password      | password for gitlab user root                          | string | CHANGEME                                                                            |
| gitlab_api_url            | resolvable endpoint for the API, use http://ip_address | string | CHANGEME                                                                            |
| gitlab_api_token_root     | access API token for root                              | string | CHANGEME                                                                            |
| gitlab_api_token_user     | access APT token for user                              | string | CHANGEME                                                                            |
| gitlab_name               | name of the user                                       | string | CHANGEME                                                                            |
| gitlab_username           | username of the user                                   | string | CHANGEME                                                                            |
| gitlab_password           | the password of the user                               | string | CHANGEME                                                                            |
| gitlab_email              | user's email                                           | string | CHANGEME                                                                            |
| gitlab_confirm            | require confirmation                                   | bool   | no                                                                                  |
| gitlab_sshkey_name        | name of the SSH key                                    | string | CHANGEME                                                                            |
| gitlab_sshkey_file        | SSH public key itself                                  | string | CHANGEME                                                                            |
| gitlab_access_level       | access level to the group                              | string | CHANGEME                                                                            |
| gitlab_project_name       | name of your project                                   | string | CHANGEME                                                                            |
| github_url                | remote github repository                               | string | https://github.com/Borodatko/my_wordpress.git                                       |
| ***runner.yml***                                                                                                                                                                  |
| gitlab_ip                 | gilab server ip address                                | string | CHANGEME                                                                            |
| gitlab_registration_token | registration token                                     | string | CHANGEME                                                                            |
| runner_desc               | gitlab runner description                              | string | ssh-runner                                                                          |
| runner_exec               | gitlab runner executor                                 | string | ssh                                                                                 |
| runner_ssh_host           | remote host, use ip address                            | string | CHANGEME                                                                            |
| runner_ssh_port           | remote host port                                       | number | 22                                                                                  |
| runner_ssh_user           | local admin user                                       | string | centos                                                                              |
| runner_ssh_id             | identity file to be used                               | string | /home/centos/.ssh/id_rsa                                                            |
| runner_ssh_host_key_check | disable SSH strict host key checking                   | bool   | true                                                                                |
| ***exporter.yml***                                                                                                                                                                |
| exporter_version          | prometheus node exporter version                       | string | 1.3.1                                                                               |
| node_exporter_archive     | downloaded archive                                     | string | {{ tmp_path }}/node_exporter-{{ node_exporter_version }}.{{ arch }}.tar.gz          |
| node_exporter_path_tmp    | temporary path                                         | string | {{ tmp_path }}/node_exporter-{{ node_exporter_version }}.{{ arch }}                 |
| systemd_path              | systemd unit file path                                 | string | /etc/systemd/system                                                                 |


Tags
----

Supported tags in tasks:

 - **pretasks**
 - **gitlab**
 - **yum_gitlab**
 - **ce**
 - **yum_runner**
 - **runner**
 - **exporter**


Example of inventory file
-------------------------

```yaml
---
git:
  hosts:
    gitlab:
      ansible_host: CHANGEME
      ansible_ssh_user: CHANGEME
    runner:
      ansible_host: CHANGEME
      ansible_ssh_user: CHANGEME
...
```


Example Playbook
----------------

An example of using role:

```yaml
- name: GitLab Provisioning
  hosts: gitlab
  roles:
    - Gitlab-role
```


License
-------

BSD-3-Clause


Author Information
------------------

https://github.com/Borodatko
