Role Name
=========

Ansible role for Nginx installation & configuration.


Dependencies
------------

 - RHEL7-based OS


Role Variables
--------------

| Name                       | Description                                      | Type   | Default Value                                                              |
|----------------------------|--------------------------------------------------|--------|----------------------------------------------------------------------------|
| ***vars/yum.yml***                                                                                                                                                  |
| repo_path                  | path to repositories directory                   | string | /etc/yum.repos.d                                                           |
| ***vars/nginx.yml***                                                                                                                                                |
| conf_path                  | path to nginx configs                            | string | /etc/nginx/conf.d                                                          |
| ***vars/letsencrypt.yml***                                                                                                                                          |
| domains                    | list of domains via *-d* to obtain a certificate | string | CHANGEME                                                                   |
| email                      | admin email for let's encrypt notifications      | string | CHANGEME                                                                   |
| cert_path                  | path to let's encrypt certificate                | string | /etc/letsencrypt/live/CHANGEME/cert.pem                                    |
| ***vars/exporter.yml***                                                                                                                                             |
| arch                       | architecture                                     | string | linux-amd64                                                                |
| bin_path                   | path to binary                                   | string | /usr/local/bin                                                             |
| tmp_path                   | temporary path                                   | string | /tmp                                                                       |
| exporter_version           | prometheus node exporter version                 | string | 1.3.1                                                                      |
| node_exporter_archive      | downloaded archive                               | string | {{ tmp_path }}/node_exporter-{{ node_exporter_version }}.{{ arch }}.tar.gz |
| node_exporter_path_tmp     | temporary path                                   | string | {{ tmp_path }}/node_exporter-{{ node_exporter_version }}.{{ arch }}        |
| systemd_path               | systemd unit file path                           | string | /etc/systemd/system                                                        |
| ***template variables***                                                                                                                                            |
| domain_name                | domain name                                      | string | CHANGEME                                                                   |
| ip_upstream_alertmanager   | webserver internal ip address                    | string | CHANGEME                                                                   |
| ip_upstream_gitlab         | webserver internal ip address                    | string | CHANGEME                                                                   |
| ip_upstream_grafana        | webserver internal ip address                    | string | CHANGEME                                                                   |
| ip_upstream_prometheus     | webserver internal ip address                    | string | CHANGEME                                                                   |
| ip_upstream_www            | webserver internal ip address                    | string | CHANGEME                                                                   |


Tags
----

Supported tags in tasks:

    - **pretasks**
    - **yum**
    - **nginx**
    - **upstream**
    - **letsenrypt**
    - **exporter**


Example of inventory file
-------------------------

```yaml
---
nginx:
  hosts:
    www:
      ansible_host: CHANGEME
      ansible_ssh_user: CHANGEME
...
```


Example Playbook
----------------

```yaml
- name: Nginx Provisioning
  hosts: nginx
  roles:
    - Nginx-role
```


License
-------

BSD-3-Clause


Author Information
------------------

https://github.com/Borodatko
