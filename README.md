# AirBnB Clone - The Console
The console is the first segment of the AirBnB project at Holberton School that will collectively cover fundamental concepts of higher level programming. The goal of AirBnB project is to eventually deploy our server a simple copy of the AirBnB Website(HBnB). A command interpreter is created in this segment to manage objects for the AirBnB(HBnB) website.

#### Functionalities of this command interpreter:
* Create a new object (ex: a new User or a new Place)
* Retrieve an object from a file, a database etc...
* Do operations on objects (count, compute stats, etc...)
* Update attributes of an object
* Destroy an object

## Table of Content
* [Environment](#environment)
* [Installation](#installation)
* [File Descriptions](#file-descriptions)
* [Usage](#usage)
* [Examples of use](#examples-of-use)
* [Bugs](#bugs)
* [Authors](#authors)
* [License](#license)

## Environment
This project is interpreted/tested on Ubuntu 14.04 LTS using python3 (version 3.4.3)

## Installation
* Clone this repository: `git clone "https://github.com/alexaorrico/AirBnB_clone.git"`
* Access AirBnb directory: `cd AirBnB_clone`
* Run hbnb(interactively): `./console` and enter command
* Run hbnb(non-interactively): `echo "<command>" | ./console.py`

## File Descriptions
[console.py](console.py) - the console contains the entry point of the command interpreter. 
List of commands this console current supports:
* `EOF` - exits console 
* `quit` - exits console
* `<emptyline>` - overwrites default emptyline method and does nothing
* `create` - Creates a new instance of`BaseModel`, saves it (to the JSON file) and prints the id
* `destroy` - Deletes an instance based on the class name and id (save the change into the JSON file). 
* `show` - Prints the string representation of an instance based on the class name and id.
* `all` - Prints all string representation of all instances based or not on the class name. 
* `update` - Updates an instance based on the class name and id by adding or updating attribute (save the change into the JSON file). 

#### `models/` directory contains classes used for this project:
[base_model.py](/models/base_model.py) - The BaseModel class from which future classes will be derived
* `def __init__(self, *args, **kwargs)` - Initialization of the base model
* `def __str__(self)` - String representation of the BaseModel class
* `def save(self)` - Updates the attribute `updated_at` with the current datetime
* `def to_dict(self)` - returns a dictionary containing all keys/values of the instance

Classes inherited from Base Model:
* [amenity.py](/models/amenity.py)
* [city.py](/models/city.py)
* [place.py](/models/place.py)
* [review.py](/models/review.py)
* [state.py](/models/state.py)
* [user.py](/models/user.py)

#### `/models/engine` directory contains File Storage class that handles JASON serialization and deserialization :
[file_storage.py](/models/engine/file_storage.py) - serializes instances to a JSON file & deserializes back to instances
* `def all(self)` - returns the dictionary __objects
* `def new(self, obj)` - sets in __objects the obj with key <obj class name>.id
* `def save(self)` - serializes __objects to the JSON file (path: __file_path)
* ` def reload(self)` -  deserializes the JSON file to __objects

The console currently supports the following commands:
- **create \<class name>**, which will create an object of the class declared by user;
- **show \<class name> \<id>**, which will display the object information if it exists;
- **destroy \<class name> \<id>**, which will delete the object if it exists;
- **all \<class name>**, where the class name input is optional and the console will display all instances, or all instances of a specified object;
- **update \<class name> \<id> \<attribute name> \<attribute value>**, whilch will update an instance attribute of a previously declared object.

Additionally, the console also supports the following command formats:
- **\<class name>.all()**, which will display all instances of the specified class;
- **\<class name>.count()**, whilch will display the number of instances of the specified class;
- **\<class name>.show(\<id>)**, whilch will display the instance with correct id and class;
- **\<class name>.destroy(\<id>)**, which will delete the instance with correct id and class;
- **\<class name>.update(\<id>, \<attribute name>, \<attribute value>)**, which will update an instance of the given class and id with the new attribute;
- **\<class name>.update(\<id>, \<dictionary representation>)**, which will update an instance of the given class and id with a dictionary of key value pairs that will be new attributes for the objects. 
- **\<class name>.create(<key>=<value>) create an instance of the class


## Examples of use
```
vagrantAirBnB_clone$./console.py
(hbnb) help

Documented commands (type help <topic>):
========================================
EOF  all  create  destroy  help  quit  show  update

(hbnb) all MyModel
** class doesn't exist **
(hbnb) create BaseModel
7da56403-cc45-4f1c-ad32-bfafeb2bb050
(hbnb) all BaseModel
[[BaseModel] (7da56403-cc45-4f1c-ad32-bfafeb2bb050) {'updated_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772167), 'id': '7da56403-cc45-4f1c-ad32-bfafeb2bb050', 'created_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772123)}]
(hbnb) show BaseModel 7da56403-cc45-4f1c-ad32-bfafeb2bb050
[BaseModel] (7da56403-cc45-4f1c-ad32-bfafeb2bb050) {'updated_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772167), 'id': '7da56403-cc45-4f1c-ad32-bfafeb2bb050', 'created_at': datetime.datetime(2017, 9, 28, 9, 50, 46, 772123)}
(hbnb) destroy BaseModel 7da56403-cc45-4f1c-ad32-bfafeb2bb050
(hbnb) show BaseModel 7da56403-cc45-4f1c-ad32-bfafeb2bb050
** no instance found **
(hbnb) quit
```

## Bugs
No known bugs at this time. 

## Authors
Alexa Orrico - [Github](https://github.com/alexaorrico) / [Twitter](https://twitter.com/alexa_orrico)  
Jennifer Huang - [Github](https://github.com/jhuang10123) / [Twitter](https://twitter.com/earthtojhuang)
Chigbu Joshua - [Github](https://github.com/yungryce)

Second part of Airbnb: Joann Vuong
## License
Public Domain. No copy write protection. 






## Rest API
Build an API. To implement, run the API module. Current implmentation requires an existing database in mysql. 

Run at the root of the folder
<pre><code>
>>> HBNB_MYSQL_USER=hbnb_dev HBNB_MYSQL_PWD=hbnb_dev_pwd HBNB_MYSQL_HOST=localhost HBNB_MYSQL_DB=hbnb_dev_db HBNB_TYPE_STORAGE=db HBNB_API_HOST=0.0.0.0 HBNB_API_PORT=5000 python3 -m api.v1.app
</code></pre>
Expected response:
<pre><code>
 * Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
...
</code></pre>
A list of all the possible routes and their respective routes are available on Flasgger's application, <a href="http://0.0.0.0:5000/apidocs/">here</a>. 

Input route for specific api request and available route below.

http://0.0.0.0:5000/api/v1/{Route}

| Route                                    | Request            |
|------------------------------------------|--------------------|
| states                                   | [GET, POST]        |
| states/<state_id>                        | [GET, DELETE, PUT] |
| states/<state_id>/cities                 | [GET, POST]        |
| cities/<city_id>                         | [GET, DELETE. PUT] |
| amenities                                | [GET, POST]        |
| amenities/<amenity_ids>                  | [GET, DELETE, PUT] |
| users                                    | [GET, POST]        |
| users/<user_id>                          | [GET, DELETE, PUT  |
| cities/<city_id>/places                  | [GET, POST]        |
| places/<place_id>                        | [GET, DELETE, PUT] |
| places/<place_id>/amenities              | [GET, DELETE]      |
| places/<place_id>/amenities/<amenity_id> | [POST]             |
| places/<place_id>/reviews                | [GET, POST]        |
| reviews/<review_id>                      | [GET, DELETE, PUT] |
| places                                   | [POST]             |



