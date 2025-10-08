# Test case catalogue

The following table documents every test case that is executed within the Postman collection. The naming matches the request titles in [`collections/swagger-petstore.postman_collection.json`](../collections/swagger-petstore.postman_collection.json).

| Folder | Request | Description | Assertions |
| --- | --- | --- | --- |
| Pets | Create pet | Generates a new pet with a random identifier and persists it for dependent scenarios. | * Response status is 200.<br>* The `id` in the response equals the generated `petId`.<br>* The response echoes the requested `status` and `name` fields. |
| Pets | Get pet by id | Fetches the pet created in the previous step. | * Response status is 200.<br>* Response payload contains the expected `id` and `name`. |
| Pets | Update pet status | Updates the pet to the `pending` status. | * Response status is 200.<br>* Response payload reflects the new `status`. |
| Store | Place order | Places a store order for the pet and saves the generated order identifier. | * Response status is 200.<br>* Response contains the `orderId` and references the `petId`. |
| Store | Get order by id | Retrieves the order created previously. | * Response status is 200.<br>* Response payload contains the expected `orderId` and `petId`. |
| Store | Delete order | Deletes the order to tidy up data. | * Response status is 200 or 204. |
| Users | Create user | Creates a unique user for login and retrieval flows. | * Response status is 200.<br>* Response message echoes the generated `username`. |
| Users | Login user | Authenticates with the generated user credentials. | * Response status is 200.<br>* Response message contains a session token indicator. |
| Users | Get user by username | Retrieves the user profile created earlier. | * Response status is 200.<br>* Response payload contains the expected `username` and `email`. |
| Cleanup | Delete pet | Removes the created pet to avoid polluting the demo service. | * Response status is 200, 204, or 404 to account for eventual consistency. |

## Execution order

Requests are ordered to respect dependencies. Pet creation happens first, followed by store order actions that depend on the pet, then user flows, and finally cleanup activities.
