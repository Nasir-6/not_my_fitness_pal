
# NotMyFitnessPal

Counting your Calories without judgement.

By Aaron, Marcy, Nasir, Sarina and Suraaj.


## Table of contents
<!--ts-->
* [Project Description](#project-description)
* [Setup Instructions](#setup-instructions)
* [Usage](#usage)
    * [JSON Formats](#json-formats)
    * [Table of HTTP Request Paths](#table-of-http-request-paths)
* [Features in Action](#features-in-action)
  * [Post and Get Request](#post-and-get-request)
  * [Put and Delete Request](#put-and-delete-request)
  * [Further Get Requests](#further-get-requests)
  * [Custom Response Error Messages](#custom-response-error-messages)
* [Tests](#tests)
* [What we learnt](#what-we-learnt)
* [Future Improvements](#future-improvements)
* [Contributors](#contributors)

<!--te-->



## Project Description

A back-end food/calorie tracking API project which gives developers access to basic CRUD functionalities such as adding, deleting, updating and retrieving food entries for a specified user with the aim of it being the foundations for a full-stack calorie tracking application.

This project was built using Java (Spring Boot) and a PostgreSQL database.

This project was the back-end group project as part of the Bright Network Technology Academy - Full Stack Bootcamp (Cohort 4).


## Setup Instructions

1. Clone the Repo: 
```git clone git@github.com:Nasir-6/not_my_fitness_pal.git```
2. Create the not_my_fitness_pal database - refer to the [Database setup queries.md](https://github.com/Nasir-6/not_my_fitness_pal/blob/main/Database%20setup%20queries.md) file (PostgreSQL must be installed) 
3. Open the project using IntelliJ and run the NotMyFitnessPalApplication (It should run on port 8080 unless another application is using this port)


## Usage
#### JSON Formats
Our database consists of two tables; people and food_entries which have the following JSON Formats:

```http
Person:
  { "id": 1, 
    "name": "Bob", 
    "age": 34, 
    "height_in_cm": 177.0, 
    "weight_in_kg": 78.0, 
    "calorie_target": 3000 }

Food_Entry:
  { "id": 20, 
    "person_id": 5, 
    "name": "avocado on toast", 
    "mealType": "BREAKFAST", 
    "notes": "sliced avocado on brown bread", 
    "calories": 200, 
    "week": 1, 
    "day": "TUESDAY" }
```
#### Table of HTTP Request Paths
In order to use the CRUD functionalities, the following HTTP paths are available using the path 
"localhost:8080" appended with the desired HTTP request path:

| HTTP Request Path                               | Request Type | Description                                                     |
|:------------------------------------------------|:-------------|:----------------------------------------------------------------|
| `.../getAllFood `                               | `GET`        | Get All Food Entries                                            |
| `.../food/{id} `                                | `GET`        | Get Food Entries by Food ID                                     |
| `.../food/person/{id} `                         | `GET`        | Get Food Entries By Person's ID                                 |
| `.../food/person/{id}/week/{week} `             | `GET`        | Get Food Entries By Person's Id for a specific Week                        |
| `.../food/person/{id}/week/{week}/day/{day} `   | `GET`        | Get Food Entries By Person's ID for a specific Day of a given Week                |
| `.../food/mealtype/{mealtype} `                 | `GET`        | Get Food Entries By Meal Type                                   |
| `.../food `                                     | `POST`       | Add Food Entry (use Food-Entry JSON excluding ID)               |
| `.../food /{id}`                                | `PUT`        | Update Food Entry By Food ID (use Food-Entry JSON excluding ID) |
| `.../food/{id} `                                | `DELETE`     | Delete Food Entry                                               |
| `.../people `                                   | `GET`        | Get All People                                                  |
| `.../people/{id} `                              | `GET`        | Get Person By Person's ID                                       |
| `.../person `                                   | `POST`       | Add Person (use person JSON excluding ID)                       |
| `.../person/{id} `                              | `DELETE`     | Delete Person By Person's ID                                    |
| `.../person/{id} `                              | `PUT`        | Update Person By Person's ID (use person JSON excluding ID)     |
| `.../food/calorie_goals/week/{week}/day/{day} ` | `GET`        | Get Daily Calories Goal for a given Day of a given Week for all users           |


**Note: Last HTTP Request is a Stretch Goal**

**Server Note: Please ensure the server is running on port 8080 or adjust the port number (8080) to the one you are currently running.**

## Features in action
### Post and Get request
![post and get request in action](https://github.com/Nasir-6/not_my_fitness_pal/blob/main/readme-gifs-images/post_get_demo.gif)
As you can see the last entry in the database has an ID of 28 and a new entry with an ID of 29 is added using the food entry JSON format as the request body. 

Note: The ID (29) is in the request body mainly for demonstration purposes but it is not needed in practice as it is serially generated by the SQL database.

### Put and Delete request
![put and delete request in action](https://github.com/Nasir-6/not_my_fitness_pal/blob/main/readme-gifs-images/put_delete_demo.gif)
Here the new entry with an ID of 29 is updated using the put request (The ID is not required within the request body). It is then deleted using just the ID in the request path.


### Further Get Requests
**By Meal Type**

![get food entries by meal type response](https://github.com/Nasir-6/not_my_fitness_pal/blob/main/readme-gifs-images/meal_type_image.png)

**By Week**

![get food entries by week response](https://github.com/Nasir-6/not_my_fitness_pal/blob/main/readme-gifs-images/by_week_image.jpg)

**By Week by day**

![get food entries by week by day response](https://github.com/Nasir-6/not_my_fitness_pal/blob/main/readme-gifs-images/by_week_by_day_image.jpg)

### Custom Response Error Messages
![error responses in action](https://github.com/Nasir-6/not_my_fitness_pal/blob/main/readme-gifs-images/errors_demo.gif)
Here you can see the various error messages shown to the user letting them know exactly what is wrong with their request. These were created using custom Java Exception classes available in the Spring framework.

## Tests
A huge part of this project was the Test Driven Development of much of the API. All of the person service class aswell as most of the food service class (excluding the stretch goal implementation) was developed using TDD. As shown below a total of 90 tests were written for this application. The test files can be run using the IntelliJ IDE as shown in the images below.

![person service test results](https://github.com/Nasir-6/not_my_fitness_pal/blob/main/readme-gifs-images/person_service_tests.jpg)
![food service test results](https://github.com/Nasir-6/not_my_fitness_pal/blob/main/readme-gifs-images/food_service_tests.jpg)

## What we learnt
- How to plan, structure and develop a Java (SpringBoot) back-end application with a PostgreSQL database
- How to use GitHub for collaboration (using branches and dealing with merge conflicts)
- The benefit and application of Test Driven Development
- Greater understanding of Java testing concepts (mocking, argument captors etc.)
- Implementing custom exception classes

## Future improvements
- Completely integrate/develop/test the calorie target (stretch goal) feature 
- Expand to include exercise data to integrate calories burnt into the API
- Use H2 in memory databases to test DataAccessService Classes

## Contributors

- [Aaron](https://github.com/Aaron-Nazareth)
- [Marcy](https://github.com/mycp98)
- [Nasir](https://github.com/Nasir-6)
- [Sarina](https://github.com/sarinajsal)
- [Suraaj](https://github.com/SuraajL)



