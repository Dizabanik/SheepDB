# Sheep DB - Fast C Database
Sheep DB is a fast database written in C language. It provides an easy-to-use API to interact with databases and manage data. This database is designed to be lightweight, fast and flexible, making it an ideal solution for applications that need to handle large amounts of data efficiently.

## Features
- Lightweight: Sheep DB has a small footprint and does not require any additional dependencies.
- Fast: The database is optimized for performance, making it suitable for use in high-performance applications.
- Flexible: Sheep DB supports both key-value pairs and arrays, allowing you to store and manage your data in a variety of ways.
- Easy to use: The API is designed to be simple and intuitive, making it easy to get started with Sheep DB.

## Getting Started
This section provides a tutorial on how to use Sheep DB in your own projects.

### Creating a database object
You can create a database object in two ways, either by using a direct reference or by using a pointer. Here's an example of each:

```c
//creating simple database object
shdb db;
shdb_create(&db);

//creating database object using pointer
shdb* dbp;
shdb_createp(db);
```
### Loading a file into a database object
You can load a file into a database object using the `shdb_load` function. Here's an example:

```c
//load a file to a database object
shdb_load(&db, "base.sdb");

//load another file to a database pointer object
shdb_load(dbp, "base2.sdb");
```
### Getting values from the database
You can retrieve values from the database using the `shdb_getValue` function. Here's an example:

```c
//get value from database by a key
char *value1 = shdb_getValue(&db, "key");

//get an array by key from database
shdb* db2 = shdb_getKeyArray(&db, "key2");

//get values from array by key
char *value = shdb_getValue(db2, "arrKey1");
char *value2 = shdb_getValue(db2, "arrKey2");
```
### Closing a database object
When you're finished with a database object, you should close it to release the memory it's using. You can do this using the `shdb_close` function for direct references and shdb_destroyp for pointers. Here's an example:

```c
//close database object
shdb_close(&db);

//close pointer database object
shdb_destroyp(dbp);
```
### Using comments in the database
You can use comments in the .sdb file to add notes and explanations. Comments start with a `//` and continue until the end of the line. For example:

```c
// this is a comment
```
### Using `"` characters in the database
You can use " characters in values to denote values that won't be tokenized, such as links. For example:


```c
link = "https://example.com"
```

### Using arrays in the database
You can use arrays in Sheep DB to store multiple values under a single key. Arrays can either be simple lists of values or lists of key-value pairs. Here's an example of a simple array:

```c
array = [1, 2, 3]
```
And here's an example of an array with key-value pairs:

```c
array = [version: 0.0.1, link: "https://example.com"]
```
