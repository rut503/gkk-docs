# MongoDB Data Model

## Producer Documents
```json
{
    "_id": 123456,
    "firstName": "Bob",
    "lastName": "Bill",
    "phoneNum": "8157657895",
    "address": {
        "street": "123 Fake Street",
        "city": "DeKalb",
        "state": "IL",
        "zip": "60000",
    },
    // Array that contains the food items assocaited with this producer
    "food": [foodId, foodId],
    "averageProducerRating": 5,
    // Array that contains the orders associated with this producer
    "currentOrders": [orderId, orderId],
    // Archived orders
    "archivedOrders": [orderId, orderId],
    // Contains the menu of a producer for a week
    "menu": {
        "sunday": {
            "breakfast": [foodId, foodId],
            "lunch": [],
            "dinner": []
        },
        "monday": {
            "breakfast": [foodId],
            "lunch": [foodId],
            "dinner": [foodId]
        },
        "tuesday": {
            ....
        },...
    },
    "dateCreated": "2021-10-24T02:10:00.814+00:00",
    "dataUpdated": "2021-10-24T02:10:00.814+00:00"
}
```

## Reviews for Producers Documents

```json
{
    // Review for chef 123456
    "_id": 1,
    "consumerId": 555555,
    "producerId": 123456, 
    "rating": 5,
    "title": "Best. Food. Ever",
    // Reviews bounded to 300 characters
    "description": "Food was nice and warm",
    "dateCreated": "2021-11-01T13:00:00.000+00:00"
}
```

## Consumer Documents
```json
{
    "_id": 555555,
    "name": "Bob",
    "phoneNum": "8157657895",
    "address": {
        "street": "123 Fake Street",
        "city": "DeKalb",
        "state": "IL",
        "zip": "60000",
    },
    "averageConsumerRating": 2,
    "currentOrders": [orderId, orderId],
    "archievedOrders": [],
    "dateCreated": "2021-10-24T02:10:00.814+00:00",
    "dataUpdated": "2021-10-24T02:10:00.814+00:00"
}
```

## Reviews for Consumer Documents
```json
{
    "_id": 1,
    "consumerId": ,
    "producerId": 555555, 
    "rating": 1,
    "title": "Worst. Customer. Ever.",
    // Reviews bounded to 300 characters
    "description": "wtf",
    "dateCreated": "2021-11-01T13:00:00.000+00:00"
}
```

// Separate Food document which will have a location property.
// Producer reviews are tied to food, not user
// Limit of 50 food items per user
## Food Documents
```json
{
    "_id": 12568, 
    "producerId": 546,
    "dietPreference": "N/A",
    "description": "American French Fries",
    "photo": "image.jpg",
    "price": 5.00,
    "rating": 4.54, 
    "name": "French Fries",
    "portionSize": 1.4,
    "spicy": 0,
    "dateCreated": "2021-11-01T13:00:00.000+00:00",
    "dateUpdated": "2021-11-01T13:00:00.000+00:00"
}
```

## Reviews for Food
```json
{
    "foodId": 12568,
    "consumerId": 555555,
    "rating": 5,
    "title": "Best cookies ever",
    "description": "The texture. The taste. My satisfactory face, 10/10",
    "dateCreated": "2021-11-01T13:00:00.000+00:00"
}
```

## Order Documents
```json
{
    "id": 123456789,
    "consumerId": 555555,
    "producerId": 123456,
    "items": [{
        foodId: 12568,
        quantity :12
    }],
    "amount": 7.00,
    "status": "producer pending",
    "mealTime": "breakfast",
    "pickUpDateTime": "2021-11-01T13:00:00.000+00:00",
    "dateCreated": "2021-10-25T19:21:14.963+00:00",
    "dateUpdated": "2021-10-25T19:21:14.963+00:00",
}
```

Notes for implementation:
Whenever a new review is added, the averageRating value needs to be recalculated. 

Embedded documents are most useful when you only use a single read statement to get all the data needed. 

Manual references are when you save the _id field of one document in another document as a reference. Then you application can run a second query to return the related data. 
Source: https://docs.mongodb.com/manual/reference/database-references/
*************************************************************************************************
Most used queries. 

1) Display the orders for a consumer and producer.

2) Display the menu items for a single producer. 

3) Display the food items offered in a set location, set time and diet restriction


User Cases:

Use Case 1:
Consumer wants to find Chinese food on the 9th for breakfast. 
App would query the Location collection and find the document that corresponds
to the 9th. 

Use Case 2: 
Producer wants to add a new food to their menu.
App will insert a new food document to the Food collection. 
App will use the producersId to find an the producer's document. 
App will add the foodId to the Food array in the producer's document

Concerns:
How will a consumer search for the best producers in a location?