What is MongoDB?
 MongoDB is a free and open-source cross-platform  document-oriented database. Classified as a  NoSQL  database, MongoDB avoids the traditional table-based relational database structure in favor of JSON-like documents with dynamic schemas, making the integration of data in certain types of applications easier and faster.

The best way we learn anything is by practice and exercise questions. We have started this section for those (beginner to intermediate) who are familiar with NoSQL and MongoDB. Hope, these exercises help you to improve your MongoDB query skills. Currently, following exercises are available based on collection :

restaurants collection [ 87 Exercises]
listingAndReviews collection [ 50 Exercises]
Movies collection [ 28 Exercises]
MongoDB Query Exercises and Solution [ 87 Exercises]
Structure of 'restaurants' collection:

{
  "address": {
     "building": "1007",
     "coord": [ -73.856077, 40.848447 ],
     "street": "Morris Park Ave",
     "zipcode": "10462"
  },
  "borough": "Bronx",
  "cuisine": "Bakery",
  "grades": [
     { "date": { "$date": 1393804800000 }, "grade": "A", "score": 2 },
     { "date": { "$date": 1378857600000 }, "grade": "A", "score": 6 },
     { "date": { "$date": 1358985600000 }, "grade": "A", "score": 10 },
     { "date": { "$date": 1322006400000 }, "grade": "A", "score": 9 },
     { "date": { "$date": 1299715200000 }, "grade": "B", "score": 14 }
  ],
  "name": "Morris Park Bake Shop",
  "restaurant_id": "30075445"
}
You may download the compressed file and uncompress it to find the collection used in our exercises. The collection comprises of 3772 documents.


1. Write a MongoDB query to display all the documents in the collection restaurants.


2. Write a MongoDB query to display the fields restaurant_id, name, borough and cuisine for all the documents in the collection restaurant.


3. Write a MongoDB query to display the fields restaurant_id, name, borough and cuisine, but exclude the field _id for all the documents in the collection restaurant.


4. Write a MongoDB query to display the fields restaurant_id, name, borough and zip code, but exclude the field _id for all the documents in the collection restaurant.


5. Write a MongoDB query to display all the restaurant which is in the borough Bronx.


6. Write a MongoDB query to display the first 5 restaurant which is in the borough Bronx.


7.Write a MongoDB query to display the next 5 restaurants after skipping first 5 which are in the borough Bronx.


8. Write a MongoDB query to find the restaurants who achieved a score more than 90.


9. Write a MongoDB query to find the restaurants that achieved a score, more than 80 but less than 100.


10. Write a MongoDB query to find the restaurants which locate in latitude value less than -95.754168.


11. Write a  MongoDB query to find the restaurants that do not prepare any cuisine of 'American' and their grade score more than 70 and latitude less than -65.754168.


12. Write a MongoDB query to find the restaurants which do not prepare any cuisine of 'American' and achieved a score more than 70 and located in the longitude less than -65.754168.
Note : Do this query without using $and operator.



13. Write a MongoDB query to find the restaurants which do not prepare any cuisine of 'American' and achieved a grade point 'A' not belongs to the borough Brooklyn. The document must be displayed according to the cuisine in descending order.


14. Write a MongoDB query to find the restaurant Id, name, borough and cuisine for those restaurants which contain 'Wil' as first three letters for its name.


15. Write a MongoDB query to find the restaurant Id, name, borough and cuisine for those restaurants which contain 'ces' as last three letters for its name.


16. Write a MongoDB query to find the restaurant Id, name, borough and cuisine for those restaurants which contain 'Reg' as three letters somewhere in its name.


17. Write a MongoDB query to find the restaurants which belong to the borough Bronx and prepared either American or Chinese dish.


18. Write a MongoDB query to find the restaurant Id, name, borough and cuisine for those restaurants which belong to the borough Staten Island or Queens or Bronxor Brooklyn.


19. Write a MongoDB query to find the restaurant Id, name, borough and cuisine for those restaurants which are not belonging to the borough Staten Island or Queens or Bronxor Brooklyn.


20. Write a MongoDB query to find the restaurant Id, name, borough and cuisine for those restaurants which achieved a score which is not more than 10.


21. Write a  MongoDB query to find the restaurant Id, name, borough and cuisine for those restaurants which prepared dish except 'American' and 'Chinees' or restaurant's name begins with letter 'Wil'.


22. Write a MongoDB query to find the restaurant Id, name, and grades for those restaurants which achieved a grade of "A" and scored 11 on an ISODate "2014-08-11T00:00:00Z" among many of survey dates..



