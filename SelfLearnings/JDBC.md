What Is JDBC and JDBC

# Drivers
JDBC (Java Database Connectivity) is a Java API for connecting and
with databases. JDBC drivers are software components that
provide the necessary functionality to connect Java applications to
different types of databases.
There are four types of JDBC drivers:
1. Type 1: JDBC-ODBC Bridge Driver -->NATIVE C DRIVER,OLDEST,DEPRECATED
2. Type 2: Native-API Partly Java Driver-->vendor specific driver like mysql driver,oracle driver, maria driver
3. 3: Network Protocol pure Java Driver--->connection using middleware
4. 4: Thin Driver (also known as the Direct to Database Pure
Java Driver)---->latest driver,directly connects native api calls to database calls,lightweight,efficient
Each type Of driver has its own advantages and is suitable for different
scenarios.


# JDBC Components
In addition to the JDBC drivers, there are several other components that
make up the JDBC API, including:
Class
• Connection interface
Statement and PreparedStatement interfaces
• ResultSet interface
These components work together to provide a powerful and flexible API
for working with databases in Java.


# Program Flow

![[Pasted image 20260212125809.png]]