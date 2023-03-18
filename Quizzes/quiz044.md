# Quiz 044
![Screen Shot 2023-03-18 at 16 17 18](https://user-images.githubusercontent.com/111895127/226091247-104afa40-fd4d-4318-929c-d29160c4e528.png)

## SQLite
```.sql
SELECT COUNT(*) FROM INHABITANT WHERE gender="Male" AND state="Friendly";
SELECT AVG(gold) FROM INHABITANT GROUP BY villageid;
SELECT COUNT(*) FROM ITEM WHERE item LIKE 'A%';
SELECT job FROM INHABITANT GROUP BY job;
SELECT item FROM ITEM, INHABITANT WHERE INHABITANT.personid = ITEM.owner AND INHABITANT.job = "Herbalist";
```

### How many tables are there in the database?
![Screen Shot 2023-03-18 at 16 32 43](https://user-images.githubusercontent.com/111895127/226091883-070b4910-15de-46e8-b346-fdcb72e6f3f8.png)

### How many Male inhabitants are Friendly?
![Screen Shot 2023-03-18 at 16 27 14](https://user-images.githubusercontent.com/111895127/226091608-a78d8604-3b56-456c-bd67-920eee7d6cc7.png)

### What is the average gold by village?
![Screen Shot 2023-03-18 at 16 28 51](https://user-images.githubusercontent.com/111895127/226091685-1c97d521-02cc-4e25-8319-6bbdec293ace.png)

### How many items are there that start with the letter “A”
![Screen Shot 2023-03-18 at 16 29 24](https://user-images.githubusercontent.com/111895127/226091722-4aea97d8-b69e-46a0-8f76-3341f9c69cb7.png)

### How many different jobs are there?
![Screen Shot 2023-03-18 at 16 30 21](https://user-images.githubusercontent.com/111895127/226091766-af160585-cbd7-4384-b915-b0eca7d53572.png)

### What are the items owned by the herbalists?
![Screen Shot 2023-03-18 at 16 30 48](https://user-images.githubusercontent.com/111895127/226091786-0ac33d81-f1cc-401c-bc6f-7a786ec578f1.png)
