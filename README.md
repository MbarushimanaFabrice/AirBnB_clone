# AirBnB Clone

## Description
This is a command-line interface (CLI) application that replicates the basic functionality of AirBnB. The project implements a custom command interpreter to manage AirBnB objects, including creating, reading, updating, and deleting instances of various classes. Data is persisted using JSON file storage.

## Command Interpreter

The command interpreter provides a shell-like interface to manage the application's objects. It's built using Python's `cmd` module.

### How to Start
To start the console, run:
```bash
./console.py
```
Or:
```bash
python3 console.py
```

### How to Use
Once started, the console displays a prompt `(hbnb)` where you can enter commands.

#### Available Commands:

- **quit** or **EOF**: Exit the console
- **create**: Creates a new instance of a class
  ```
  (hbnb) create BaseModel
  (hbnb) create User
  ```

- **show**: Displays the string representation of an instance
  ```
  (hbnb) show BaseModel 1234-1234-1234
  ```

- **destroy**: Deletes an instance based on class name and id
  ```
  (hbnb) destroy BaseModel 1234-1234-1234
  ```

- **all**: Displays all instances or all instances of a specific class
  ```
  (hbnb) all
  (hbnb) all BaseModel
  ```

- **update**: Updates an instance by adding or updating an attribute
  ```
  (hbnb) update BaseModel 1234-1234-1234 email "user@example.com"
  ```

### Examples:

```bash
$ ./console.py
(hbnb) create User
3c9b1c9e-6a5f-4b7a-9c8d-1e2f3a4b5c6d
(hbnb) show User 3c9b1c9e-6a5f-4b7a-9c8d-1e2f3a4b5c6d
[User] (3c9b1c9e-6a5f-4b7a-9c8d-1e2f3a4b5c6d) {'id': '3c9b1c9e-6a5f-4b7a-9c8d-1e2f3a4b5c6d', 'created_at': datetime.datetime(2026, 3, 11, 10, 30, 0, 0), 'updated_at': datetime.datetime(2026, 3, 11, 10, 30, 0, 0)}
(hbnb) update User 3c9b1c9e-6a5f-4b7a-9c8d-1e2f3a4b5c6d email "user@example.com"
(hbnb) all User
["[User] (3c9b1c9e-6a5f-4b7a-9c8d-1e2f3a4b5c6d) {'id': '3c9b1c9e-6a5f-4b7a-9c8d-1e2f3a4b5c6d', 'created_at': datetime.datetime(2026, 3, 11, 10, 30, 0, 0), 'updated_at': datetime.datetime(2026, 3, 11, 10, 30, 5, 0), 'email': 'user@example.com'}"]
(hbnb) quit
$
```

## Classes

The project includes the following classes:

### BaseModel
The base class for all other models. Defines common attributes and methods:
- **Attributes:**
  - `id`: Unique identifier (UUID)
  - `created_at`: Datetime when instance is created
  - `updated_at`: Datetime when instance is last updated
- **Methods:**
  - `save()`: Updates the `updated_at` attribute and saves to storage
  - `to_dict()`: Converts instance to dictionary representation

### User
Represents a user of the application.
- **Attributes:**
  - `email`: User's email address
  - `password`: User's password
  - `first_name`: User's first name
  - `last_name`: User's last name

### State
Represents a state/region.
- **Attributes:**
  - `name`: State name

### City
Represents a city.
- **Attributes:**
  - `state_id`: ID of the associated state
  - `name`: City name

### Amenity
Represents an amenity available at a place.
- **Attributes:**
  - `name`: Amenity name

### Place
Represents a rental property/place.
- **Attributes:**
  - `city_id`: ID of the city where the place is located
  - `user_id`: ID of the user who owns the place
  - `name`: Place name
  - `description`: Place description
  - `number_rooms`: Number of rooms
  - `number_bathrooms`: Number of bathrooms
  - `max_guest`: Maximum number of guests
  - `price_by_night`: Price per night
  - `latitude`: Latitude coordinate
  - `longitude`: Longitude coordinate
  - `amenity_ids`: List of amenity IDs

### Review
Represents a review for a place.
- **Attributes:**
  - `place_id`: ID of the place being reviewed
  - `user_id`: ID of the user who wrote the review
  - `text`: Review text

## File Storage

The application uses a JSON file-based storage system (`FileStorage` class) to persist data:
- Objects are serialized to `file.json`
- Objects are deserialized from `file.json` on startup
- All CRUD operations are automatically saved to the file

## Project Structure

```
.
├── console.py              # Command interpreter
├── models/
│   ├── __init__.py        # Initializes storage
│   ├── base_model.py      # BaseModel class
│   ├── user.py            # User class
│   ├── state.py           # State class
│   ├── city.py            # City class
│   ├── amenity.py         # Amenity class
│   ├── place.py           # Place class
│   ├── review.py          # Review class
│   └── engine/
│       ├── __init__.py
│       └── file_storage.py # FileStorage class
└── tests/                 # Unit tests
    └── __init__.py
```

## Requirements
- Python 3.x
- No external dependencies required

## Authors
This project is part of the AirBnB clone series.
