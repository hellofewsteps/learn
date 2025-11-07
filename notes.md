## 🧰 Read JSON file (and also dynamically update the value if needed) in Your Test:

```java
// Java 11+ style
String jsonBody = Files.readString(Path.of("src/test/resources/bookingData.json"));
// Works in Java 7+
String jsonBody = new String(Files.readAllBytes(Paths.get("src/test/resources/bookingData.json")));

jsonBody = jsonBody.replace("Jim", "John");

given()
    .header("Content-Type", "application/json")
    .body(jsonBody)
.when()
    .post("/booking")
.then()
    .statusCode(200)
    .log().all();
```

✅ This sends the same JSON request — but with `firstname = John` — to your API dynamically.

| **Part**                  | **Meaning**                             |
| ------------------------- | --------------------------------------- |
| `Files.readAllBytes()`    | Reads file content into memory          |
| `Paths.get()`             | Locates the file                        |
| `new String(...)`         | Converts bytes to a readable string     |
| `.replace("Jim", "John")` | Dynamically updates data before sending |

| Method                  | Java Version | Reads Whole File  | Works Inside JAR | Handles Large Files Well | Simplicity |
| ----------------------- | ------------ | ----------------- | ---------------- | ------------------------ | ---------- |
| `Files.readString()`    | 11+          | ✅                | ❌               | ⚠️                       | ⭐⭐⭐⭐   |
| `Files.readAllBytes()`  | 7+           | ✅                | ❌               | ⚠️                       | ⭐⭐⭐     |
| `BufferedReader`        | All          | ❌ (line by line) | ❌               | ✅                       | ⭐⭐       |
| `getResourceAsStream()` | All          | ✅                | ✅               | ⚠️                       | ⭐⭐⭐     |

## Sending File Attachments in Postman and Rest Assured

- Always tell learners that **multipart/form-data** is required for file uploads.

| Feature                | Postman                        | Rest Assured                                   |
| ---------------------- | ------------------------------ | ---------------------------------------------- |
| **Request Type**       | form-data                      | multipart/form-data                            |
| **How to Attach File** | Choose “File” type in Body tab | `.multiPart("key", new File(...))`             |
| **Headers**            | Handled automatically          | Handled automatically                          |
| **Extra Parameters**   | Add as text fields             | Use `.formParam()`                             |
| **Authentication**     | Add in Authorization tab       | Use `.header("Authorization", "Bearer token")` |

```java
given()
    .header("Authorization", "Bearer " + token)
    .multiPart("file", uploadFile)
.when()
    .post("/upload")
.then()
    .statusCode(200);
```

## ✅ Tools / Libraries Used

- **Jackson** — Default JSON serializer/deserializer in _Rest Assured_. [jackson databind]
- **Gson** — Alternative JSON library (developed by Google)
- **JsonPath** — Used for manually parsing JSON when required

# Serialization and Deserialization (in API Testing)

| **Concept**    | **Serialization**                             | **Deserialization** .as(ClassName.Class) |
| -------------- | --------------------------------------------- | ---------------------------------------- |
| **Example**    | `.body(booking)`                              | `.extract().as(Booking.class)`           |
| **Definition** | Converting a Java object → JSON (or XML)      | Converting JSON (or XML) → Java object   |
| **Direction**  | Java ➜ JSON                                   | JSON ➜ Java                              |
| **Used When**  | Sending a request body to an API              | Reading a response body from an API      |
| **Benefit**    | Avoids hardcoded JSON and makes code reusable | Easy to validate API response data       |

# For each POJO:

- Create Claass
  - for each field
    - data type: 'private'
    - constructor - with all fileds. delete super()
    - empty consturctor [empty totally/no field]. delete super()
    - 'toString()' method with all fields

## 🧱 **Maven Basics**

| **Concept**     | **Meaning**                                                                         | **Example / Note**                                       |
| --------------- | ----------------------------------------------------------------------------------- | -------------------------------------------------------- |
| **Group ID**    | Represents the **package name** or organization domain (reverse domain convention). | `com.example.api` → Usually your company or domain name. |
| **Artifact ID** | Represents the **project name** or the name of your module.                         | `restassured-tests`                                      |
| **Version**     | Defines the project’s version.                                                      | `1.0.0`                                                  |
| **Packaging**   | Defines the type of output (jar, war, pom).                                         | `jar`                                                    |

## 🧪 **Rest Assured Overview**

| **Keyword** | **Meaning in BDD style** | **Explanation**                                                           |
| ----------- | ------------------------ | ------------------------------------------------------------------------- |
| `given()`   | **Precondition**         | Setup step — define base URI, headers, request body, authentication, etc. |
| `when()`    | **Action**               | Execute the HTTP request (GET, POST, PUT, DELETE, FETCH).                 |
| `then()`    | **Validation**           | Verify or assert the response (status code, response body, headers).      |

🧠 **Mnemonic:**
Think of **GIVEN → WHEN → THEN** as **Arrange → Act → Assert** in traditional testing.

✅ Example:

```java
given()
   .baseUri("https://restful-booker.herokuapp.com")
   .header("Content-Type", "application/json")
   .body(requestBody)
.when()
   .post("/booking")
.then()
   .statusCode(200)
   .body("booking.firstname", equalTo("Jim"));
```

---

## 🥒 **Cucumber Basics (Gherkin Syntax)**

| **Keyword** | **Meaning**  | **Purpose in Scenario**                     |
| ----------- | ------------ | ------------------------------------------- |
| **Given**   | Precondition | Define the starting state or input setup.   |
| **When**    | Action       | Describe what user or system does.          |
| **Then**    | Verification | Describe the expected outcome or assertion. |

## 📦 **Common Maven Dependencies for API Automation**

| **Purpose**                        | **Library (Dependency)** | **Artifact ID**                                      | **Notes**                                                      |
| ---------------------------------- | ------------------------ | ---------------------------------------------------- | -------------------------------------------------------------- |
| API Testing                        | **Rest Assured**         | `rest-assured`                                       | Core library for HTTP testing.                                 |
| JSON Serialization/Deserialization | **Jackson Databind**     | `jackson-databind`                                   | Converts Java objects ↔ JSON.                                  |
| Test Framework                     | **TestNG**               | `testng`                                             | Supports test execution, grouping, priorities, and assertions. |
| Alternative Test Framework         | **JUnit**                | `junit`                                              | Common in unit testing; Cucumber integrates with it.           |
| BDD Framework                      | **Cucumber**             | `cucumber-java`, `cucumber-junit`, `cucumber-testng` | Enables feature file-based BDD tests.                          |
| Logging (optional)                 | **Log4j / SLF4J**        | `log4j-api`, `slf4j-simple`                          | For logging test execution.                                    |
| JSON Parsing (optional)            | **JsonPath**             | `json-path`                                          | Helps extract values from JSON responses.                      |

---

## 🧭 Quick Recap

| **Tool / Concept** | **Purpose**                     | **Key Idea**                                 |
| ------------------ | ------------------------------- | -------------------------------------------- |
| Maven              | Build & dependency management   | Centralizes library management in `pom.xml`. |
| Rest Assured       | API Automation                  | Fluent BDD-style syntax (`given-when-then`). |
| Cucumber           | BDD Framework                   | Uses human-readable `.feature` files.        |
| Jackson            | Serialization / Deserialization | Converts JSON ↔ Java Objects.                |
| TestNG / JUnit     | Test Execution                  | Run and organize tests efficiently.          |

# Postman | Get Value from One API Response and Pass into Another API Request

[Watch Tutorial on YouTube](https://www.youtube.com/watch?v=5PM4gyE-ZWM)
