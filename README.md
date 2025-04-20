# AirBnB Clone - RESTful API

![AirBnB Logo](https://i.imgur.com/QiU1LdE.png)

## Project Overview

This is the third phase of the AirBnB clone project where we implement a RESTful API. The project now includes:

1. **Command Line Interface**: Console for managing objects
2. **Data Models and Storage Engines**: File-based and database persistence 
3. **RESTful API**: HTTP interface for programmatic access to data

## Technology Stack

| Category | Technologies |
|----------|-------------|
| **Backend** | Python 3.4.3, Flask |
| **Database** | MySQL, SQLAlchemy ORM |
| **API** | RESTful architecture, JSON, CORS |
| **Storage** | JSON File Storage, MySQL Database |
| **Documentation** | Swagger/Flasgger |
| **Testing** | unittest framework |

## Installation

1. Clone the repository:
```bash
git clone "https://github.com/username/AirBnB_clone_v3.git"
cd AirBnB_clone_v3
```

2. Setup MySQL database (if using db storage):
```bash
cat setup_mysql_dev.sql | mysql -u root -p
```

## Usage

### Starting the API Server

Run the API with database storage:
```bash
HBNB_MYSQL_USER=hbnb_dev HBNB_MYSQL_PWD=hbnb_dev_pwd HBNB_MYSQL_HOST=localhost \
HBNB_MYSQL_DB=hbnb_dev_db HBNB_TYPE_STORAGE=db HBNB_API_HOST=0.0.0.0 \
HBNB_API_PORT=5000 python3 -m api.v1.app
```

Or with file storage:
```bash
HBNB_TYPE_STORAGE=file HBNB_API_HOST=0.0.0.0 HBNB_API_PORT=5000 python3 -m api.v1.app
```

### API Documentation

Interactive API documentation is available at:
```
http://0.0.0.0:5000/apidocs/
```

### API Endpoints

| Endpoint | Methods | Description |
|----------|---------|-------------|
| `/api/v1/status` | GET | Returns API status |
| `/api/v1/stats` | GET | Returns count of objects by type |
| `/api/v1/states` | GET, POST | List all states or create a new state |
| `/api/v1/states/<state_id>` | GET, DELETE, PUT | Manage a specific state |
| `/api/v1/states/<state_id>/cities` | GET, POST | List cities in a state or create a new city |
| `/api/v1/cities/<city_id>` | GET, DELETE, PUT | Manage a specific city |
| `/api/v1/amenities` | GET, POST | List all amenities or create a new amenity |
| `/api/v1/amenities/<amenity_id>` | GET, DELETE, PUT | Manage a specific amenity |
| `/api/v1/users` | GET, POST | List all users or create a new user |
| `/api/v1/users/<user_id>` | GET, DELETE, PUT | Manage a specific user |
| `/api/v1/cities/<city_id>/places` | GET, POST | List places in a city or create a new place |
| `/api/v1/places/<place_id>` | GET, DELETE, PUT | Manage a specific place |
| `/api/v1/places/<place_id>/amenities` | GET, DELETE | List or remove amenities from a place |
| `/api/v1/places/<place_id>/amenities/<amenity_id>` | POST | Add an amenity to a place |
| `/api/v1/places/<place_id>/reviews` | GET, POST | List reviews for a place or create a new review |
| `/api/v1/reviews/<review_id>` | GET, DELETE, PUT | Manage a specific review |
| `/api/v1/places_search` | POST | Search for places based on criteria |

### Console Usage

The console is still available for managing objects:

```bash
./console.py
```

Console commands:
* `create <class>` - Create an object
* `show <class> <id>` - Show an object
* `destroy <class> <id>` - Delete an object
* `all [class]` - Show all objects or objects of a class
* `update <class> <id> <attribute> <value>` - Update an object
* `quit/EOF` - Exit the console

Alternative syntax:
* `<class>.all()` - List all instances of class
* `<class>.count()` - Count instances of class
* `<class>.show(<id>)` - Show instance with ID
* `<class>.destroy(<id>)` - Delete instance with ID
* `<class>.update(<id>, <attribute>, <value>)` - Update instance
* `<class>.update(<id>, <dictionary>)` - Update instance with dictionary
* `<class>.create(<key>=<value>)` - Create instance with attributes

## Project Structure

* `api/` - API implementation
  * `v1/` - API version 1
    * `views/` - API route handlers
    * `app.py` - Flask application
* `models/` - Data models
  * `engine/` - Storage engines
* `tests/` - Unit tests

## Storage Enhancements

For v3, the storage engines (`DBStorage` and `FileStorage`) have been extended with:
* `get(cls, id)` - Retrieves an object by class and ID
* `count(cls=None)` - Counts objects in storage, optionally filtered by class

## Authors
See the list of [contributors](./AUTHORS) who participated in this project.

## License
This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](./LICENSE) file for details.