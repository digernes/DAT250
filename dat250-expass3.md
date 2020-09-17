# DAT250: Software Technology Experiment 3 
[Link to assignment description](https://github.com/selabhvl/dat250public/blob/master/expassignments/expass3.md)

## Installation: MongoDB Database

During installation of MongoDB I encoutered some small errors to do with the validation. After adding my correct local paths to the script, and getting the public signature files for the correct version, it worked. 

Below is a picture of the successfull validation. (of MongoDB version 4.4.1)
![](/images/mongodb_validation.png)

## Experiment 1: MongoDB CRUD operations

Next task was learning about the different CRUD operations in MongoDB. The tutorial was pretty straightforward and easy to follow. I include a screenshot for each of the different steps. 

### Insert documents

![](/images/mongodb_insert.png)

Usage of both insertOne() and insertMany().

### Query documents

![](/images/mongodb_query.png)

The simplest usage of find(). 

### Update documents

![](/images/mongodb_update.png)

Example usage of updateOne().

### Remove documents

![](/images/mongodb_delete.png)

Example usage of deleteMany()

## Experiment 2: Aggregation

### Map-Reduce Examples 

Next I was reading about aggregation and map-reduce. I followed the map-reduce examples and ran them in the terminal. Below is a screenshot from the first example. 

![](/images/mongodb_mapreduce_example1.png)

### Custom Map-Reduce Operation

The last task was to develop an own operation and execute it. I decided to sort the data by the different days. This could show what days had the most orders, total income per day and how many unique customers made orders a specific day. Maybe there could be some good insight by sorting the data like this. 

Firstly i made the mapFunction. The key value was the date of the order. (``ord_date``)  
The value was an object which included the price (``price``) and customer id (``cust_id``) associated with the order. 
```
var mapFunction3 = function() {
	var key = this.ord_date;
  	var value = {income: this.price, customer: this.cust_id}; 
   	emit(key, value);
};
```

Next, the reduce function counted unique customers (``unique_customers``) per date, as well as adding the prices together to find the total income (``income``) and counting how many orders were made. 

```
var reduceFunction3 = function(keyDate, objs) {
   reducedVal = { income: 0, orders: 0, unique_customers: 0};
   customer_list = []

   for (var i = 0; i < objs.length; i++) {
       if(!customer_list.includes(objs[i].customer)) {
           customer_list.push(objs[i].customer);
           reducedVal.unique_customers += 1;
       }
       reducedVal.orders++;
       reducedVal.customer_list = customer_list;
       reducedVal.income += objs[i].income;
   }

   return reducedVal;
};
```

To run in the terminal, first set up the mapReduce operation: 

```
db.orders.mapReduce(
    mapFunction3,
    reduceFunction3,
    { out: "map_reduce_example3" }
 )
 ```
 
 and then to see the result, enter: ``db.map_reduce_example3.find().sort({_id: 1})`` (ordered by date).
 
 Below is a screenshot of setting up the functions and operation in PowerShell. 
 
 ![](/images/mongodb_mapreduce_example_custom.png)
 
 
 
 As far as I'm aware, there are no pending issues with the whole assignment which I did not manage to solve.