23. Write a MongoDB query to find the restaurant Id, name and grades for those restaurants where the 2nd element of grades array contains a grade of "A" and score 9 on an ISODate "2014-08-11T00:00:00Z".


24. Write a MongoDB query to find the restaurant Id, name, address and geographical location for those restaurants where 2nd element of coord array contains a value which is more than 42 and upto 52..


25. Write a MongoDB query to arrange the name of the restaurants in ascending order along with all the columns.


26. Write a MongoDB query to arrange the name of the restaurants in descending along with all the columns.


27. Write a MongoDB query to arranged the name of the cuisine in ascending order and for that same cuisine borough should be in descending order.


28. Write a MongoDB query to know whether all the addresses contains the street or not.

Sure! Here are the MongoDB queries for each of the requests:

1. **Display all the documents in the collection `restaurants`.**

   ```javascript
   db.restaurants.find({})
   ```

2. **Display the fields `restaurant_id`, `name`, `borough`, and `cuisine` for all documents in the collection `restaurants`.**

   ```javascript
   db.restaurants.find({}, { restaurant_id: 1, name: 1, borough: 1, cuisine: 1 })
   ```

3. **Display the fields `restaurant_id`, `name`, `borough`, and `cuisine`, but exclude the field `_id` for all documents in the collection `restaurants`.**

   ```javascript
   db.restaurants.find({}, { restaurant_id: 1, name: 1, borough: 1, cuisine: 1, _id: 0 })
   ```

4. **Display the fields `restaurant_id`, `name`, `borough`, and `zip code`, but exclude the field `_id` for all documents in the collection `restaurants`.**

   ```javascript
   db.restaurants.find({}, { restaurant_id: 1, name: 1, borough: 1, zip_code: 1, _id: 0 })
   ```

5. **Display all the restaurants which are in the borough `Bronx`.**

   ```javascript
   db.restaurants.find({ borough: "Bronx" })
   ```

6. **Display the first 5 restaurants which are in the borough `Bronx`.**

   ```javascript
   db.restaurants.find({ borough: "Bronx" }).limit(5)
   ```

7. **Display the next 5 restaurants after skipping the first 5 which are in the borough `Bronx`.**

   ```javascript
   db.restaurants.find({ borough: "Bronx" }).skip(5).limit(5)
   ```

8. **Find the restaurants who achieved a score more than 90.**

   ```javascript
   db.restaurants.find({ "grades.score": { $gt: 90 } })
   ```

9. **Find the restaurants that achieved a score more than 80 but less than 100.**

   ```javascript
   db.restaurants.find({ "grades.score": { $gt: 80, $lt: 100 } })
   ```

10. **Find the restaurants which are located in latitude value less than -95.754168.**

    ```javascript
    db.restaurants.find({ "address.coord.0": { $lt: -95.754168 } })
    ```

11. **Find the restaurants that do not prepare any cuisine of `American` and their grade score more than 70 and latitude less than -65.754168.**

    ```javascript
    db.restaurants.find({
        cuisine: { $ne: "American" },
        "grades.score": { $gt: 70 },
        "address.coord.0": { $lt: -65.754168 }
    })
    ```

12. **Find the restaurants which do not prepare any cuisine of `American` and achieved a score more than 70 and located in the longitude less than -65.754168. Note: Do this query without using `$and` operator.**

    ```javascript
    db.restaurants.find({
        cuisine: { $ne: "American" },
        "grades.score": { $gt: 70 },
        "address.coord.1": { $lt: -65.754168 }
    })
    ```

13. **Find the restaurants which do not prepare any cuisine of `American` and achieved a grade point `A` not belonging to the borough `Brooklyn`. The document must be displayed according to the cuisine in descending order.**

    ```javascript
    db.restaurants.find({
        cuisine: { $ne: "American" },
        "grades.grade": "A",
        borough: { $ne: "Brooklyn" }
    }).sort({ cuisine: -1 })
    ```

14. **Find the restaurant ID, name, borough, and cuisine for those restaurants which contain `Wil` as the first three letters of their name.**

    ```javascript
    db.restaurants.find({ name: /^Wil/ }, { restaurant_id: 1, name: 1, borough: 1, cuisine: 1 })
    ```

15. **Find the restaurant ID, name, borough, and cuisine for those restaurants which contain `ces` as the last three letters of their name.**

    ```javascript
    db.restaurants.find({ name: /ces$/ }, { restaurant_id: 1, name: 1, borough: 1, cuisine: 1 })
    ```

