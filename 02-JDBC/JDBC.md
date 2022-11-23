JDBC:

Persistence - Store the data beyond application process
	In OOP - Persistence means store data beyond application process(beyond JVM)
	
	JDBC - Java Database Connectivity helps us to write java applications to connect and interact with relational databases using JDBC API

	JDBC API is industry standard API which provides programmatic access to various relational databases from java application

	JDBC API comprises of two packages.

	java.sql  - Basic functionalities like register the driver, establishing the connection to a database for accessing and processing the data stored in the database 

javax.sql - package serves for server side accessing of data and processing the data stored in the database/s

JDBC Driver Manager -

	To Connect java app to DB, drivers are needed 
	In order to connect to a specific database, specific databases driver is needed 
Driver Manager responsible for loading and registering the driver in order to connect to specific database

	                                                  (com.mysql.jdbc.driver)
	Java app --->DriverManager---------------------> MySql DB
(JDBC)

					        (org.postgresql.Driver)
	Java app --->DriverManager---------------------> Postgres DB
(JDBC)


	Similarly there are different drivers we can use to connect to that specific database.


Connect to Database

To connect to a database, following step are defined and followed :
1.Loading and registering the JDBC driver
2.Create the connection using database
3.URL Create statement  
4.Fire the statement
5.Close the connection

JDBC Steps -
1.Import the Package -> (java.sql.*)

2.Load and Register the driver -> load - download connector for database, Register - Class.forName(" ") //from jdbc 4.0 this line is no more needed

3.establish the connection -> Instantiate 'Connection' Interface.
code:
Connection conn = DriverManager.getConnection(url, username, password)

4.create the statement interface -> Statement, PreparedStatement, CallableStatement
code: Statement st = conn.createStatement();

5.execute the query
ResultSet rs = st.executeQuery("write sql query here")
Note: ResultSet is interface which can hold the table with data from database

6.process result
rs.next()
Note: Initially the pointer will be above the table, rs.next() will Move the pointer to the first row and so on.. till the end of the table.

while(rs.next())
rs.getInt(1) + rs.getString(2);

Note: 1 and 2 inside the method is column number

7.close
st.close()
conn.close() //closing the connection finally
