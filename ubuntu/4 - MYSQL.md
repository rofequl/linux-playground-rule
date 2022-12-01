## MySQL Tutorial
- Connecting to and Disconnecting from the Server
    ```bash
    $ mysql -h host -u user -p
    $ mysql
    mysql> QUIT
    ```
- Find out what databases currently exist on the server: ``SHOW DATABASES;``
- If the test database exists, try to access it: ``USE test``
- Create database ``CREATE DATABASE databasename;``
- DROP DATABASE ``DROP DATABASE databasename;``
- Creates a table called "Persons" :
  ```sql
    CREATE TABLE Persons (
        PersonID int,
        LastName varchar(255),
        FirstName varchar(255),
        Address varchar(255),
        City varchar(255)
    );
    ```
- SHOW TABLES should produce some output: ``SHOW TABLES;``
- Describe a database table: ``DESCRIBE pet;``
- DROP TABLE: ``DROP TABLE table_name;``
- You could add a new record using an INSERT statement like this:
  ```sql
    INSERT INTO pet VALUES ('Puffball','Diane','hamster','f','1999-03-30',NULL);
    ```
- 