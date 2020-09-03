# DAT250: Software Technology Experiment Assignment 2
[Link to assignment description](https://github.com/selabhvl/dat250public/blob/master/expassignments/expass2.md)

### Installation of the Derby Software

Following the tutorial was nice. I encountered however some technical difficulties along the way. Most of them to do with versions of Derby not matching up with versions of Java. I fixed these by downloading a slightly older version of Derby. But I later understood that the problem was that my Java JDK version did not match up with my JRE version.  

### Experiment 1: Application using JPA

I first followed [the JPA tutorial in the Assignment description](https://www.vogella.com/tutorials/JavaPersistenceAPI/article.html#installation), but after encountering several different errors in my own java project, i copied the Maven project in the description. No errors there. 

To inspect the variables i used the `ij` interactive scripting tool that comes with Derby. 

1. To start up `ij` in powershell: ```java org.apache.derby.tools.ij```

2. Connected to the database (that i called simpleDb): `connect 'jdbc:derby:simpleDb';`

3. To inspect the data that was created: `select * from test.TODO;`. See image below

![Inspecting data](/images/inspectTable.png)
