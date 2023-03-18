# Quiz 046
![Screen Shot 2023-03-18 at 16 55 06](https://user-images.githubusercontent.com/111895127/226093026-fb89b6b0-3605-4573-98b7-85db903a6ef2.png)

```.py
import sqlite3

haiku = '''Code flows like a stream
Algorithms guide its way
In silence, it solves'''

# connect to the file, if the file doesn't exist, the database file will automatically create
connection = sqlite3.connect("quiz_046.db")
# get the cursor to the database
cursor = connection.cursor()
# create database with table words (query)
query = f"""CREATE TABLE haiku(
    id INTEGER PRIMARY KEY,
    word NOT NULL,
    length integer 
)"""

cursor.execute(query)

for word in haiku.split():
    # insert every word and length in the database
    insert_query = f""" INSERT into haiku(word, length) values("{word}", {len(word)})
    """
    cursor.execute(insert_query)
    connection.commit() # to save
# query the average of all the lengths
average_query=""" SELECT avg(length) from haiku"""

out=cursor.execute(average_query).fetchone()
connection.commit()

# close database

print("average word length is", out)
```
## Evidence

![Screen Shot 2023-03-18 at 16 59 31](https://user-images.githubusercontent.com/111895127/226093275-bc53d3c6-2c36-43eb-a089-a75a003b1353.png)