16. **Find the restaurant ID, name, borough, and cuisine for those restaurants which contain `Reg` as three letters somewhere in their name.**

    ```javascript
    db.restaurants.find({ name: /Reg/ }, { restaurant_id: 1, name: 1, borough: 1, cuisine: 1 })
    ```

17. **Find the restaurants which belong to the borough `Bronx` and prepare either `American` or `Chinese` dishes.**

    ```javascript
    db.restaurants.find({
        borough: "Bronx",
        cuisine: { $in: ["American", "Chinese"] }
    })
    ```

18. **Find the restaurant ID, name, borough, and cuisine for those restaurants which belong to the borough `Staten Island` or `Queens` or `Bronx` or `Brooklyn`.**

    ```javascript
    db.restaurants.find({
        borough: { $in: ["Staten Island", "Queens", "Bronx", "Brooklyn"] }
    }, { restaurant_id: 1, name: 1, borough: 1, cuisine: 1 })
    ```

19. **Find the restaurant ID, name, borough, and cuisine for those restaurants which are not belonging to the borough `Staten Island` or `Queens` or `Bronx` or `Brooklyn`.**

    ```javascript
    db.restaurants.find({
        borough: { $nin: ["Staten Island", "Queens", "Bronx", "Brooklyn"] }
    }, { restaurant_id: 1, name: 1, borough: 1, cuisine: 1 })
    ```

20. **Find the restaurant ID, name, borough, and cuisine for those restaurants which achieved a score that is not more than 10.**

    ```javascript
    db.restaurants.find({
        "grades.score": { $lte: 10 }
    }, { restaurant_id: 1, name: 1, borough: 1, cuisine: 1 })
    ```

21. **Find the restaurant ID, name, borough, and cuisine for those restaurants which prepare dishes except `American` and `Chinese`, or whose name begins with the letter `Wil`.**

    ```javascript
    db.restaurants.find({
        $or: [
            { cuisine: { $nin: ["American", "Chinese"] } },
            { name: /^Wil/ }
        ]
    }, { restaurant_id: 1, name: 1, borough: 1, cuisine: 1 })
    ```

22. **Find the restaurant ID, name, and grades for those restaurants which achieved a grade of `A` and scored 11 on an ISODate `"2014-08-11T00:00:00Z"` among many of survey dates.**

    ```javascript
    db.restaurants.find({
        "grades.grade": "A",
        "grades.score": 11,
        "grades.date": new Date("2014-08-11T00:00:00Z")
    }, { restaurant_id: 1, name: 1, grades: 1 })
    ```

23. **Find the restaurant ID, name, and grades for those restaurants where the 2nd element of the grades array contains a grade of `A` and a score of 9 on an ISODate `"2014-08-11T00:00:00Z"`.**

    ```javascript
    db.restaurants.find({
        "grades.1.grade": "A",
        "grades.1.score": 9,
        "grades.1.date": new Date("2014-08-11T00:00:00Z")
    }, { restaurant_id: 1, name: 1, grades: 1 })
    ```

24. **Find the restaurant ID, name, address, and geographical location for those restaurants where the 2nd element of the `coord` array contains a value which is more than 42 and up to 52.**

    ```javascript
    db.restaurants.find({
        "address.coord.1": { $gt: 42, $lte: 52 }
    }, { restaurant_id: 1, name: 1, address: 1, "address.coord": 1 })
    ```

25. **Arrange the name of the restaurants in ascending order along with all the columns.**

    ```javascript
    db.restaurants.find({}).sort({ name: 1 })
    ```

26. **Arrange the name of the restaurants in descending order along with all the columns.**

    ```javascript
    db.restaurants.find({}).sort({ name: -1 })
    ```

27. **Arrange the name of the cuisine in ascending order and for that same cuisine borough should be in descending order.**

    ```javascript
    db.restaurants.find({}).sort({ cuisine: 1, borough: -1 })
    ```

28. **Know whether all the addresses contain the street or not.**

    ```javascript
    db.restaurants.find({ "address.street": { $exists: true } })
    ```



29. Write a MongoDB query which will select all documents in the restaurants collection where the coord field value is Double.


30. Write a MongoDB query which will select the restaurant Id, name and grades for those restaurants which returns 0 as a remainder after dividing the score by 7.


31. Write a MongoDB query to find the restaurant name, borough, longitude and attitude and cuisine for those restaurants which contains 'mon' as three letters somewhere in its name.


