Role Name
=========

Ansible role for Gitlab installation & configuration.


Requirements
------------

The following modules are used:
 - community.general.gitlab_user
 - community.general.gitlab_group
 - community.general.gitlab_project


Role Variables
--------------
| Name | Description | Type | Default Value|
|------|-------------|------|---------|
| ***defaults/main.yml*** |
| arch | architecture  | string | linux-amd64 |
| bin_path | path to binary  | string | /usr/local/bin |
| tmp_path | temporary path  | string | /tmp |
| ***yum_gitlab.yml, yum_runner.yml*** |
| ce_url | gitlab CE repo URL | string | https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh |
| runner_url | gitlab runner repo URL | string | https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.rpm.sh |
| ***gitlab.yml*** |
| gitlab_conf | path to gitlab config file | string | /etc/gitlab/gitlab.rb |
| gitlab_root_password | password for gitlab user root | string | CHANGEME |
| gitlab_api_url | resolvable endpoint for the API | string | CHANGEME |
| gitlab_api_token_root | access API token for root | string | CHANGEME |
| gitlab_api_token_user | access APT token for user | string | CHANGEME |
| gitlab_name | name of the user | string | CHANGEME |
| gitlab_username | username of the user | string | CHANGEME |
| gitlab_password | the password of the user | string | CHANGEME |
| gitlab_email | user's email | string | CHANGEME |
| gitlab_confirm | require confirmation | bool | no |
| gitlab_sshkey_name | name of the SSH key | string | CHANGEME |
| gitlab_sshkey_file | SSH public key itself | string | CHANGEME |
| gitlab_access_level | access level to the group | string | CHANGEME |
| gitlab_project_name | name of your project | string | CHANGEME |
| github_url | remote github repository | string | CHANGEME |
| ***runner.yml*** |
| gitlab_ip | gilab server ip address| string | CHANGEME |
| gitlab_registration_token | registration token | string | CHANGEME |
| runner_desc | gitlab runner description | string | ssh-runner |
| runner_exec | gitlab runner executor | string | ssh |
| runner_ssh_host | remote host | string | CHANGEME |
| runner_ssh_port | remote host port | number | 22 |
| runner_ssh_user | user name | string | CHANGEME |
| runner_ssh_password | user password | string | CHANGEME |
| runner_ssh_id | identity file to be used | string | CHANGEME |
| runner_ssh_host_key_check | disable SSH strict host key checking | bool | true |
| ***exporter.yml*** |
| node_exporter_version | prometheus node exporter version | string | 1.3.1 |
| node_exporter_archive | downloaded archive | string | {{ tmp_path }}/node_exporter-{{ node_exporter_version }}.{{ arch }}.tar.gz |
| node_exporter_path_tmp | temporary path | string | {{ tmp_path }}/node_exporter-{{ node_exporter_version }}.{{ arch }} |
| systemd_path | systemd unit file path | string | /etc/systemd/system |


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

Borodatko
