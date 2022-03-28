# To-Do App
This spec outlines all endpoints and resources exposed by the project. It will also outline the schema and structure of the models that should be built and maintained to achieve the behavior.

## API Resources
These are the outward facing REST resources that the API exposes to the client. These may or may not directly correspond to a model:

* **ToDo Item** - A task represents a single to-do item with the due date, complete status, and a description of what needs to be done.


## Data Tables
This is the propose table structure for this API's data store. This does not necessarily relate to the models.

### todoItem:
```
ID - Int (PK, AutoGenerated)
name - String
description - String
dueDate - Date
completed - Boolean
```

## Data Models
These are the model definitions that should be used when building out the data layer of the API. These models would be derived from the table structure with the repository pattern to ease the use of the data for developers.

All fields are by default required in the data model. Optional fields will be marked with `?` in the data type. All collection property are required (non-nullable) and will be empty arrays if relationships do not exist.

### toDoItem
```
Id - Int
name - String
description - String
dueDate - Date
completed - Bool
```

## Endpoints
These are the endpoints that will be defined in the API which expose the desired functionality for the calling/realtime system.

### Fetch All Tasks
---

**Request**:
```
GET /todoItems/
```

Body: None

**Response** - 200 OK

Body:
```
{
    "items": [
        {
            "id": Int,
            "name": String,
            "dueDate": Date
            "completed" - Bool
        }
        {
            "id": Int,
            "name": String,
            "dueDate": Date
            "completed" - Bool
        }
        {
            "id": Int,
            "name": String,
            "dueDate": Date
            "completed" - Bool
        }
    ]
}
```

**Error Codes**:

`404 Not Found` - Cannot retrieve list of tasks.

### Fetch item by ID
---

**Request**:
```
GET /toDoItems?id=Int
```

Body: None

**Response** - 200 OK

Body:
```
{
    "description": String,
}
```

**Error Codes**: 

`404 Not Found` - Cannot get task from this id.


### Add new task
---

**Request**:
```
POST /toDoItems/add
{
    "name": String,
    "description": String,
    dueDate: Date

}
```

**Response** - 204 No Content

Body: None

**Error Codes**:

`409 Conflict` - Name of task already exists in Database.

### Modify Task 
---

**Request**:
```
PUT /toDoItems/modify
Body:
{
    "id": Int,
    "name": String?,
    "description": String?,
    "dueDate": Date?,
    "completed": Boolean?
}
```

**Response** - 200 OK

**Error Codes**:

`404 Not Found` - Task does not exist in the Database.

### Delete Task
---

**Request**:
```
DELETE /toDoItems/remove
Body:
{
    "id": Int
}
```

**Response** - 200 OK

**Error Codes**:
`404 Not Found` - Item does not exist
