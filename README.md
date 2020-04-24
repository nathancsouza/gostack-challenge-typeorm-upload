# bootcamp-gostack-challenge

## 🚀 About the challenge

This will be an application that should store incoming and outgoing financial transactions and allow the registration and listing of these transactions, in addition to allowing the creation of new records in the database by sending a csv file.


## Application routes

- `POST / transactions:` The route must receive title, value, type, and category within the body of the request, with type being the type of the transaction, which should be income for incoming (depositing) and outcome for outgoing (withdrawing). When registering a new transaction, it must be stored within your database, having the fields ` id`, `title`, `value`, `type`, `category_id`, `created_at`, `updated_at`.

```
{
   "id": "uuid",
   "title": "Salary",
   "value": 3000,
   "type": "income",
   "category": "Food"
}
```

- `GET / transactions:` This route should return a listing with all the transactions you have registered so far, together with the sum of the entries, withdrawals and total credit. This route must return an object in the following format:


```
{
  "transactions": [
    {
      "id": "uuid",
      "title": "Salary",
      "value": 4000,
      "type": "income",
      "category": {
        "id": "uuid",
        "title": "Salary",
        "created_at": "2020-04-20T00: 00: 49.620Z",
        "updated_at": "2020-04-20T00: 00: 49.620Z",
      },
      "created_at": "2020-04-20T00: 00: 49.620Z",
      "updated_at": "2020-04-20T00: 00: 49.620Z",
    },
    {
      "id": "uuid",
      "title": "Freela",
      "value": 2000,
      "type": "income",
      "category": {
        "id": "uuid",
        "title": "Others",
        "created_at": "2020-04-20T00: 00: 49.620Z",
        "updated_at": "2020-04-20T00: 00: 49.620Z",
      },
      "created_at": "2020-04-20T00: 00: 49.620Z",
      "updated_at": "2020-04-20T00: 00: 49.620Z",
    },
    {
      "id": "uuid",
      "title": "Invoice payment",
      "value": 4000,
      "type": "outcome",
      "category": {
        "id": "uuid",
        "title": "Others",
        "created_at": "2020-04-20T00: 00: 49.620Z",
        "updated_at": "2020-04-20T00: 00: 49.620Z",
      },
      "created_at": "2020-04-20T00: 00: 49.620Z",
      "updated_at": "2020-04-20T00: 00: 49.620Z",
    },
    {
      "id": "uuid",
      "title": "Gamer Chair",
      "value": 1200,
      "type": "outcome",
      "category": {
        "id": "uuid",
        "title": "Recreation",
        "created_at": "2020-04-20T00: 00: 49.620Z",
        "updated_at": "2020-04-20T00: 00: 49.620Z",
      },
      "created_at": "2020-04-20T00: 00: 49.620Z",
      "updated_at": "2020-04-20T00: 00: 49.620Z",
    }
  ],
  "balance": {
    "income": 6000,
    "outcome": 5200,
    "total": 800
  }
}
```

<ul><li>
DELETE / transactions /: id: The route must delete a transaction with the id present in the route parameters.
</li>
<p>
<li>
POST / transactions / import: The route must allow the import of a file with .csv format containing the same information needed to create a transaction id, title, value, type, category_id, created_at, updated_at, where each line of the CSV file must be a new record for the database, and finally return all transactions that have been imported into your database.
</li>

</ul>

## Testing specification

For this challenge we have the following tests:

- `should be able to create a new transaction:` In order for this test to pass, your application must allow a transaction to be created, and return a json with the created transaction.
<p>

- `should create tags when inserting new transactions:` For this test to pass, your application must allow that when creating a new transaction with a category that does not exist, it is created and inserted in the category_id field of the transaction with the id that was just created.
<p>

- `should not create tags when they already exists:` In order for this test to pass, your application must allow when creating a new transaction with a category that already exists, to be assigned to the category_id field of the transaction with the id of that existing category, not allowing the creation of categories with the same title.
<p>

- `should be able to list the transactions:` In order for this test to pass, your application must allow an array of objects containing all transactions to be returned together with the balance of income, outcome and total transactions that have been created so far.
<p>


- `should not be able to create outcome transaction without a valid balance:` In order for this test to pass, your application should not allow an outcome type transaction to exceed the total amount the user has in cash (total income), returning a response with HTTP 400 code and an error message in the following format: {error: string}.
<p>


- `should be able to delete a transaction:` In order for this test to pass, you must allow your delete route to delete a transaction, and when deleting, it returns an empty response, with status 204.
<p>


- `should be able to import transactions:` For this test to pass, your application must allow a csv file to be imported. With the imported file, you must allow all records and categories that were present in that file to be created in the database, and return all transactions that were imported.