32. Write a MongoDB query to find the restaurant name, borough, longitude and latitude and cuisine for those restaurants which contain 'Mad' as first three letters of its name.


33. Write a  MongoDB query to find the restaurants that have at least one grade with a score of less than 5.


34. Write a MongoDB query to find the restaurants that have at least one grade with a score of less than 5 and that are located in the borough of Manhattan.


35. Write a MongoDB query to find the restaurants that have at least one grade with a score of less than 5 and that are located in the borough of Manhattan or Brooklyn.


36. Write a MongoDB query to find the restaurants that have at least one grade with a score of less than 5 and that are located in the borough of Manhattan or Brooklyn, and their cuisine is not American.


37. Write a MongoDB query to find the restaurants that have at least one grade with a score of less than 5 and that are located in the borough of Manhattan or Brooklyn, and their cuisine is not American or Chinese.


38. Write a MongoDB query to find the restaurants that have a grade with a score of 2 and a grade with a score of 6.


39. Write a MongoDB query to find the restaurants that have a grade with a score of 2 and a grade with a score of 6 and are located in the borough of Manhattan.


40. Write a MongoDB query to find the restaurants that have a grade with a score of 2 and a grade with a score of 6 and are located in the borough of Manhattan or Brooklyn.


41. Write a MongoDB query to find the restaurants that have a grade with a score of 2 and a grade with a score of 6 and are located in the borough of Manhattan or Brooklyn, and their cuisine is not American.


42. Write a  MongoDB query to find the restaurants that have a grade with a score of 2 and a grade with a score of 6 and are located in the borough of Manhattan or Brooklyn, and their cuisine is not American or Chinese.


43. Write a MongoDB query to find the restaurants that have a grade with a score of 2 or a grade with a score of 6.


44. Write a MongoDB query to find the restaurants that have a grade with a score of 2 or a grade with a score of 6 and are located in the borough of Manhattan.


45. Write a MongoDB query to find the restaurants that have a grade with a score of 2 or a grade with a score of 6 and are located in the borough of Manhattan or Brooklyn.


46. Write a MongoDB query to find the restaurants that have a grade with a score of 2 or a grade with a score of 6 and are located in the borough of Manhattan or Brooklyn, and their cuisine is not American.


47. Write a MongoDB query to find the restaurants that have a grade with a score of 2 or a grade with a score of 6 and are located in the borough of Manhattan or Brooklyn, and their cuisine is not American or Chinese.


48. Write a MongoDB query to find the restaurants that have all grades with a score greater than 5.


49. Write a MongoDB query to find the restaurants that have all grades with a score greater than 5 and are located in the borough of Manhattan.


50. Write a MongoDB query to find the restaurants that have all grades with a score greater than 5 and are located in the borough of Manhattan or Brooklyn.


51. Write a  MongoDB query to find the average score for each restaurant.


52. Write a MongoDB query to find the highest score for each restaurant.


53. Write a MongoDB query to find the lowest score for each restaurant.


54. Write a MongoDB query to find the count of restaurants in each borough.


55. Write a MongoDB query to find the count of restaurants for each cuisine.


56. Write a MongoDB query to find the count of restaurants for each cuisine and borough.


57. Write a MongoDB query to find the count of restaurants that received a grade of 'A' for each cuisine.


58. Write a MongoDB query to find the count of restaurants that received a grade of 'A' for each borough.


59. Write a MongoDB query to find the count of restaurants that received a grade of 'A' for each cuisine and borough.


60. Write a MongoDB query to find the number of restaurants that have been graded in each month of the year.


61. Write a MongoDB query to find the average score for each cuisine.


62. Write a MongoDB query to find the highest score for each cuisine.


63. Write a MongoDB query to find the lowest score for each cuisine.


64. Write a MongoDB query to find the average score for each borough.


65. Write a MongoDB query to find the highest score for each borough.


66. Write a MongoDB query to find the lowest score for each borough.


67. Write a MongoDB query to find the name and address of the restaurants that received a grade of 'A' on a specific date.


68. Write a MongoDB query to find the name and address of the restaurants that received a grade of 'B' or 'C' on a specific date.


69. Write a MongoDB query to find the name and address of the restaurants that have at least one 'A' grade and one 'B' grade.


70. Write a  MongoDB query to find the name and address of the restaurants that have at least one 'A' grade and no 'B' grades.


71. Write a MongoDB query to find the name ,address and grades of the restaurants that have at least one 'A' grade and no 'C' grades.


