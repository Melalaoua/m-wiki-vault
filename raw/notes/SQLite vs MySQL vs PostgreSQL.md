### A comparison of Relational Database Management Systems.
tags:: #thelaboratory/coding
source:: [1](https://www.digitalocean.com/community/tutorials/sqlite-vs-mysql-vs-postgresql-a-comparison-of-relational-database-management-systems)
relation::[[PostgreSQL]]


Il existe trois modèles de gestion de bases de données : [[Relational Databases|Les bases de données relationnelles]], [[NoSQL|le NoSQL ]], et [[NewSQL|le NewSQL]]

Sur cette page on va se focus que sur des RDBMs (relational databases models) : SQLite, MySQL et PostgreSQL. Plus précisement leurs avantages, désavantages et les situations dans lesquels ils sont les plus optimisés chacuns.

### Quelques précisions sur les DBMS.
Un DBMs est un ordinateur qui intéragit avec une base données. Il ne faut pas cofondre. Les DBMs vont permettre d'accéder à ces bases de données pour écrire, modifier, lire, ... 

![[Pasted image 20230210180223.png]]


### Data Types and Constraints.
Chaque colonne dans une base de données est associé à un type de données qui va dicter ce qui est autorisé en entrée ou non. Parfois c'est interchangable, parfois non. On retrouve communément les dates, strings, chiffres, booleans.

Stocker des chiffres est plus nuancés que des string car ils peuvent avoir un signe (signed) ou non (unsigned).

Etre en capacité de contrôler ce qui rentre dans la base de données est important. Un administrateur est en capacité d'imposer une contrainte sur une table pour limiter ce qui rentre dedans. Voici les contraintes :
-   `UNIQUE`: Applying this constraint to a column ensures that no two entries in that column are identical.
-   `NOT NULL`: This constraint ensures that a column doesn’t have any `NULL` entries.
-   `PRIMARY KEY`: A combination of `UNIQUE` and `NOT NULL`, the `PRIMARY KEY` constraint ensures that no entry in the column is `NULL` and that every entry is distinct.
-   `FOREIGN KEY`: A `FOREIGN KEY` is a column in one table that refers to the `PRIMARY KEY` of another table. This constraint is used to link two tables together. Entries to the `FOREIGN KEY` column must already exist in the parent `PRIMARY KEY` column for the write process to succeed.
-   `CHECK`: This constraint limits the range of values that can be entered into a column. For example, if your application is intended only for residents of Alaska, you could add a `CHECK` constraint on a ZIP code column to only allow entries between 99501 and 99950.
  

> [!INFO]
> Pour voir les comparaisons entre Sqlite, Postgresql et mysql, voir le lien en source.

