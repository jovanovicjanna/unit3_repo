# Quiz 043

![Screen Shot 2023-03-18 at 14 14 38](https://user-images.githubusercontent.com/111895127/226086331-d4d39be0-5cee-4ae4-9803-516efe7dc1e0.png)

## SQLite

```.sql
CREATE table if not exists Movies(
    id INTEGER PRIMARY KEY,
    name TEXT,
    producer TEXT,
    director TEXT,
    category TEXT,
    budget INTEGER,
    year INTEGER
)

INSERT INTO Movies (name, producer, director, category, budget, year) VALUES ('Pulp Fiction', 'Lawrence Bender', 'Quentin Tarantino', 'crime film', 8500000, 1994);
INSERT INTO Movies (name, producer, director, category, budget, year) VALUES ('The Pursuit of Happyness', 'James Lassiter', 'Gabriele Muccino', 'biographical drama film', 55000000, 2006);
```
## Evidence

![Screen Shot 2023-03-18 at 14 38 44](https://user-images.githubusercontent.com/111895127/226087448-ac8f6ce4-e476-4881-ad9c-f0b94c341941.png)


