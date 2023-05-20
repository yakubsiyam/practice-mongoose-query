# mongoose Practice Aggregation

**Task 1:** Find all users who are located in New York.

```ts
db.personData.find({ "address.city": "New York" });
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
db.personData.find({ "favorites.food": "pizza" }).sort("age");
```

**Task 4**: Find all users over 30 whose favorite color is "green".

```ts
db.personData.find({
  $and: [{ age: { $gt: 30 } }, { "favorites.color": "green" }],
});
```

**Task 5:** Count the number of users whose favorite movie is "The Shawshank Redemption."

```ts
db.personData.find({ "favorites.movie": "The Shawshank Redemption" }).count();
```

**Task 6:** Update the zipcode of the user with the email "**[johndoe@example.com](mailto:johndoe@example.com)**" to "10002".

```ts
db.personData.updateOne(
  { email: "johndoe@example.com" },
  { $set: { "address.zipcode": "10002" } }
);
```

**Task 7:** Delete the user with the email "**[alicewilliams@example.com](mailto:alicewilliams@example.com)**" from the user data.

```ts
db.personData.deleteOne({ email: "alicewilliams@example.com" });
```

**Task 8**: Group users by their favorite movie and retrieve the average age in each movie group.

**Task 9:** Calculate the average age of users with a favorite " pizza " food.

```js
// orders
[
  {
    _id: 1,
    order_number: "ORD-001",
    customer_id: 1,
    total_amount: 100.0,
  },
  {
    _id: 2,
    order_number: "ORD-002",
    customer_id: 2,
    total_amount: 150.0,
  },
  {
    _id: 3,
    order_number: "ORD-003",
    customer_id: 1,
    total_amount: 200.0,
  },
][
  // customers
  ({
    _id: 1,
    name: "Alice Williams",
    email: "alice@example.com",
  },
  {
    _id: 2,
    name: "Bob Anderson",
    email: "bob@example.com",
  },
  {
    _id: 3,
    name: "Emily Davis",
    email: "emily@example.com",
  })
];
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
