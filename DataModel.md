# Data Model

## consumer
```json
{
    "id": "UUID",
    "firstName": "string",
    "lastName": "string",
    "phoneNumber": "string",
    "email": "string",
    "photo": "string",
    "bio": "string",
    "address": {
        "street": "string",
        "city": "string",
        "state": "string",
        "zipCode": "string"
    },
    "rating": 0,
    "dateCreated": "date",
    "dateUpdated": "date"
}
```

## producer
```json
{
    "id": "UUID",
    "firstName": "string",
    "lastName": "string",
    "phoneNumber": "string",
    "email": "string",
    "photo": "string",
    "bio": "string",
    "address": {
        "street": "string",
        "city": "string",
        "state": "string",
        "zipCode": "string"
    },
    "rating": 0,
    "menu": {

    },
    "dateCreated": "date",
    "dateUpdated": "date"
}
```

## foodItem
```json
{
    "id": "UUID",
    "producerId": "UUID",
    "name": "string",
    "description": "string",
    "photo": "string",
    "price": 0.00,
    "rating": 0,
    "portionSize": 0.00,
    "portionUnit": "string",
    "spiceLevel" : 0,
    "dietPreference" : "",
    "allergies" : ["string", "string"],
    "dateCreated": "date",
    "dateUpdated": "date"
}
```

## activeOrder / archivedOrder
```json
{
    "id": "UUID",
    "consumerId": "UUID",
    "producerId": "UUID",
    "messageForProducer": "string",
    "totalPrice": 0.00,
    "status": "string",
    "orderDueDate": "date",
    "orderedFoodItems" : [
        {
            "name": "string",
            "description": "string",
            "photo": "string",
            "price": 0.00,
            "rating": 0,
            "portionSize": 0.00,
            "portionUnit": "string",
            "spiceLevel" : 0,
            "dietPreference" : "",
            "allergies" : ["string", "string"],
            "quantity": 0,
        },
        {
            "..."
        }
    ],
    "dateCreated": "date",
    "dateUpdated": "date"
}
```

## reviewForProducer / reviewForConsumer
```json
{
    "id": "UUID",
    "consumerId": "UUID",
    "producerId": "UUID",
    "title": "string",
    "description": "string",
    "rating": 0,
    "dateCreated": "date",
    "dateUpdated": "date"
}
```

## reviewForFoodItem
```json
{
    "id": "UUID",
    "consumerId": "UUID",
    "foodItemId": "UUID",
    "title": "string",
    "description": "string",
    "rating": 0,
    "dateCreated": "date",
    "dateUpdated": "date"
}
```