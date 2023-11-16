# Simple_Python_DB_Connector

Python module for simple connection and editing of databases.

## Installation

To install the python module, enter the following code in the terminal. Remember, "python" must be swapped with the Python interpreter installed on your system:

```sh
python -m pip install simple-db-connector
```

## Usage Example

### Call Database Class

First of all, we call the "database" class. Im using the os modul to call my database parameter from my environment variables. I advise you to do this straight away, as it is very bad to have sensitive data such as passwords and IP addresses in plain text:

```python
import  os
from  simple_db_connector  import  database

# Call the database class
db  =  database(
	os.environ["db_url"],
	os.environ["db_user"],
	os.environ["db_password"],
	os.environ["db_port"],
	os.environ["db_name"],
)
```

After we have called the class, we can also use the functions of the class. All functions are self-explanatory. Nevertheless, I will briefly explain the use of each function:

### _class_ database.check_table

##### Parameter

> table name: _string_

```python
# Example Table Name
table_name = "test_table"

# if "test_table" exists return true, otherwise return false
print(db.check_table(table_name))
```

> It is also executed within the create_table function, so it is not necessary to execute this before you create a table.

### _class_ database.create_table

##### Parameter

> table name: _string_, table content: _dict_

```python
# Example Table Name
table_name = "cars_table"

# Example Table Content
table_content = {
	"manufacture" : "toyota",
	"model" : "Aygo X play",
	"ps" : 72,
}

# Example Table creation
db.create_table(table_name, table_content):
```

> This will create the table "cars_table" with the information contained in "test_content". In addition, a primary key field with the name "ID" will be created too. Currently this field is hard coded with a GUID field. In the near future, however, it will be possible to declare your own primary key field.

### _class_ database.check_db_entry

##### Parameter

> table: _string_, search_parameter: _dict_

```python
# Example Table Name
table_name =  "cars_table"

# Example Search Parameter
search_parameter =  {
	"manufacture"  :  "toyota"
}

# Example Table creation
db.check_db_entry(table_name, search_parameter):
```

> This will create the table "cars_table" with the information contained in "test_content". In addition, a primary key field with the name "ID" will be created too. Currently this field is hard coded with a GUID field. In the near future, however, it will be possible to declare your own primary key field.

```python
# Example Table Name
table_name =  "cars_table"

# Example Search Parameter
search_parameter =  {
	"manufacture"  :  "toyota"
	"model" : "Aygo X play",
}

# Example Table creation
db.check_db_entry(table_name, search_parameter):
```

> It's also possible to have multiple search parameter

### _class_ database.create_db_entry

##### Parameter

> table: _string_, data: _dict_, prime*key: \_string*; \*default value = "id"

```python
# Example Table Name
table_name =  "cars_table"

# Example Table Content
table_content = {
	"manufacture" : "toyota",
	"model" : "Aygo X play",
	"ps" : 72,


}

# Example Table prime key
prime_key = "ID"
# To illustrate this, I have entered "ID". However, if "prime_key" is empty, "ID" is selected.

# Example
db.create_db_entry(table_name, table_content, prime_key):
```

### _class_ database.get_db_entrys

##### Parameter

> table: _string_, search*parameter: \_dict*

```python
# Example Table Name
table_name =  "cars_table"

# Example Search Parameter
search_parameter =  {
	"manufacture"  :  "toyota"
}

# Example Table creation
db.get_db_entrys(table_name, search_parameter):
```

```python
# Example Table Name
table_name =  "cars_table"

# Example Search Parameter
search_parameter =  {
	"manufacture"  :  "toyota"
	"model" : "Aygo X play",
}

# Example Table creation
db.get_db_entrys(table_name, search_parameter):
```

> As with check_db_entry, it is also possible to use several search parameters here

### _class_ database.update_entry

##### Parameter

> table: _string_, search*parameter: \_dict*, update*parameter \_dict*

```python
# Example Table Name
table_name =  "cars_table"

# Example Search Parameter
search_parameter =  {
	"manufacture"  :  "toyoat"
}
# Example Update Parameter
search_parameter =  {
	"manufacture"  :  "toyota"
}

# Example Table creation
db.update_entry(table_name, search_parameter):
```

```python
# Example Table Name
table_name =  "cars_table"

# Example Search Parameter
search_parameter =  {
	"manufacture"  :  "toyoat"
	"model" : "Aygo X yalp",
}
# Example Update Parameter
search_parameter =  {
	"manufacture"  :  "toyota"
	"model" : "Aygo X play",
}

# Example Table creation
db.update_entry(table_name, search_parameter):
```

> It's also possible to use multiple search and update parameter here
