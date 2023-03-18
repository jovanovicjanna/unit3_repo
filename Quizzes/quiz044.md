# Quiz 044
![Screen Shot 2023-03-18 at 16 17 18](https://user-images.githubusercontent.com/111895127/226091247-104afa40-fd4d-4318-929c-d29160c4e528.png)

## SQLite
```.sql
SELECT "name" from sqlite_master where type = "table";

select count(*) from INHABITANT where gender = "Male" and state = "Friendly";

select avg(gold) from INHABITANT group by villageid;

select count(*) from ITEM where item like "A%";

select job from INHABITANT group by job;

select item from ITEM, INHABITANT where INHABITANT.personid = ITEM.owner and INHABITANT.job = "Herbalist";
```
