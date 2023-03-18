# Quiz 048

![Screen Shot 2023-03-18 at 17 24 37](https://user-images.githubusercontent.com/111895127/226094400-18431d90-c48d-456c-803e-2735a9b3f451.png)

## Python code

```.py
import sqlite3
from unit3lib import encrypt_password, check_password


class database_handler:
    def __init__(self,namedb:str):
        self.connection = sqlite3.connect(namedb)
        self.cursor = self.connection.cursor()


    def search(self, query):
        result = self.cursor.execute(query).fetchall()
        return result

    def run_save(self, query):
        self.cursor.execute(query)
        self.connection.commit()

    def close(self):
        self.connection.close()



x = database_handler("bitcoin_exchange (1).db")
query = "SELECT * from ledger"
result = x.search(query)
x.close()

end_code = "\033[00m"
green = "\033[0;32m"
red = "\33[0;31m"

for i in result:
    id = i[0]
    sender_id = i[1]
    receiver_id = i[2]
    amount = i[3]
    signature = i[4]
    string = f"id {id},sender_id {sender_id},receiver_id {receiver_id},amount {amount}"

    if check_password(string,signature) == True:
        print(f"{green}Tx id={id} Signature matches{end_code}")
    else:
        print(f"{red}Tx id={id} Error signature{end_code}")
```
## Evidence

![Screen Shot 2023-03-18 at 17 57 32](https://user-images.githubusercontent.com/111895127/226095810-0329d0f9-8aa5-4348-a12b-aa7210c92486.png)
