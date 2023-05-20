# mongoose Practice Aggregation
## Example data:

```js
[
  {
    "name": "John Doe",
    "email": "johndoe@example.com",
    "age": 28,
    "address": {
      "street": "123 Main St",
      "city": "New York",
      "state": "NY",
      "zipcode": "10001"
    },
    "favorites": {
      "color": "blue",
      "food": "pizza",
      "movie": "The Shawshank Redemption"
    },
    "friends": [
      {
        "name": "Jane Smith",
        "email": "janesmith@example.com"
      },
      {
        "name": "Mike Johnson",
        "email": "mikejohnson@example.com"
      }
    ]
  },
  {
    "name": "Alice Smith",
    "email": "alicesmith@example.com",
    "age": 32,
    "address": {
      "street": "456 Elm St",
      "city": "San Francisco",
      "state": "CA",
      "zipcode": "94101"
    },
    "favorites": {
      "color": "green",
      "food": "sushi",
      "movie": "Pulp Fiction"
    },
    "friends": [
      {
        "name": "Bob Anderson",
        "email": "bobanderson@example.com"
      },
      {
        "name": "Emily Davis",
        "email": "emilydavis@example.com"
      }
    ]
  },
  {
    "name": "David Johnson",
    "email": "davidjohnson@example.com",
    "age": 40,
    "address": {
      "street": "789 Oak St",
      "city": "Chicago",
      "state": "IL",
      "zipcode": "60601"
    },
    "favorites": {
      "color": "red",
      "food": "burger",
      "movie": "The Godfather"
    },
    "friends": [
      {
        "name": "Sarah Thompson",
        "email": "sarahthompson@example.com"
      },
      {
        "name": "Michael Brown",
        "email": "michaelbrown@example.com"
      }
    ]
  },
  {
    "name": "Emily Wilson",
    "email": "emilywilson@example.com",
    "age": 27,
    "address": {
      "street": "987 Pine St",
      "city": "Los Angeles",
      "state": "CA",
      "zipcode": "90001"
    },
    "favorites": {
      "color": "purple",
      "food": "tacos",
      "movie": "Inception"
    },
    "friends": [
      {
        "name": "Olivia Davis",
        "email": "oliviadavis@example.com"
      },
      {
        "name": "Noah Thompson",
        "email": "noahthompson@example.com"
      }
    ]
  },
  {
    "name": "Sophia Anderson",
    "email": "sophiaanderson@example.com",
    "age": 35,
    "address": {
      "street": "321 Cedar St",
      "city": "Seattle",
      "state": "WA",
      "zipcode": "98101"
    },
    "favorites": {
      "color": "yellow",
      "food": "pasta",
      "movie": "The Dark Knight"
    },
    "friends": [
      {
        "name": "James Wilson",
        "email": "jameswilson@example.com"
      },
      {
        "name": "Ava Thompson",
        "email": "avathompson@example.com"
      }
    ]
  },
  {
    "name": "Liam Davis",
    "email": "liamdavis@example.com",
    "age": 31,
    "address": {
      "street": "555 Maple St",
      "city": "Denver",
      "state": "CO",
      "zipcode": "80201"
    },
    "favorites": {
      "color": "orange",
      "food": "steak",
      "movie": "The Matrix"
    },
    "friends": [
      {
        "name": "Charlotte Wilson",
        "email": "charlottewilson@example.com"
      },
      {
        "name": "Oliver Smith",
        "email": "oliversmith@example.com"
      }
    ]
  },
  {
    "name": "Mia Thompson",
    "email": "miathompson@example.com",
    "age": 29,
    "address": {
      "street": "222 Oak St",
      "city": "Houston",
      "state": "TX",
      "zipcode": "77001"
    },
    "favorites": {
      "color": "pink",
      "food": "ice cream",
      "movie": "Titanic"
    },
    "friends": [
      {
        "name": "Ethan Davis",
        "email": "ethandavis@example.com"
      },
      {
        "name": "Emma Wilson",
        "email": "emmawilson@example.com"
      }
    ]
  },
  {
    "name": "Oliver Wilson",
    "email": "oliverwilson@example.com",
    "age": 33,
    "address": {
      "street": "777 Elm St",
      "city": "Boston",
      "state": "MA",
      "zipcode": "02101"
    },
    "favorites": {
      "color": "black",
      "food": "chocolate",
      "movie": "Fight Club"
    },
    "friends": [
      {
        "name": "Charlotte Davis",
        "email": "charlottedavis@example.com"
      },
      {
        "name": "William Smith",
        "email": "williamsmith@example.com"
      }
    ]
  },
  {
    "name": "Ava Johnson",
    "email": "avajohnson@example.com",
    "age": 26,
    "address": {
      "street": "444 Pine St",
      "city": "Miami",
      "state": "FL",
      "zipcode": "33101"
    },
    "favorites": {
      "color": "silver",
      "food": "sushi",
      "movie": "The Avengers"
    },
    "friends": [
      {
        "name": "James Davis",
        "email": "jamesdavis@example.com"
      },
      {
        "name": "Charlotte Thompson",
        "email": "charlottethompson@example.com"
      }
    ]
  },
  {
    "name": "William Smith",
    "email": "williamsmith@example.com",
    "age": 30,
    "address": {
      "street": "888 Maple St",
      "city": "Dallas",
      "state": "TX",
      "zipcode": "75201"
    },
    "favorites": {
      "color": "gold",
      "food": "hamburger",
      "movie": "Forrest Gump"
    },
    "friends": [
      {
        "name": "Emma Davis",
        "email": "emmadavis@example.com"
      },
      {
        "name": "Oliver Thompson",
        "email": "oliverthompson@example.com"
      }
    ]
  }
]

```

