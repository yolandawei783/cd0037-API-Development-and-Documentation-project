## GET '/categories'

- Description:Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category.
- Request Arguments: None
- Response:
    - Success: Returns an object with a single key, categories, that contains an object of id: category_string key: value pairs.
    - Example:

    ```json
    {
    "success": true,
    "categories": {
        "1": "Science",
        "2": "Art",
        "3": "Geography",
        "4": "History",
        "5": "Entertainment",
        "6": "Sports"
    }
    }
    ```
## GET '/questions'

- Description: Fetches a list of questions, number of total questions, current category, and categories. Supports pagination.
- Request Arguments:page (optional): The page number for pagination.
- Response:
    - Success: Returns a list of questions, total number of questions, categories, and current category.
    - Example:

    ```json
    {
    "success": true,
    "questions": [
        {
        "id": 1,
        "question": "What is the capital of France?",
        "answer": "Paris",
        "category": 3,
        "difficulty": 2
        },
        ...
    ],
    "total_questions": 100,
    "categories": {
        "1": "Science",
        "2": "Art",
        "3": "Geography",
        "4": "History",
        "5": "Entertainment",
        "6": "Sports"
    },
    "current_category": null
    }
    ```

## DELETE '/questions/<int:question_id>'

- Description: Deletes a question by its ID.
- Request Arguments: None
- Response:
    - Success: Returns the ID of the deleted question, updated list of questions, and total number of questions.
    - Example

    ```json
    {
    "success": true,
    "deleted": 1,
    "questions": [
        {
        "id": 2,
        "question": "What is the capital of Germany?",
        "answer": "Berlin",
        "category": 3,
        "difficulty": 2
        },
        ...
    ],
    "total_questions": 99
    }
    ```
## POST '/questions'

- Description: Creates a new question.
- Request Arguments:
    - question: The question text.
    - answer: The answer text.
    - category: The category ID.
    - difficulty: The difficulty level.
- Response:
    - Success: Returns the ID of the created question, updated list of questions, and total number of questions.
    - Example:

    ```json
    {
    "success": true,
    "created": 101,
    "questions": [
        {
        "id": 101,
        "question": "What is the capital of Italy?",
        "answer": "Rome",
        "category": 3,
        "difficulty": 2
        },
        ...
    ],
    "total_questions": 101
    }
    ```
## POST '/questions/search'

- Description: Searches for questions based on a search term.
- Request Arguments:
    - searchTerm: The search term.
- Response:
    - Success: Returns a list of questions that match the search term and total number of matching questions.
    - Example:

    ```json
    {
    "success": true,
    "questions": [
        {
        "id": 5,
        "question": "What is the title of the book 'The Great Gatsby'?",
        "answer": "The Great Gatsby",
        "category": 4,
        "difficulty": 3
        },
        ...
    ],
    "total_questions": 10,
    "current_category": null
    }
    ```

## GET '/categories/<int:category_id>/questions'

- Description: Fetches questions based on category ID.
- Request Arguments: None
- Response:
    - Success: Returns a list of questions for the specified category and total number of questions in that category.
    - Example:

    ```json
    {
    "success": true,
    "questions": [
        {
        "id": 7,
        "question": "Who painted the Mona Lisa?",
        "answer": "Leonardo da Vinci",
        "category": 2,
        "difficulty": 3
        },
        ...
    ],
    "total_questions": 20,
    "current_category": 2
    }
    ```
## POST '/quizzes'

- Description: Fetches a random question to play the quiz.
- Request Arguments:
    - previous_questions: A list of previously asked question IDs.
    - quiz_category: The category for the quiz.
- Response:
    - Success: Returns a random question that is not in the list of previous questions.
    - Example:

    ```json
    {
    "success": true,
    "question": {
        "id": 10,
        "question": "What is the largest planet in our solar system?",
        "answer": "Jupiter",
        "category": 1,
        "difficulty": 2
    }
    }
    ```

## Error Handlers

- 404 Not Found:

    - Response:
    ```json
    {
    "success": false,
    "error": 404,
    "message": "resource not found"
    }
    ```
- 422 Unprocessable Entity:

    - Response:
    ```json
    {
    "success": false,
    "error": 422,
    "message": "unprocessable"
    }
    ```
- 400 Bad Request:

    - Response:
    ```json
    {
    "success": false,
    "error": 400,
    "message": "bad request"
    }
    ```
