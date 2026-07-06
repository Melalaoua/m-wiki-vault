tags:: #thelaboratory/howto, #thelaboratory/coding 
source:: [1](https://www.digitalocean.com/community/tutorials/how-to-install-postgresql-on-ubuntu-20-04-quickstart)



PostgreSQL fonctionne comme linux, plus ou moins, avec un système d'utilisateurs qui vont se connecter à la base de donnée portant le même nom que l'utilisateur. Pour le serveur, l'utilisateur créer se nomme **whitewave**.

**Pour se connecter à la db.**
- ``sudo -u whitewave psql`

**Pour quitter postgresql**
- ```\q ou exit```

**Data Types**
https://tableplus.com/blog/2018/06/postgresql-data-types.html


Execute postgresql file : 
```psql -U username -d myDataBase -a -f myInsertFile```

postgresql create schema : 
```
CREATE SCHEMA schema_name
```

add schema to search path 
``` SET search_path TO moodyblues,public;```