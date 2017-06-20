PostgreSQL Server
=================
Ansible Role para instalar servidor PostgreSQL 9.6 e cadastrar usuários e bancos de dados.

Usuários devem ser cadastrados no playbook que executa este role. Este role não remove usuários ou os bancos de dados, apenas inclui.

Os hosts com permissão de acesso devem ser incluidos no arquivo pg_hba.conf.

Requisitos
----------
CentOS 7

Variaveis do Role
-----------------
Na variavel _postgresql_server_pg_hba_file_ deve ser informado o caminho onde se encontra o arquivo pg_hba.conf.
```yaml
postgresql_server_pg_hba_file: ../templates/postgresql/pg_hba.conf
```

O bloco de variavel _user_ contem as variaveis necessarias para criação dos usuários:

Nome do usuário:
```yaml
username: joe
```

Senha do usuário:
```yaml
password: joeVeryLongPassphase
```

Banco de dados:
```yaml
database: joe
```

Dependências
------------

Nenhuma.

Playbook de exemplo
-------------------
```yaml
---
- name: Instala postgresql Server
  hosts: all
  become: true
  gather_facts: true
          
  roles:
    - role: postgresql_server
      postgresql_server_pg_hba_file: ../templates/postgresql/pg_hba.conf
      users:
        - username: alice
          password: aliceLongPassword
          database: alice
  
        - username: neo
          password: neoEvenLongerPassword
          database: neo
```

Licença
-------

MIT

Informações do Autor
--------------------

Fabricio Boreli Ferreira  
fabricioboreli@openmailbox.org