72. Write a MongoDB query to find the name, address, and grades of the restaurants that have at least one 'A' grade, no 'B' grades, and no 'C' grades.


73. Write a MongoDB query to find the name and address of the restaurants that have the word 'coffee' in their name.


74. Write a MongoDB query to find the name and address of the restaurants that have a zipcode that starts with '10'.


75. Write a MongoDB query to find the name and address of the restaurants that have a cuisine that starts with the letter 'B'.


76. Write a MongoDB query to find the name, address, and cuisine of the restaurants that have a cuisine that ends with the letter 'y'.


77. Write a MongoDB query to find the name, address, and cuisine of the restaurants that have a cuisine that contains the word 'Pizza'.


78. Write a MongoDB query to find the restaurants achieved highest average score.


79. Write a MongoDB query to find all the restaurants with the highest number of "A" grades.


80. Write a MongoDB query to find the cuisine type that is most likely to receive a "C" grade.


81. Write a MongoDB query to find the restaurant that has the highest average score for thecuisine "Turkish".


82. Write a MongoDB query to find the restaurants that achieved the highest total score.


83. Write a MongoDB query to find all the Chinese restaurants in Brooklyn.


84. Write a MongoDB query to find the restaurant with the most recent grade date.


85. Write a  MongoDB query to find the top 5 restaurants with the highest average score for each cuisine type, along with their average scores.


86. Write a MongoDB query to find the top 5 restaurants in each borough with the highest number of "A" grades.


87. Write a MongoDB query to find the borough with the highest number of restaurants that have a grade of "A" and a score greater than or equal to 90.

Sure, here are the MongoDB queries for the provided requirements:

### Query 29
**Select all documents in the `restaurants` collection where the `coord` field value is of type `Double`:**
```javascript
db.restaurants.find({
  "coord": { $type: "double" }
})
```

### Query 30
**Select the restaurant Id, name, and grades for those restaurants where the score returns 0 as a remainder after dividing by 7:**
```javascript
db.restaurants.find(
  { "grades.score": { $mod: [7, 0] } },
  { "restaurant_id": 1, "name": 1, "grades": 1, _id: 0 }
)
```

### Query 31
**Find the restaurant name, borough, longitude, latitude, and cuisine for those restaurants which contain 'mon' as three letters somewhere in its name:**
```javascript
db.restaurants.find(
  { "name": /mon/ },
  { "name": 1, "borough": 1, "address.coord": 1, "cuisine": 1, _id: 0 }
)
```

### Query 32
**Find the restaurant name, borough, longitude, latitude, and cuisine for those restaurants which contain 'Mad' as the first three letters of its name:**
```javascript
db.restaurants.find(
  { "name": /^Mad/ },
  { "name": 1, "borough": 1, "address.coord": 1, "cuisine": 1, _id: 0 }
)
```

### Query 33
**Find the restaurants that have at least one grade with a score of less than 5:**
```javascript
db.restaurants.find(
  { "grades.score": { $lt: 5 } }
)
```

### Query 34
**Find the restaurants that have at least one grade with a score of less than 5 and that are located in the borough of Manhattan:**
```javascript
db.restaurants.find(
  { 
    "grades.score": { $lt: 5 },
    "borough": "Manhattan"
  }
)
```

### Query 35
**Find the restaurants that have at least one grade with a score of less than 5 and that are located in the borough of Manhattan or Brooklyn:**
```javascript
db.restaurants.find(
  { 
    "grades.score": { $lt: 5 },
    "borough": { $in: ["Manhattan", "Brooklyn"] }
  }
)
```

### Query 36
**Find the restaurants that have at least one grade with a score of less than 5, located in the borough of Manhattan or Brooklyn, and their cuisine is not American:**
```javascript
db.restaurants.find(
  { 
    "grades.score": { $lt: 5 },
    "borough": { $in: ["Manhattan", "Brooklyn"] },
    "cuisine": { $ne: "American" }
  }
)
```

### Query 37
**Find the restaurants that have at least one grade with a score of less than 5, located in the borough of Manhattan or Brooklyn, and their cuisine is not American or Chinese:**
```javascript
db.restaurants.find(
  { 
    "grades.score": { $lt: 5 },
    "borough": { $in: ["Manhattan", "Brooklyn"] },
    "cuisine": { $nin: ["American", "Chinese"] }
  }
)
```

