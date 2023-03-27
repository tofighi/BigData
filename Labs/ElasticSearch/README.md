Run the following in Kibana Dev Tools&nbsp;


Indexing Syntax


PUT /index/type/id
{
"field1": "value1"
"field2": "value2"
........
}


Examples&nbsp;


PUT /vehicles/car/333
{
"make": "Honda",
"Color": "Black",
"HP": 250,
"milage": 2400,
"price": 19300.97
}


1. What is the output? What does it mean?


GET /vehicles


2. What is the output? What does it mean?


GET /vehicles/car/333


3. What is the output? What does it mean?


4. What happens if you run GET /vehicles/car/333 again?


5. #what is the impact of the _source endpoint?&nbsp;
GET /vehicles/car/333/_source&nbsp;


6. What does the HEAD method/verb/command do?
HEAD&nbsp; /vehicles/car/333


7. What is the result of running


HEAD&nbsp; /vehicles/car/222


PUT /vehicles/car/333
{
"make": "Honda",
"Color": "Black",
"HP": 250,
"milage": 1200,
"price": 19300.97
}


8. Can you change a specific field within a document independently?&nbsp;


9. Explain the concept of data immutability in big data


The Big Data immutability is based on similar principles to the immutability in programming data structures. The goal is the same - do not change the data in-place and instead create a new one. The data can't be altered and deleted. This rule can be defined for the eternity or only for a specific amount of time.

Thus the immutability prohibits the&nbsp;in-place changes&nbsp;that are represented by random access. Instead of overriding already existent data we can only add a new one. This new data through one of its attributes can help to distinguish between old and the most recent version (e.g. data creation timestamp attribute). A great example of immutable data store is&nbsp;Apache Kafka&nbsp;- an append-only distributed log system.

