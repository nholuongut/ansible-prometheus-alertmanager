# Ansible Role: prometheus-alertmanager 

![](https://i.imgur.com/waxVImv.png)
### [View all Roadmaps](https://github.com/nholuongut/all-roadmaps) &nbsp;&middot;&nbsp; [Best Practices](https://github.com/nholuongut/all-roadmaps/blob/main/public/best-practices/) &nbsp;&middot;&nbsp; [Questions](https://www.linkedin.com/in/nholuong/)
<br/>

An Ansible role that installs Prometheus Alertmanager server on Ubuntu-based machines with systemd.

## Requirements

All needed packages will be installed with this role.

## Role Variables

Available main variables are listed below, along with default values:
```yaml
prometheus_alertmanager_version: 0.3.0

prometheus_alertmanager_user: prometheus
prometheus_alertmanager_group: prometheus

prometheus_alertmanager_root_dir: /opt/prometheus/alertmanager
prometheus_alertmanager_templates_files: []
prometheus_alertmanager_resolve_timeout: 5m

prometheus_alertmanager_config_flags:
  'config.file': '{{ prometheus_alertmanager_config_dir }}/alertmanager.yml'
  'storage.path': '{{ prometheus_alertmanager_db_dir }}'
  'web.listen-address': '{{ prometheus_alertmanager_listen_address }}'
```
All variables you can see [here](defaults/main.yml).

## Dependencies

This role doesn't have dependencies.

## Example Playbook
deploy.yml file:
```yaml
- hosts: alertmanager
  roles:
    - { role: nholuong.prometheus-alertmanager }
```
You should create another config parts of main file inside `{{ playbook_dir }}/files/alertmanager_config_parts`.  
I use Ansible [assembly](http://docs.ansible.com/ansible/assemble_module.html) and config parts should have alphabethical order. For example `2-route.yml`:
```yaml
# 2-route.yml
route:
  # The labels by which incoming alerts are grouped together. For example,
  # multiple alerts coming in for cluster=A and alertname=LatencyHigh would
  # be batched into a single group.
  group_by: ['alertname', 'cluster', 'service']
  
  ...
```

# 🚀 I'm are always open to your feedback.  Please contact as bellow information:
### [Contact ]
* [Name: nho Luong]
* [Skype](luongutnho_skype)
* [Github](https://github.com/nholuongut/)
* [Linkedin](https://www.linkedin.com/in/nholuong/)
* [Email Address](luongutnho@hotmail.com)

![](https://i.imgur.com/waxVImv.png)
![](Donate.png)
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/nholuong)

# License
* Nho Luong (c). All Rights Reserved.🌟