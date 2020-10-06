# Exercices database partie 2


Télécharger la base de donnée: https://sp.postgresqltutorial.com/wp-content/uploads/2019/05/dvdrental.zip
Dézipper le fichier dvdrental.zip et installer la base de donnée dvdrental.tar avec les commandes suivantes:   

```sql
% psql -d postgres -U db_user
postgres=> CREATE DATABASE dvdrental;
postgres=> \quit
% pg_restore -U db_user -d dvdrental ./dvdrental.tar
% psql -d dvbrental -U db_user
```

Vous êtes maintenant connectés à la base de donnée dvdrental

Vous pouvez récupérer un modele visuel de cette base de donnée sur: https://www.postgresqltutorial.com/postgresql-sample-database/
C'est très utile si vous voulez comprendre que représente cette base de données.

## 1  

la commande \dt+ NOM_DE_LA_TABLE vous donne la liste des tables.  
la commande \dt+ NOM_DE_LA_TABLE vous donne le nom des colonnes de d'une table. la commande \d   NOM_DE_LA_TABLE vous affiche le nom des colonnes ainsi que les types associés à chaque colonnes.  


```sql
=> \dt
            List of relations
 Schema |     Name      | Type  |  Owner
--------+---------------+-------+---------
 public | actor         | table | db_user
 public | address       | table | db_user
 public | category      | table | db_user
 public | city          | table | db_user
 public | country       | table | db_user
 public | customer      | table | db_user
 public | film          | table | db_user
 public | film_actor    | table | db_user
 public | film_category | table | db_user
 public | inventory     | table | db_user
 public | language      | table | db_user
 public | payment       | table | db_user
 public | rental        | table | db_user
 public | staff         | table | db_user
 public | store         | table | db_user
(15 rows)
```
```sql
=> \dt+actor
                          List of relations
 Schema |     Name      | Type  |  Owner  |    Size    | Description
--------+---------------+-------+---------+------------+-------------
 public | actor         | table | db_user | 40 kB      |
 public | address       | table | db_user | 88 kB      |
 public | category      | table | db_user | 8192 bytes |
 public | city          | table | db_user | 64 kB      |
 public | country       | table | db_user | 8192 bytes |
 public | customer      | table | db_user | 96 kB      |
 public | film          | table | db_user | 464 kB     |
 public | film_actor    | table | db_user | 264 kB     |
 public | film_category | table | db_user | 72 kB      |
 public | inventory     | table | db_user | 224 kB     |
 public | language      | table | db_user | 8192 bytes |
 public | payment       | table | db_user | 888 kB     |
 public | rental        | table | db_user | 1224 kB    |
 public | staff         | table | db_user | 16 kB      |
 public | store         | table | db_user | 8192 bytes |
(15 rows)
```
