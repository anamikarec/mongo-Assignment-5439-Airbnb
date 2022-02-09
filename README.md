##### Problem
- use the airbnb sample data
- make the following queries
1. write a query of using two OR operators, and check for listings from any two countries
2. write a query of using two AND operators and check for one country and review ratings to be greater than a particular value
3. write a query of using AND and OR operator in conjuction
    a. it should belong to any two cities and
    b. it should have rating = 99
4. write a query of using AND and OR operator together
    a. it should belong to US and rating of 95 or
    b. it should belong to CA and rating of 99
5. write a query of using querying arrays
    5. 1. check all listings which have amenities of size 5, 6, 7, 8, 9, 10
    5. 2. check all listings of where aminities contain 4 or 5 different listings 
    5. 3. check all listings of reviews where it matches a particular user id and name 
    5. 4. check all listings of reviews where it matches a particular user id and name, list only reviews that match the particular user id and name
6. find top 10 listings, sort them according to rating in descending order, and if the rating is similar rate them according to alphabetic order
    a. also ensure results belong only to New York, and check if there are atleast Wifi, Breakfast and 2 other amenities

- 1. 
```js
     db.airlist.find({$or : [{'address.country_code' :"BR"},{'address.country_code' :"US"}]}).count()
```

- 2. 
```js
db.airlist.find({$and: [{'address.country_code' :"US"},{'review_scores.review_scores_rating' : {$gt:50}}]}).count()
```

- 3. 
```js
    db.airlist.find({$and: [{$or: [{'address.country_code' :"US"},{'address.country_code' :"BR"}]},{'review_scores.review_scores_rating' : {$eq:99}}]}).count()
```

- 4. 
```js
    db.airlist.find({$or : [{$and : [{'address.country_code' : "US"},{'review_scores.review_scores_rating' : {$eq:95}}]},{$and : [{'address.country_code' : "CA"},{'review_scores.review_scores_rating' : {$eq:99}}]}]},{'address.country_code':1,'review_scores.review_scores_rating':1})
```

- 5. 
- 5. 1. 
```js
    db.airlist.find({$or : [{amenities :{$size:5}},{amenities :{$size:6}},{amenities :{$size:7}},{amenities :{$size:8}},{amenities :{$size:9}},{amenities :{$size:10}}]},{amenities :1,_id:0})
```
- 5. 2. 
```js
     db.airlist.find({$or : [{amenities :{$size:4}},{amenities :{$size:5}}]},{amenities :1,_id:0})
```
- 5. 3. 
```js
    
```
- 5. 4. 
```js
    
```

- 6. 
```js

```