### Query 38
**Find the restaurants that have a grade with a score of 2 and a grade with a score of 6:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $all: [
        { $elemMatch: { "score": 2 } },
        { $elemMatch: { "score": 6 } }
      ]
    }
  }
)
```

### Query 39
**Find the restaurants that have a grade with a score of 2 and a grade with a score of 6 and are located in the borough of Manhattan:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $all: [
        { $elemMatch: { "score": 2 } },
        { $elemMatch: { "score": 6 } }
      ]
    },
    "borough": "Manhattan"
  }
)
```

### Query 40
**Find the restaurants that have a grade with a score of 2 and a grade with a score of 6 and are located in the borough of Manhattan or Brooklyn:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $all: [
        { $elemMatch: { "score": 2 } },
        { $elemMatch: { "score": 6 } }
      ]
    },
    "borough": { $in: ["Manhattan", "Brooklyn"] }
  }
)
```

### Query 41
**Find the restaurants that have a grade with a score of 2 and a grade with a score of 6, are located in the borough of Manhattan or Brooklyn, and their cuisine is not American:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $all: [
        { $elemMatch: { "score": 2 } },
        { $elemMatch: { "score": 6 } }
      ]
    },
    "borough": { $in: ["Manhattan", "Brooklyn"] },
    "cuisine": { $ne: "American" }
  }
)
```

### Query 42
**Find the restaurants that have a grade with a score of 2 and a grade with a score of 6, are located in the borough of Manhattan or Brooklyn, and their cuisine is not American or Chinese:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $all: [
        { $elemMatch: { "score": 2 } },
        { $elemMatch: { "score": 6 } }
      ]
    },
    "borough": { $in: ["Manhattan", "Brooklyn"] },
    "cuisine": { $nin: ["American", "Chinese"] }
  }
)
```

### Query 43
**Find the restaurants that have a grade with a score of 2 or a grade with a score of 6:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $elemMatch: { "score": { $in: [2, 6] } }
    }
  }
)
```

### Query 44
**Find the restaurants that have a grade with a score of 2 or a grade with a score of 6 and are located in the borough of Manhattan:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $elemMatch: { "score": { $in: [2, 6] } }
    },
    "borough": "Manhattan"
  }
)
```

### Query 45
**Find the restaurants that have a grade with a score of 2 or a grade with a score of 6 and are located in the borough of Manhattan or Brooklyn:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $elemMatch: { "score": { $in: [2, 6] } }
    },
    "borough": { $in: ["Manhattan", "Brooklyn"] }
  }
)
```

### Query 46
**Find the restaurants that have a grade with a score of 2 or a grade with a score of 6, are located in the borough of Manhattan or Brooklyn, and their cuisine is not American:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $elemMatch: { "score": { $in: [2, 6] } }
    },
    "borough": { $in: ["Manhattan", "Brooklyn"] },
    "cuisine": { $ne: "American" }
  }
)
```

### Query 47
**Find the restaurants that have a grade with a score of 2 or a grade with a score of 6, are located in the borough of Manhattan or Brooklyn, and their cuisine is not American or Chinese:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $elemMatch: { "score": { $in: [2, 6] } }
    },
    "borough": { $in: ["Manhattan", "Brooklyn"] },
    "cuisine": { $nin: ["American", "Chinese"] }
  }
)
```

### Query 48
**Find the restaurants that have all grades with a score greater than 5:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $not: { $elemMatch: { "score": { $lte: 5 } } }
    }
  }
)
```

### Query 49
**Find the restaurants that have all grades with a score greater than 5 and are located in the borough of Manhattan:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $not: { $elemMatch: { "score": { $lte: 5 } } }
    },
    "borough": "Manhattan"
  }
)
```

### Query 50
**Find the restaurants that have all grades with a score greater than 5 and are located in the borough of Manhattan or Brooklyn:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $

not: { $elemMatch: { "score": { $lte: 5 } } }
    },
    "borough": { $in: ["Manhattan", "Brooklyn"] }
  }
)
```

### Query 51
**Find the average score for each restaurant:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $group: { _id: "$restaurant_id", avgScore: { $avg: "$grades.score" } } }
])
```

### Query 52
**Find the highest score for each restaurant:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $group: { _id: "$restaurant_id", highestScore: { $max: "$grades.score" } } }
])
```

### Query 53
**Find the lowest score for each restaurant:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $group: { _id: "$restaurant_id", lowestScore: { $min: "$grades.score" } } }
])
```

### Query 54
**Find the count of restaurants in each borough:**
```javascript
db.restaurants.aggregate([
  { $group: { _id: "$borough", count: { $sum: 1 } } }
])
```