(source: https://www.waitingforcode.com/general-big-data/immutability-big-data/read)


10. what does the update API do?


POST /vehicles/car/333/_update&nbsp;
{
"doc": {
"driver": "Ryan"
}
}




11. What is the output? What does it mean this time?
GET /vehicles/car/333




12. What is the output? What does it mean?
DELETE /vehicles/car/333


13. Briefly explain the concept of DELETE in ES




14. What is the output? What does it mean?


DELETE /vehicles/car


15. Can you delete a document_type which has no document (id)?


DELETE /vehicles
16. Can you delete an index that has no document?


GET /vehicles
17. What is the output? What does it mean?


=================================================================
&nbsp;Part 1 - Questions
=================================================================


Index the below documents into Elasticsearch using the PUT command and answer the following questions.
1. Display all the documents in the courses index
2. Run a query that shows a match for all documents in the courses index
3. Run a query that only matches room C12 in the courses index
4. Display only the total number of documents without ES meta fields in the courses index
5. What is the benefit of using unique identifiers while indexing? (research it)
6. What was the main challenge in this kind of indexing? (research it)




PUT /courses/classroom/1
{
&nbsp; &nbsp; "name": "Accounting 101",
&nbsp; &nbsp; "room": "E3",
&nbsp; &nbsp; "professor": {
&nbsp; &nbsp; &nbsp; &nbsp; "name": "Thomas Baszo",
&nbsp; &nbsp; &nbsp; &nbsp; "department": "finance",
&nbsp; &nbsp; &nbsp; &nbsp; "facutly_type": "part-time",
&nbsp; &nbsp; &nbsp; &nbsp; "email": "baszot@onuni.com"
&nbsp; &nbsp; &nbsp; &nbsp; },
&nbsp; &nbsp; "students_enrolled": 27,
&nbsp; &nbsp; "course_publish_date": "2015-01-19",
&nbsp; &nbsp; "course_description": "Act 101 is a course from the business school on the introduction to accounting that teaches students how to read and compose basic financial statements"
}


PUT /courses/classroom/2
{
&nbsp; &nbsp; "name": "Marketing 101",
&nbsp; &nbsp; "room": "E4",
&nbsp; &nbsp; "professor": {
&nbsp; &nbsp; &nbsp; &nbsp; "name": "William Smith",
&nbsp; &nbsp; &nbsp; &nbsp; "department": "finance",
&nbsp; &nbsp; &nbsp; &nbsp; "facutly_type": "part-time",
&nbsp; &nbsp; &nbsp; &nbsp; "email": "wills@onuni.com"
&nbsp; &nbsp; &nbsp; &nbsp; },
&nbsp; &nbsp; "students_enrolled": 18,
&nbsp; &nbsp; "course_publish_date": "2015-06-21",
&nbsp; &nbsp; "course_description": "Mkt 101 is a course from the business school on the introduction to marketing that teaches students the fundamentals of market analysis, customer retention and online advertisements"
}


PUT /courses/classroom/3
{
&nbsp; &nbsp; "name": "Anthropology 230",
&nbsp; &nbsp; "room": "G11",
&nbsp; &nbsp; "professor": {
&nbsp; &nbsp; &nbsp; &nbsp; "name": "Devin Cranford",
&nbsp; &nbsp; &nbsp; &nbsp; "department": "history",
&nbsp; &nbsp; &nbsp; &nbsp; "facutly_type": "full-time",
&nbsp; &nbsp; &nbsp; &nbsp; "email": "devinc@onuni.com"
&nbsp; &nbsp; &nbsp; &nbsp; },
&nbsp; &nbsp; "students_enrolled": 22,
&nbsp; &nbsp; "course_publish_date": "2013-08-27",
&nbsp; &nbsp; "course_description": "Ant 230 is an intermediate course on human societies and cultures and their development. A focus on the Mayans civilization is rooted in this course"
}


PUT /courses/classroom/4
{
&nbsp; &nbsp; "name": "Computer Science 101",
&nbsp; &nbsp; "room": "C12",
&nbsp; &nbsp; "professor": {
&nbsp; &nbsp; &nbsp; &nbsp; "name": "Gregg Payne",
&nbsp; &nbsp; &nbsp; &nbsp; "department": "engineering",
&nbsp; &nbsp; &nbsp; &nbsp; "facutly_type": "full-time",
&nbsp; &nbsp; &nbsp; &nbsp; "email": "payneg@onuni.com"
&nbsp; &nbsp; &nbsp; &nbsp; },
&nbsp; &nbsp; "students_enrolled": 33,
&nbsp; &nbsp; "course_publish_date": "2013-08-27",
&nbsp; &nbsp; "course_description": "CS 101 is a first year computer science introduction teaching fundamental data structures and alogirthms using python. "
}


PUT /courses/classroom/5
{
&nbsp; &nbsp; "name": "Theatre 410",
&nbsp; &nbsp; "room": "T18",
&nbsp; &nbsp; "professor": {
&nbsp; &nbsp; &nbsp; &nbsp; "name": "Sebastian Hern",
&nbsp; &nbsp; &nbsp; &nbsp; "department": "art",
&nbsp; &nbsp; &nbsp; &nbsp; "facutly_type": "part-time",
&nbsp; &nbsp; &nbsp; &nbsp; "email": ""
&nbsp; &nbsp; &nbsp; &nbsp; },
&nbsp; &nbsp; "students_enrolled": 47,
&nbsp; &nbsp; "course_publish_date": "2013-01-27",
&nbsp; &nbsp; "course_description": "Tht 410 is an advanced elective course disecting the various plays written by shakespere during the 16th century"
}






=================================================================
Part 1 - Answers
=================================================================


1. Display all the documents in the courses index
GET /courses/_search


2. Run a query that shows a match for all documents in the courses index
GET /courses/_search
{
"query": {
"match_all":{}
}
}


3. Run a query that only matches room C12 in the courses index
GET /courses/_search
{
"query": {
"match":{"room": "C12"}
}
}
4. Display only the total number documents without ES meta fields in the courses index
GET /courses/_count


More examples






=================================================================
Part2 - Questions
=================================================================
Index the motorvehicles index using the BULK API. Answer the following questions.


&nbsp; POST /motorvehicles/cars/_bulk
&nbsp; { "index": {}}
&nbsp; { "price" : 10000, "color" : "white", "make" : "honda", "sold" : "2016-10-28", "condition": "okay"}
&nbsp; { "index": {}}
&nbsp; { "price" : 20000, "color" : "white", "make" : "honda", "sold" : "2016-11-05", "condition": "new" }
&nbsp; { "index": {}}
&nbsp; { "price" : 30000, "color" : "green", "make" : "ford", "sold" : "2016-05-18", "condition": "new" }
&nbsp; { "index": {}}
&nbsp; { "price" : 15000, "color" : "blue", "make" : "toyota", "sold" : "2016-07-02", "condition": "good" }
&nbsp; { "index": {}}
&nbsp; { "price" : 12000, "color" : "green", "make" : "toyota", "sold" : "2016-08-19" , "condition": "good"}
&nbsp; { "index": {}}
&nbsp; { "price" : 18000, "color" : "red", "make" : "dodge", "sold" : "2016-11-05", "condition": "good" }
&nbsp; { "index": {}}
&nbsp; { "price" : 80000, "color" : "red", "make" : "bmw", "sold" : "2016-01-01", "condition": "new" }
&nbsp; { "index": {}}
&nbsp; { "price" : 25000, "color" : "blue", "make" : "ford", "sold" : "2016-08-22", "condition": "new" }
&nbsp; { "index": {}}
&nbsp; { "price" : 10000, "color" : "gray", "make" : "dodge", "sold" : "2016-02-12", "condition": "okay" }
&nbsp; { "index": {}}
&nbsp; { "price" : 19000, "color" : "red", "make" : "dodge", "sold" : "2016-02-12", "condition": "good" }
&nbsp; { "index": {}}
&nbsp; { "price" : 20000, "color" : "red", "make" : "chevrolet", "sold" : "2016-08-15", "condition": "good" }
&nbsp; { "index": {}}
&nbsp; { "price" : 13000, "color" : "gray", "make" : "chevrolet", "sold" : "2016-11-20", "condition": "okay" }
&nbsp; { "index": {}}
&nbsp; { "price" : 12500, "color" : "gray", "make" : "dodge", "sold" : "2016-03-09", "condition": "okay" }
&nbsp; { "index": {}}
&nbsp; { "price" : 35000, "color" : "red", "make" : "dodge", "sold" : "2016-04-10", "condition": "new" }
&nbsp; { "index": {}}
&nbsp; { "price" : 28000, "color" : "blue", "make" : "chevrolet", "sold" : "2016-08-15", "condition": "new" }
&nbsp; { "index": {}}
&nbsp; { "price" : 30000, "color" : "gray", "make" : "bmw", "sold" : "2016-11-20", "condition": "good"}


-----------------------------------------------------------------------
1. What is the benefit of the BULK API as compared to the PUT command?
2. Display the first 10 documents in the motorvehicles index
3. Display all the documents in the motorvehicles index
4. Show the pagination of the first 5 cars sorted alphabetically
5. Find all the dodge cars
6. Find the count for all the dodge cars


AGGREGATIONS:
1. Find the total number of cars per their make and find Average of all the cars, the lowest car cost and the highest car cost in the motorvehicle index
2. Find all the red cars from all manufacturers together with their aggregations of average, minimum and maximum price
3. Use stats keyword as a shortcut to above aggregations
4. Find the conditions types for all motorvehicles
5. Find the average price for each of the motorvehicles' condition
6. For each of the motorvehicles' conditions, find the respective "make" and find the minimum and maximum price aggregation


=================================================================
Part2 Answers
=================================================================


After Bulk input
Display the first 10 documents in the motorvehicles index (By default, Kibana only shows the first 10 records)


GET /motorvehicles/cars/_search
{
"query": {
"match_all":{}
}
}


Display all the documents in the motorvehicles index
GET /motorvehicles/cars/_search
{
"size": 20,
"query": {
"match_all":{}
}
}


Show the pagination of the first 5 cars sorted alphabetically
GET /motorvehicles/cars/_search
{
"from": 0,
"size": 5,
"query":{
"match_all":{}
},
"sort": [
{"price":{"order": "desc"}}
]
}


Find all the dodge cars
GET /motorvehicles/cars/_search
{
"query": {
"match":{"make": "dodge"}
}
}


Find the count for all the dodge cars
GET /motorvehicles/cars/_count
{
"query": {
"match":{"make": "dodge"}
}
}








AGGREGATIONS:


///more details: https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations.html
Syntax
"aggregations" : {
&nbsp; "<aggregation_name>" : {
&nbsp; &nbsp; "<aggregation_type>" : {
&nbsp; &nbsp; &nbsp; <aggregation_body>
&nbsp; &nbsp; }
&nbsp; &nbsp; [,"meta" : { [<meta_data_body>] } ]?
&nbsp; &nbsp; [,"aggregations" : { [<sub_aggregation>]+ } ]?
&nbsp; }
&nbsp; [,"<aggregation_name_2>" : { ... } ]*
}


Find the total number of cars per their make and find Average of all the cars, the lowest car cost and the highest car cost in the motorvehicle index


GET /motorvehicles/cars/_search
{
"aggs":{
&nbsp;"popular_cars": {
&nbsp;"terms":{
&nbsp;"field": "make.keyword"}
&nbsp;},
&nbsp;"avg_price": {
&nbsp;"avg":{
&nbsp;"field": "price"}
&nbsp;},
&nbsp;"max_price":{
&nbsp;"max":{
&nbsp;"field": "price"}
&nbsp;},
&nbsp;"min_price":{
&nbsp;"min":{
&nbsp;"field": "price"}
}
}
}


Find all the red cars from all manufacturers together with their aggregations of average, minimum and maximum price
GET /motorvehicles/cars/_search
{
"query":{
"match":{"color": "red"}
},
"aggs":{
&nbsp;"popular_cars": {
&nbsp;"terms":{
&nbsp;"field": "make.keyword"}
&nbsp;},
&nbsp;"avg_price": {
&nbsp;"avg":{
&nbsp;"field": "price"}
&nbsp;},
&nbsp;"max_price":{
&nbsp;"max":{
&nbsp;"field": "price"}
&nbsp;},
&nbsp;"min_price":{
&nbsp;"min":{
&nbsp;"field": "price"}
}
}
}


Use stats key word as shortcut to above aggregations
GET /motorvehicles/cars/_search
{
"size":0,
"aggs": {
"popular_cars": {
"terms" : {
"field": "make.keyword"
},
"aggs": {
"stats_on_price": {
"stats":{
"field": "price"}
}}}}}


Find the conditions types for all motorvehicles
GET /motorvehicles/cars/_search
{
"size":0,
"aggs": {
"car_conditions":{
"terms": {
"field": "condition.keyword"
}}}}


Find the average price for each of the motorvehicles' condition
GET /motorvehicles/cars/_search
{
"size":0,
"aggs": {
"car_conditions":{
"terms": {
"field": "condition.keyword"
},
"aggs":{
"avg_price":{
"avg":{
"field": "price"
}}}}}}


For each of the motorvehicles' conditions, find the respective "make" and find the minimum and maximum price aggregation
GET /motorvehicles/cars/_search
{
"size":0,
"aggs": {
"car_conditions":{
"terms": {
"field": "condition.keyword"
},
"aggs":{
"avg_price":{
"avg":{
"field": "price"
}
},
"make":{
"terms": {
&nbsp;"field":"make.keyword"
}}}}}}


-----------------------------------------
GET /motorvehicles/cars/_search
{
"size":0,
"aggs": {
"car_conditions":{
"terms": {
"field": "condition.keyword"
},
"aggs":{
"Min_price":{
"min":{
"field": "price"
}
},
"Max_price":{
"max":{
"field": "price"
}
},
"make":{
"terms": {
&nbsp;"field":"make.keyword"
}}}}}}</aggregation_name_2></sub_aggregation></meta_data_body></aggregation_body></aggregation_type></aggregation_name>
