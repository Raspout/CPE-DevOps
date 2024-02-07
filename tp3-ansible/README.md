# TP3 - Ansible

Pour avoir des infos sur la distribution linux du serveur:

```bash
ansible all -i inventories/setup.yml -m setup -a "filter=ansible_distribution*"
```

Pour désinstaller un package yum avec le module ansible yum 


```bash
ansible all -i inventories/setup.yml -m yum -a "name=httpd state=absent" --become
```

> remarque: --become permet d'éxecuter la tâche en root sur le serveur distant