### Query 55
**Find the count of restaurants for each cuisine:**
```javascript
db.restaurants.aggregate([
  { $group: { _id: "$cuisine", count: { $sum: 1 } } }
])
```

### Query 56
**Find the count of restaurants for each cuisine and borough:**
```javascript
db.restaurants.aggregate([
  { $group: { _id: { cuisine: "$cuisine", borough: "$borough" }, count: { $sum: 1 } } }
])
```

### Query 57
**Find the count of restaurants that received a grade of 'A' for each cuisine:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $match: { "grades.grade": "A" } },
  { $group: { _id: "$cuisine", count: { $sum: 1 } } }
])
```

### Query 58
**Find the count of restaurants that received a grade of 'A' for each borough:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $match: { "grades.grade": "A" } },
  { $group: { _id: "$borough", count: { $sum: 1 } } }
])
```

### Query 59
**Find the count of restaurants that received a grade of 'A' for each cuisine and borough:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $match: { "grades.grade": "A" } },
  { $group: { _id: { cuisine: "$cuisine", borough: "$borough" }, count: { $sum: 1 } } }
])
```

### Query 60
**Find the number of restaurants that have been graded in each month of the year:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $project: { month: { $month: "$grades.date" } } },
  { $group: { _id: "$month", count: { $sum: 1 } } }
])
```

### Query 61
**Find the average score for each cuisine:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $group: { _id: "$cuisine", avgScore: { $avg: "$grades.score" } } }
])
```

### Query 62
**Find the highest score for each cuisine:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $group: { _id: "$cuisine", highestScore: { $max: "$grades.score" } } }
])
```

### Query 63
**Find the lowest score for each cuisine:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $group: { _id: "$cuisine", lowestScore: { $min: "$grades.score" } } }
])
```

### Query 64
**Find the average score for each borough:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $group: { _id: "$borough", avgScore: { $avg: "$grades.score" } } }
])
```

### Query 65
**Find the highest score for each borough:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $group: { _id: "$borough", highestScore: { $max: "$grades.score" } } }
])
```

### Query 66
**Find the lowest score for each borough:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $group: { _id: "$borough", lowestScore: { $min: "$grades.score" } } }
])
```

### Query 67
**Find the name and address of the restaurants that received a grade of 'A' on a specific date:**
```javascript
db.restaurants.find(
  { 
    "grades.grade": "A",
    "grades.date": new Date("specific_date_here")
  },
  { "name": 1, "address": 1, _id: 0 }
)
```

### Query 68
**Find the name and address of the restaurants that received a grade of 'B' or 'C' on a specific date:**
```javascript
db.restaurants.find(
  { 
    "grades.grade": { $in: ["B", "C"] },
    "grades.date": new Date("specific_date_here")
  },
  { "name": 1, "address": 1, _id: 0 }
)
```

### Query 69
**Find the name and address of the restaurants that have at least one 'A' grade and one 'B' grade:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $all: [
        { $elemMatch: { "grade": "A" } },
        { $elemMatch: { "grade": "B" } }
      ]
    }
  },
  { "name": 1, "address": 1, _id: 0 }
)
```

### Query 70
**Find the name and address of the restaurants that have at least one 'A' grade and no 'B' grades:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $elemMatch: { "grade": "A" },
      $not: { $elemMatch: { "grade": "B" } }
    }
  },
  { "name": 1, "address": 1, _id: 0 }
)
```

### Query 71
**Find the name, address, and grades of the restaurants that have at least one 'A' grade and no 'C' grades:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $elemMatch: { "grade": "A" },
      $not: { $elemMatch: { "grade": "C" } }
    }
  },
  { "name": 1, "address": 1, "grades": 1, _id: 0 }
)
```

### Query 72
**Find the name, address, and grades of the restaurants that have at least one 'A' grade, no 'B' grades, and no 'C' grades:**
```javascript
db.restaurants.find(
  { 
    "grades": { 
      $elemMatch: { "grade": "A" },
      $not: { $elemMatch: { "grade": { $in: ["B", "C"] } } }
    }
  },
  { "name": 1, "address": 1, "grades": 1, _id: 0 }
)
```

### Query 73
**Find the name and address of the restaurants that have the word 'coffee' in their name:**
```javascript
db.restaurants.find(
  { "name": /coffee/i },
  { "name": 1, "address": 1, _id: 0 }
)
```

### Query 74
**Find the name and address of the restaurants that have a zipcode that starts with '10':**
```javascript
db.restaurants.find(
  { "address.zipcode": /^10/ },
  { "name": 1, "address": 1, _id: 0 }
)
```

### Query 75
**Find the name and address of the restaurants that have a cuisine that starts with the letter 'B':**
```javascript
db.restaurants.find(
  { "cuisine": /^B/ },
  { "name": 1, "address": 1, _id: 0 }
)
```

### Query 76
**Find the name, address, and cuisine of the restaurants that have a cuisine that ends with the letter 'y':**
```javascript
db.restaurants.find(
  { "cuisine": /y$/ },
  { "name": 1, "address": 1, "cuisine": 1, _id: 0 }
)
```

### Query 77
**Find

 the name, address, and cuisine of the restaurants that have a cuisine that contains the word 'Pizza':**
```javascript
db.restaurants.find(
  { "cuisine": /Pizza/i },
  { "name": 1, "address": 1, "cuisine": 1, _id: 0 }
)
```

### Query 78
**Find the restaurants that achieved the highest average score:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $group: { _id: "$restaurant_id", avgScore: { $avg: "$grades.score" } } },
  { $sort: { avgScore: -1 } },
  { $limit: 1 }
])
```

