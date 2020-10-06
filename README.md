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

Vous êtes maintenant connectés à la base de donnée `dvdrental`

Vous pouvez récupérer un modele visuel de cette base de donnée sur: https://www.postgresqltutorial.com/postgresql-sample-database/
C'est très utile si vous voulez comprendre que représente cette base de données.

## 1  

la commande `\dt` vous donne la liste des tables.  
la commande `\dt+ NOM_DE_LA_TABLE` vous donne le nom des colonnes de d'une table.  
la commande `\d   NOM_DE_LA_TABLE` vous affiche le nom des colonnes ainsi que les types associés à chaque colonnes.  


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
=> \dt+ actor
                   List of relations
 Schema | Name  | Type  |  Owner  | Size  | Description
--------+-------+-------+---------+-------+-------------
 public | actor | table | db_user | 40 kB |
(1 row)
```
```sql
=> \d actor
                                            Table "public.actor"
   Column    |            Type             | Collation | Nullable |                 Default
-------------+-----------------------------+-----------+----------+-----------------------------------------
 actor_id    | integer                     |           | not null | nextval('actor_actor_id_seq'::regclass)
 first_name  | character varying(45)       |           | not null |
 last_name   | character varying(45)       |           | not null |
 last_update | timestamp without time zone |           | not null | now()
Indexes:
    "actor_pkey" PRIMARY KEY, btree (actor_id)
    "idx_actor_last_name" btree (last_name)
Referenced by:
    TABLE "film_actor" CONSTRAINT "film_actor_actor_id_fkey" FOREIGN KEY (actor_id) REFERENCES actor(actor_id) ON UPDATE CASCADE ON DELETE RESTRICT
Triggers:
    last_updated BEFORE UPDATE ON actor FOR EACH ROW EXECUTE FUNCTION last_updated()
```

## 2  

Ecrivez une requête SQL qui affiche tous les titres et descriptions des films dont la description contient le mot `Amazing`.  
