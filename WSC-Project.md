# WSC Project

## Python

### sqlite3

SQLite is a C library that provides a lightweight disk-based database that doesn't require a separate server process and allows accessing the database using a nonstandard variant of the SQL query language. In the project, we decide to use sqlite3 to handle the data of the users.

#### Intro

~~~python
import sqlite3

con = sqlite3.connect('./test.db')
~~~

The code above is to create the data storage in the file, *test.db*. The variable, *con*, will connect this data file, letting us to handle and change the data. We can choose to store in the heap memory using the following variable:

~~~python
con = sqlite3.connect(':memory:')
~~~

Then, we need to create an object called, *cursor*. The method **.execute()** could execute SQL code, manipulate the data storage.

~~~python
cur = conn.cursor()
~~~

#### Create the data table

~~~python
sql_data = '''CREATE TABLE user_data
           (name TEXT,
            email TEXT,
            term TEXT,
            course_field TEXT,
            course_number NUM);'''
cur.execute(sql_data)
~~~

#### Input the data

~~~python
data_text = "INSERT INTO user_data VALUES('Eric','kangyuf2@illinois.edu','SP2022', 'CS', '225')"
cur.execute(data_text)
~~~

Or, we can use array to insert mutiple data.

~~~python
#data is the array of tuple with data
cur.executemany('INSERT INTO user_data VALUES (?,?,?,?,?)', data)
~~~

#### Commit

After we input data into storeage, it will not update until we commit the change. Using

~~~python
conn.commit()
~~~

#### Search the data storage

~~~python
cur.execute("SELECT * FROM user_data WHERE name=='Eric'")
cur.fetchall()
#output: [('Eric', 'kangyuf2@illinois.edu', 'SP2022', 'CS', 225)]
~~~

#### Close the data storage

We need to close the cursor and the connection. Using

~~~python
cur.close()
conn.close()
~~~



