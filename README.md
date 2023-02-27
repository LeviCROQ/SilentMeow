# Pets Database
Develop SQL statements required to manipulate a database of pets<br>

[data types](https://www.w3schools.com/sql/sql_datatypes.asp),
[hsqldb](http://hsqldb.org/),
[sql](https://www.w3schools.com/sql/),
[uuid](https://www.uuidgenerator.net/)

## Pre-requirements
* Ensure the Eclipse IDE has Maven by looking for M2E from Help About ([details](https://www.vogella.com/tutorials/EclipseMaven/article.html))
* Install `DBViewer Plugin 1.2.2.v20101009` by ZIGEN from the Eclipse IDE marketplace
* Import into Eclipse as Git with smart import (accepting all defaults in wizard)
* Let the IDE finish building dependencies before proceeding (see bottom right of Eclipse)

## Steps
* Run the PetsDB app to start the database
* Develop Pets-based SQL statements
* Switch to DBViewer perspective to test
* Stop the PetsDB app to shutdown database
* Ensure SQL documented within this README
* Push update README back to forked GitHub

## Bonus
* Create another related table with SQL

## Database Schema

**Animal table**
 - Hunger INT
 - Id CHAR(36)
 - Name VARCHAR(100)
 - OwnerId CHAR(36)
 - Species CHAR(1)

**Owner table**
 - Id CHAR(36)
 - Name VARCHAR(100)
 - Town VARCHAR(100)
 
**To create the Owner table**<br>
CREATE TABLE Owner (Id CHAR(36), Name VARCHAR(100), Town VARCHAR(100), PRIMARY KEY(Id))

**To create the Animal table**<br>
CREATE TABLE Animal (Hunger INT, Id CHAR(36), Name VARCHAR(100), OwnerId CHAR(36), Species CHAR(1), PRIMARY KEY (Id), FOREIGN KEY (OwnerId) REFERENCES Owner(Id))

**To insert a new Owner row**<br>
INSERT INTO Owner (Id, Name, Town) VALUES ('c75121fe-9aaf-4d0b-a03c-f9df4f13dbe5', 'Keith', 'Lower Swell')

**To insert a new Cat row**<br>
INSERT INTO Animal (Hunger, Id, Name, OwnerId, Species) VALUES (10, 'df93fddc-6cec-4f76-8600-fcca83af5faa', 'Derek', 'c75121fe-9aaf-4d0b-a03c-f9df4f13dbe5', 'C')

**To insert a new Dog row**<br>
INSERT INTO Animal (Hunger, Id, Name, OwnerId, Species) VALUES (5, 'c1c78910-06fc-4fe2-a5ac-62abff797ac6', 'Smurfette', 'c75121fe-9aaf-4d0b-a03c-f9df4f13dbe5', 'D')

**To query an animal**<br>
SELECT Animal.Name FROM Animal animal WHERE animal.ID = 'df93fddc-6cec-4f76-8600-fcca83af5faa'

**To query all pets for an owner**<br>
SELECT animal.Name FROM Animal animal, Owner owner WHERE owner.Name = 'Keith' AND animal.ownerId = owner.Id
