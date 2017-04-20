# Graph Theory Project
> Author: Helen McDonagh      3rd year Project

# Project Requirements
You are required to design and prototype a Neo4j database for use in a timetabling system for a third level institute like GMIT to be delivered on the 23rd of April 2017. The database should store information about student groups, classrooms, lecturers, and work hours – just like the currently used timetabling system at GMIT. 

# Neo4j
First, neo4j is one of the best graph database management systems in the software market. It is written in Java and has an easy syntax to learn also it was developed by Neo Technology. Co-founders Emil, Johan, Peter started building the first Neo4j prototype back in 2000 later finished developed the first ever version of Neo4j in 2002. Walmart, Cisco, Swiss, LinkedIn, HP, AWOL and up to 500 more companies use neo4j’s graph database management systems. Neo4j graph database has 5 main building blocks and they are the following:

| Features | Description  | 
| ------------- |:-------------:| 
| Nodes | a node is an essential unit of a graph; it also contains properties with key-value pairs. For example, a Node name = ”Customer” and it contains a set of properties like customer Number, customer Name, spends |
| Properties | a property is a key-value pair to describe a graph nodes and relationship. For example, “BOB” = Value where BOB is a String |
| Relationships | are one of the major building blocks of graph database. Relationships connects two or more nodes together; they can also contain properties as key-value pairs |
| Labels | a label associates a common name to set of nodes or relationships, they can also contain one or more labels, create and remove labels for existing ones |
| Data Browser | When you have, everything installed, you can access NEO4j Data Browser by using this URL http://localhost:7474/browser/ . When opened, you can execute your CQL commands |

Neo4j has its own CQL commands and clauses, here are some of the frequently used:

| Command        | Use           | 
| ------------- |:-------------:| 
| Create |To create nodes, relationships and properties  | 
| Match | To retrieve data about nodes, relationships and properties | 
| Return | To return query results | 
| Where | To provide conditions to filter retrieval data | 
| Delete | To delete nodes and relationships | 
| Remove | To delete properties of nodes and relationships | 
| Order By | To sort retrieval data |
| Set | To add or update labels | 		

Neo4j CQL functions, here are some of the most frequently ones used:

| Functions        | Use          | 
| ------------- |:-------------:| 
| Strings      | These are used to manipulate strings or create a string representation of another value. For example, left(), replace(), reverse(), right(), split() | 
| Aggregation      | These take multiple values as arguments, and calculate and return an aggregated value from them. Avg() collect(), count(), max(), min() and sum() are some examples | 
| Mathematical | These all operate on numerical expressions only and will return an error if used on any other values. Examples of mathematical functions: abs(), ceil(), floor(), rand(), round() sign() | 

# Installing Neo4j
Firstly you must go to [Node.js](http://www.neo4j.org/download) and download the "For Individuals Download Community Edition", then go to your downloads folder and click on the executable file and run it. 
Follow the instructions throught the installation program, once it has installed click on the Desktop shortcut to run it.
Then you start the server and it will tell you when its ready. http://localhost:7474/browser/ 

# Database Design
I have decided to create a graph timetabling system for the 2nd semster my 3rd year course, Software Development in GMIT. I created individual nodes for all the following:
+ Modules
+ Lecturers
+ Year
+ Groups 
+ Classes
+ Days and individual hours for each day
+ Course
+ Rooms

# References
1. https://neo4j.com/developer/get-started/
2. https://neo4j.com/developer/cypher/
3. https://www.tutorialspoint.com/neo4j/index.htm