### Query 79
**Find all the restaurants with the highest number of "A" grades:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $match: { "grades.grade": "A" } },
  { $group: { _id: "$restaurant_id", aCount: { $sum: 1 } } },
  { $sort: { aCount: -1 } },
  { $limit: 1 }
])
```

### Query 80
**Find the cuisine type that is most likely to receive a "C" grade:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $match: { "grades.grade": "C" } },
  { $group: { _id: "$cuisine", cCount: { $sum: 1 } } },
  { $sort: { cCount: -1 } },
  { $limit: 1 }
])
```

### Query 81
**Find the restaurant with the highest average score for the cuisine "Turkish":**
```javascript
db.restaurants.aggregate([
  { $match: { "cuisine": "Turkish" } },
  { $unwind: "$grades" },
  { $group: { _id: "$restaurant_id", avgScore: { $avg: "$grades.score" } } },
  { $sort: { avgScore: -1 } },
  { $limit: 1 }
])
```

### Query 82
**Find the restaurants that achieved the highest total score:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $group: { _id: "$restaurant_id", totalScore: { $sum: "$grades.score" } } },
  { $sort: { totalScore: -1 } },
  { $limit: 1 }
])
```

### Query 83
**Find all the Chinese restaurants in Brooklyn:**
```javascript
db.restaurants.find(
  { 
    "cuisine": "Chinese",
    "borough": "Brooklyn"
  }
)
```

### Query 84
**Find the restaurant with the most recent grade date:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $sort: { "grades.date": -1 } },
  { $group: { _id: "$restaurant_id", mostRecentDate: { $first: "$grades.date" } } },
  { $sort: { mostRecentDate: -1 } },
  { $limit: 1 }
])
```

### Query 85
**Find the top 5 restaurants with the highest average score for each cuisine type, along with their average scores:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $group: { _id: { cuisine: "$cuisine", restaurant_id: "$restaurant_id" }, avgScore: { $avg: "$grades.score" } } },
  { $sort: { "_id.cuisine": 1, avgScore: -1 } },
  { $group: { _id: "$_id.cuisine", topRestaurants: { $push: { restaurant_id: "$_id.restaurant_id", avgScore: "$avgScore" } } } },
  { $project: { topRestaurants: { $slice: ["$topRestaurants", 5] } } }
])
```

### Query 86
**Find the top 5 restaurants in each borough with the highest number of "A" grades:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $match: { "grades.grade": "A" } },
  { $group: { _id: { borough: "$borough", restaurant_id: "$restaurant_id" }, aCount: { $sum: 1 } } },
  { $sort: { "_id.borough": 1, aCount: -1 } },
  { $group: { _id: "$_id.borough", topRestaurants: { $push: { restaurant_id: "$_id.restaurant_id", aCount: "$aCount" } } } },
  { $project: { topRestaurants: { $slice: ["$topRestaurants", 5] } } }
])
```

### Query 87
**Find the borough with the highest number of restaurants that have a grade of "A" and a score greater than or equal to 90:**
```javascript
db.restaurants.aggregate([
  { $unwind: "$grades" },
  { $match: { "grades.grade": "A", "grades.score": { $gte: 90 } } },
  { $group: { _id: "$borough", count: { $sum: 1 } } },
  { $sort: { count: -1 } },
  { $limit: 1 }
])
```

These queries cover a wide range of use cases for working with MongoDB collections of restaurant data. Let me know if you need further assistance!
