# BetterMe---Back-End-Qa---Yurii-Mot

<ins>TC-01 - Create pet with valid data types</ins>

Preconditions:
Valid JSON where all fields follow the correct data types:
- id is number
- name is string
- photoUrls is an array of strings
- status is string
- category.id is number
- category.name is string
- tags is an array of objects (id number, name string)

Steps:
Send POST /pet with a valid JSON body.

Expected Result:
- Status code 200 OK.
- Response Content-Type is application/json.
- All returned fields match the expected data types and values that were sent.
- Pet is created successfully.

<ins>TC-02 - id as string instead of number</ins>

Preconditions:
Prepare JSON where id is a string instead of a number.

Steps:
Send POST /pet with id = "123".

Expected Result:
- Status code 4xx validation error is returned.

<ins>TC-03 - name as number instead of string</ins>

Preconditions:
Prepare JSON where name is a number.

Steps:
- Send POST /pet with name = 12345.

Expected Result:
- Status code 4xx validation error is returned.

<ins>TC-04 - photoUrls as string instead of array</ins>

Preconditions:
- Prepare JSON where photoUrls is a string instead of an array.

Steps:
- Send POST /pet with photoUrls = "http://test.com/image.jpg".

Expected Result:
- Status code 4xx validation error is returned.

<ins>TC-05 - photoUrls contains invalid item types</ins>

Preconditions:
Prepare JSON where photoUrls contains non-string values (e.g., numbers or booleans).

Steps:
- Send POST /pet with photoUrls = [123, true].

Expected Result:
- Status code 4xx validation error is returned.

<ins>TC-06 - tags provided as object instead of array</ins>

Preconditions:
Prepare JSON where tags is an object instead of an array.

Steps:
- Send POST /pet with tags = { id: 1, name: "tag1" }.

Expected Result:
- Status code 4xx validation error is returned.

<ins>TC-07 - tags.id as string instead of number</ins>

Preconditions:
Prepare JSON where tags is an array but id inside tag is a string.

Steps:
- Send POST /pet with tags = [{ id: "1", name: "tag1" }].

Expected Result:
- Status code 4xx validation error is returned.
- Nested object type validation should be enforced.

<ins>TC-08 - category.id as string instead of number</ins>

Preconditions:
Prepare JSON where category.id is a string instead of number.

Steps:
- Send POST /pet with category = { id: "10", name: "test" }.

Expected Result:
- 4xx validation error is returned.

<ins>TC-09 - status with invalid data type</ins>

Preconditions:
Prepare JSON where status is not a string (e.g., boolean or number).

Steps:
- Send POST /pet with status = true or status = 123.

Expected Result:
- Status code 4xx validation error is returned.

<ins>TC-10 - Empty JSON body</ins>

Preconditions:
Prepare an empty JSON object {}.

Steps:
- Send POST /pet with an empty body.

Expected Result:
- 200 OK is returned.
- Response Content-Type is application/json.
- Response contains id field with a randomly generated id.
- Pet is created successfully.
- Response structure remains valid JSON.
