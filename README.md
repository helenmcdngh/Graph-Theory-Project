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

# Database Design and Structure
I had planned creating a timetable for the whole year of third year, I found that it was very hard to read due to the number of nodes and relationships I opted for the second semester only. It seemed to be better choice for building this graph database. The structure has a year containing three groups called group A, B and C, the course has six modules Graph Theory, Software Testing, Server Side Rad, Database Management, Professional Practice in IT and Mobile applications development 2 and they are all taught by lectures in a room teaching a lab or lecture at a certain time of the day.
With the above idea for a structure, I extracted the data that I need from the GMIT website and the timetabling website. I organised all the data into a document and sorted them into a list. After some trial and error with creating nodes, labels, relationships and properties, I began to create all the nodes I needed. I ended up with 79 nodes once I finished, then I created relationships between them, only connecting them to the most relevant nodes and labelled them. I recorded all my queries in a text file just encase I destroyed the database, which I did numerous times. This text file is called commands for neo4j.txt and it is attached to my GitHub repository.
My Prototype contains the following nodes and relationships connecting all of the nodes together. I created a svg file with neo4j that has a clear image of my graph and it is attached to my GitHub repository.

#### Modules, Course and Lecturers
```sh
create (s:SoftwareDev {name:'Software Development'}) return s

create (m1:Module {name:'Software Testing'}),(m2:Module {name:'Database Management'}),(m3:Module{name: 'Graph Theory'}),(m4:Module {name:'Server Side Rad'}),(m5:Module {name: 'Mobile Application Development 2'}),(m6:Module {name: 'Professional Practice in IT'}) return m1,m2,m3,m4,m5,m6

Match(s:SoftwareDev {name:'Software Development'}), (m1:Module {name:'Software Testing'}) create (s)-[r:Module_of]->(m1)

create (lect1:Lecturer {name: 'Ian McLoughlin'}),(lect2:Lecturer {name: 'Martin Hynes'}),(lect3:Lecturer {name: 'Deirdre O Donovan'}),(lect4:Lecturer {name: 'Gerard Harrison'}),(lect5:Lecturer {name: 'Damien Costello'}) return lect1,lect2,lect3,lect4,lect5

Match(lect2:Lecturer {name: 'Martin Hynes'}), (m1:Module {name:'Software Testing'}) create (lect2)-[r:Teaches]->(m1)
```
![database2](https://cloud.githubusercontent.com/assets/15608152/25253737/181cb8da-261a-11e7-9f3d-6ca7c3800440.png)

#### Year and Groups
```sh
create(y:Year {name:'Year 3'}),(gA:Group {name:'Group A'}),(gB:Group {name:'Group B'}), (gC:Group {name:'Group C'})

match(gA:Group {name:'Group A'}),(y:Year {name:'Year 3'}) create (y)-[r:YEAR_OF]->(gA)
```
![database3](https://cloud.githubusercontent.com/assets/15608152/25253739/182c6500-261a-11e7-9c39-fecf15840c45.png)

#### Rooms
```sh
create(Rm1:Room {name:'994'}),(Rm2:Room {name:'223'}), (Rm3:Room {name:'PF05'}),(Rm4:Room {name:'481'}),(Rm5:Room {name:'436'}),(Rm6:Room {name:'482'}),(Rm7:Room {name:'470'}),(Rm8:Room {name:'379'}),(Rm9:Room {name:'162'}),(Rm10:Room {name:'938'}),(Rm11:Room {name:'208'}),(Rm12:Room {name:'997'}),(Rm13:Room {name:'939'}),(Rm14:Room {name:'995'}),(Rm15:Room {name:'PF18'})
```
![database4](https://cloud.githubusercontent.com/assets/15608152/25253738/182a9572-261a-11e7-808f-2ca7075fb247.png)

#### Days, Individual hours, classes
```sh
Create(Mon:Day {name:'Monday'}),(Tues:Day {name:'Tuesday'}),(Wed:Day {name:'Wednesday'}),(Thurs:Day {name:'Thursday'}),(Fri:Day {name:'Friday'})

create(Monh1:MonHrs{name:'10am'}),(Monh2:MonHrs{name:'12pm'}),(Monh3:MonHrs{name:'2pm'}),(Monh4:MonHrs{name:'4pm'})

match(Mon:Day {name:'Monday'}),(Monh1:MonHrs {name:'10am'}) create (Mon)-[r:time]->(Monh1)

create(DLec:Class {name:'DBMS Lecture'})
match(DLec:Class {name:'DBMS Lecture'}),(Monh1:MonHrs {name:'10am'}) create (DLec)-[r:begins_at]->(Monh1)
match(m2:Module {name:'Database Management'}),(DLec:Class {name:'DBMS Lecture'}) create (m2)-[r:taught]->(DLec)
match(Rm1:Room {name:'994'}),(DLec:Class {name:'DBMS Lecture'}) create (Rm1)-[r:room]->(DLec)
match(y:Year {name:'Year 3'}),(DLec:Class {name:'DBMS Lecture'}) create (y)-[r:students_attending]->(DLec)
```
![database5](https://cloud.githubusercontent.com/assets/15608152/25253740/18326e8c-261a-11e7-957d-5a3d685c8eb7.png)
![database](https://cloud.githubusercontent.com/assets/15608152/25253736/17fe2104-261a-11e7-9f98-be6ce315aed7.png)



# References
1. https://neo4j.com/developer/get-started/
2. https://neo4j.com/developer/cypher/
3. https://www.tutorialspoint.com/neo4j/index.htm
4. http://dillinger.io/