**Task 1:** Find all users who are located in New York.
```ts
db.personData.find(
    { "address.city": "New York" }
)
```

**Task 2:** Find the user(s) with the email "**[johndoe@example.com](mailto:johndoe@example.com)**" and retrieve their favorite movie.
```ts
db.personData.find(
    { email: "johndoe@example.com" }
).project({
    "favorites.movie": 1
})


// output
{
	"_id" : ObjectId("6468712aa5ae9e0726c52512"),
	"favorites" : {
		"movie" : "The Shawshank Redemption"
	}
}
```

**Task 3:** Find all users with "pizza" as their favorite food and sort them according to age.
```ts
db.personData.find(
    { "favorites.food": "pizza" },
).sort("age")
```

**Task 4**: Find all users over 30 whose favorite color is "green".
```ts
db.personData.find(
    {
        $and: [
            { age: { $gt: 30 } },
            { "favorites.color": "green" }
        ]
    }
)
```

**Task 5:** Count the number of users whose favorite movie is "The Shawshank Redemption."
```ts
db.personData.find(
    { "favorites.movie": "The Shawshank Redemption" },
).count()
```

**Task 6:** Update the zipcode of the user with the email "**[johndoe@example.com](mailto:johndoe@example.com)**" to "10002".

**Task 7:** Delete the user with the email "**[alicewilliams@example.com](mailto:alicewilliams@example.com)**" from the user data.

**Task 8**: Group users by their favorite movie and retrieve the average age in each movie group.

**Task 9:** Calculate the average age of users with a favorite " pizza " food.

```js
// orders
[
  {
    "_id": 1,
    "order_number": "ORD-001",
    "customer_id": 1,
    "total_amount": 100.0
  },
  {
    "_id": 2,
    "order_number": "ORD-002",
    "customer_id": 2,
    "total_amount": 150.0
  },
  {
    "_id": 3,
    "order_number": "ORD-003",
    "customer_id": 1,
    "total_amount": 200.0
  }
]

// customers
[
  {
    "_id": 1,
    "name": "Alice Williams",
    "email": "alice@example.com"
  },
  {
    "_id": 2,
    "name": "Bob Anderson",
    "email": "bob@example.com"
  },
  {
    "_id": 3,
    "name": "Emily Davis",
    "email": "emily@example.com"
  }
]
```

**Task 10:** Perform a lookup aggregation to retrieve the orders data along with the customer details for each order.

## More Tasks on Aggregation

**Task 1:** Group users by their favorite color and retrieve the count of users in each color group.

**Task 2:** Find the user(s) with the highest age.

**Task 3:** Find the most common favorite food among all users.

**Task 4:** Calculate the total count of friends across all users.

**Task 5:** Find the user(s) with the longest name.

**Task 6:** Calculate each state's total number of users in the address field.

**Task 7:** Find the user(s) with the highest number of friends.

These tasks involve using various aggregation operators such as **`$group`**, **`$avg`**, **`$max`**, **`$sum`**, and **`$project`** to perform complex calculations and data transformations. You can write MongoDB aggregation queries to accomplish each task based on user data. Adjust the queries according to your specific implementation and requirements.