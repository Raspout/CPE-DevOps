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

Lancer le playbook
```bash
ansible-playbook -i inventories/setup.yml playbook.yml
```

Le playbook contient les roles suivants (Ils sont exécuté en root grace à l'option `become: true`) :

- docker
  - Installation de lvm2 et device-mapper-persistent-data pour la persistence des données après les
  - Ajout du repo et installation de docker
  - Installation Python3
- network
  - Créée simplement le réseau docker `app-network`
- database
  - Lance le conteneur `raspout/my-database` avec des options, on peut les retrouver (avec des commentaires) [ici](roles/database/tasks/main.yml)
- app
  - Lance le conteneur `raspout/my-backend` avec des options, on peut les retrouver (avec des commentaires) [ici](roles/app/tasks/main.yml)
- proxy
  - Lance le conteneur `raspout/my-httpd` avec des options, on peut les retrouver (avec des commentaires) [ici](roles/proxy/tasks/main.yml)
- front
  - Lance le conteneur `raspout/my-front` avec des options, on peut les retrouver (avec des commentaires) [ici](roles/proxy/tasks/main.yml)
