# Exercices database partie 2


## 1  

Télécharger la base de donnée: https://sp.postgresqltutorial.com/wp-content/uploads/2019/05/dvdrental.zip
Dézipper le fichier dvdrental.zip et installer la base de donnée dvdrental.tar avec les commandes suivantes:   

`% psql -d postgres -U db_user`
```sql
CREATE DATABASE dvdrental;
\quit
```
```
% pg_restore -U db_user -d dvdrental ./dvdrental.tar
% psql -d dvbrental -U db_user
```

Vous êtes maintenant connectés à la base de donnée `dvdrental`

Vous pouvez récupérer un modele visuel de cette base de donnée sur: https://www.postgresqltutorial.com/postgresql-sample-database/
C'est très utile si vous voulez comprendre que représente cette base de données.

La commande `\dt` vous donne la liste des tables.  
La commande `\dt+ NOM_DE_LA_TABLE` vous donne le nom des colonnes de d'une table.  
La commande `\d   NOM_DE_LA_TABLE` vous affiche le nom des colonnes ainsi que les types associés à chaque colonnes.  


## 2  

Ecrivez une requête SQL qui affiche tous les titres et descriptions des films dont la description contient le mot `Amazing`.  

```sql
SELECT
title,
description
FROM film
WHERE description
LIKE '%Amazing%';
```


## 3  

Ecrivez une requête SQL qui récupère tous les paiements supérieurs à 10. Il faudra récupérer l'id, le prénom, le nom du client ainsi que le montant et la date du paiement.

`customer_id | first_name |  last_name   | amount |        payment_date`

```sql
SELECT
customer.customer_id,
customer.first_name,
customer.last_name,
payment.amount,
payment.payment_date
FROM customer
JOIN payment
ON customer.customer_id = payment.customer_id
WHERE amount > 10;
```


## 4   

Ecrivez une requête SQL qui affiche le chiffre d'affaire gagné par le video club depuis son ouverture.  

```sql
SELECT
SUM(amount)
FROM payment;
```


## 5  

Ecrivez une requête SQL qui affiche le titre de tous les films dont la langue est l'anglais et dont la durée est supérieure à 120 minutes.  

