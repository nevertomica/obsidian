MongoDB 認證的機制

In MongoDB, the Authentication Database is the database that stores user information such as usernames, passwords, and roles, and is used to authenticate users and grant access to other databases in the MongoDB instance.

When a user logs in to a MongoDB instance, the Authentication Database checks the user's credentials, and if they are correct, grants access to the MongoDB instance. The user can then perform CRUD (create, read, update, delete) operations on the databases they are authorized to access.

The default Authentication Database in MongoDB is called "admin," but users can configure MongoDB to use a different database for authentication if needed. MongoDB also supports different authentication mechanisms, including LDAP, Kerberos, and x.509 certificates, to provide users with more secure authentication options.

https://stackoverflow.com/questions/54011332/authenticationfailed-to-mongodb-with-spring-boot