Role Name
=========

Clona o repositorio [pg-promise](https://github.com/fabiokleis/pg-promise), instala dependencias, node modules, starta o codigo e postgresql localmente.

Requirements
------------

1. Módulos:
   1. [geerlingguy.nodejs](https://galaxy.ansible.com/geerlingguy/nodejs)


Role Variables
--------------

- `dir`: local do diretório do app
- `pg_conf`: local do arquivo de variáveis de ambiente do app

- [Variáveis](vars/main.yml)
- [Variáveis default](defaults/main.yml)
- Variáveis de ambiente do [pg-promise](templates/env.j2)

Dependencies
------------

   [dependencies](meta/main.yml)
 - role: [geerlingguy.nodejs](https://galaxy.ansible.com/geerlingguy/nodejs)
 - nodejs_version: 17.x
 - nodejs_install_npm_user: root


Example Playbook
----------------
```yml
---
- hosts: pg_promise
  become: true
  roles:
    - role: git_pg_promise
```
Molecule Tests
--------------

O Molecule nesta role está com systemd como inicializador
para rodar o app como uma unit service, MOLECULE_DISTRO é a
variável para setar uma sistema que será rodado.

```bash
MOLECULE_DISTRO=debian10 molecule create            # para criar a instância do molecule com docker
molecule list                                       # para mostrar as instâncias 
molecule converge                                   # para testar a role
molecule login                                      # para entrar num shell dentro do container
molecule destroy                                    # para terminar a instância

MOLECULEE_DISTRO=ubuntu2004 molecule test           # para fazer o processo completo!

```

License
-------

BSD

Author Information
------------------

...
