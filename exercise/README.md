<h1>
  <span class="headline">FastAPI Unit Testing with Pytest Lab</span>
  <span class="subhead">Exercise</span>
</h1>

**Learning objective:** By the end of this lab, students will be able to expand test coverage for their API, implementing unit tests using Pytest to cover **70-80%** of the `tea` controller's functionality.

## **Lab Overview**

In the previous lesson, you wrote unit tests for:  
✅ Retrieving all teas (`GET /api/teas`)  
✅ Creating a new tea (`POST /api/teas`)

Now, you will **expand your test coverage** by writing additional tests for key API routes. Your goal is to **reach 70-80% test coverage** for the **`tea` controller** by testing a variety of success and failure cases.

The following table outlines the routes in your application:

| Method       | Endpoint                      | Description                          | Auth Required |
| ------------ | ----------------------------- | ------------------------------------ | ------------- |
| **General**  |                               |                                      |               |
| `GET`        | `/`                           | Returns "Hello World!"               | No            |
| **Teas**     |                               |                                      |               |
| `GET`        | `/api/teas`                   | Retrieve a list of all teas          | No            |
| `GET`        | `/api/teas/{tea_id}`          | Retrieve details of a specific tea   | No            |
| `POST`       | `/api/teas`                   | Create a new tea                     | Yes           |
| `PUT`        | `/api/teas/{tea_id}`          | Update an existing tea               | Yes (Owner)   |
| `DELETE`     | `/api/teas/{tea_id}`          | Delete a tea                         | Yes (Owner)   |
| **Comments** |                               |                                      |               |
| `GET`        | `/api/teas/{tea_id}/comments` | Retrieve all comments for a tea      | No            |
| `GET`        | `/api/comments/{comment_id}`  | Retrieve a specific comment          | No            |
| `POST`       | `/api/teas/{tea_id}/comments` | Create a comment on a tea            | No            |
| `PUT`        | `/api/comments/{comment_id}`  | Update a comment                     | No            |
| `DELETE`     | `/api/comments/{comment_id}`  | Delete a comment                     | No            |
| **Users**    |                               |                                      |               |
| `POST`       | `/api/register`               | Register a new user                  | No            |
| `POST`       | `/api/login`                  | Authenticate user and return a token | No            |

## **Your Task**

Modify and expand your existing `test_teas.py` file to include tests for the following scenarios:

✅ **Get a single tea** (`GET /api/teas/{tea_id}`)

- Test retrieving a specific tea by its ID.
- Verify the response contains correct tea details.

✅ **Handle tea not found** (`GET /api/teas/{invalid_id}`)

- Attempt to fetch a non-existent tea and ensure it returns a `404 Not Found`.

✅ **Unauthorized tea creation** (`POST /api/teas`)

- Attempt to create a tea **without authentication** and confirm the API blocks the request.

✅ **Update a tea** (`PUT /api/teas/{tea_id}`)

- Modify an existing tea and verify the response contains the updated data.

✅ **Tea not found for update** (`PUT /api/teas/{invalid_id}`)

- Attempt to update a non-existent tea and confirm it returns a `404 Not Found`.

✅ **Unauthorized update** (`PUT /api/teas/{tea_id}`)

- Attempt to update a tea that belongs to another user and ensure the API rejects it (`403 Forbidden`).

✅ **Delete a tea** (`DELETE /api/teas/{tea_id}`)

- Remove a tea and confirm it is no longer retrievable.

✅ **Tea not found for deletion** (`DELETE /api/teas/{invalid_id}`)

- Attempt to delete a non-existent tea and ensure it returns a `404 Not Found`.

✅ **Unauthorized deletion** (`DELETE /api/teas/{tea_id}`)

- Attempt to delete a tea that belongs to another user and ensure the API rejects it (`403 Forbidden`).

## **Getting Started**

1. **Locate your existing `test_teas.py` file.**

   - Add new test functions inside this file.

2. **Follow the structure of existing tests.**

   - Use `test_app` (your `TestClient`) to send requests.
   - Use `assert` statements to verify responses.
   - Use a `setup` step to create test data where necessary.

3. **Run Your Tests Frequently!**

To run only the tests in `test_teas.py` and check coverage for the tea controller, use the command:

```sh
pipenv run pytest --cov=controllers.teas tests/test_teas.py
```

> This will run only the tests in `test_teas.py` and measure test coverage specifically for `controllers/teas.py`.

4. **Check Your Coverage Report**

After running your tests, a coverage report will be displayed. If your test coverage for `controllers/teas.py` is below **70%**, add more tests to improve it!

### **Submission**

- Once your tests pass and your coverage reaches at least **70%**, you have satisfied the requirements for this lab.

Good luck! 🚀
