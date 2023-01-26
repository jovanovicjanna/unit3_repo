# Quiz 38

## Code
```.py
import random
import matplotlib.pyplot as plt
random.seed(1234)



class coordinate:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __repr__(self)->str:
        return f"[Coordinate object] x:{self.x}, y:{self.y}"

class city:
    def __init__(self, name:str, location:coordinate):
        self.name = name
        self.location = location

    def __repr__(self)->str:
        return f"[City Object] City {self.name} is located at {self.location}"

    def distance(self, cityB):
        xa, ya = self.location.x, self.location.y
        xb,yb = cityB.location.x, cityB.location.y

        d = ((xa - xb)**2 + (ya - yb)**2) ** (1/2)
        return round(d, 2)

class country:
    def __init__(self, name:str):
        self.name = name
        self.cities = []

    def add_city(self, new_city:city):
        self.cities.append(new_city)

    def __repr__(self)->str:
        return f"[Country Object] The name of the country is {self.name.title()} and it has {len(self.cities)} cities"

point1 = coordinate(x=5, y=5)
print(point1)
Tokyo = city(name="tokyo", location=point1)
Kyoto = city(name="kyoto", location=coordinate(x=10, y=10))

Japan = country(name="Japan")

for name in ["Tokyo", "Yokahoma", "Osaka", "Nagoya", "Sapporo", "Kobe", "Kyoto", "Fukuoka", "Kawasaki", "Saitama"]:
    rand_loc = coordinate(x=random.randint(0, 100), y=random.randint(0,100))
    ct = city(name=name, location = rand_loc)
    Japan.add_city(ct)

# distance from tokyo to any other
for city in Japan.cities:
    d = Japan.cities[0].distance(cityB=city)
    print(f"Distance between {Japan.cities[0].name} and {city.name} is {d}")
    plt.scatter(city.location.x, city.location.y)
    plt.text(city.location.x, city.location.y, city.name)
    plt.xlabel("Latitude(km)")
    plt.ylabel("Longitude(km)")

total_distance = 0
for i in range(0, len(Japan.cities)-1):
    start_city = Japan.cities[i]
    end_city = Japan.cities[i+1]
    x = [start_city.location.x, end_city.location.x]
    y = [start_city.location.y, end_city.location.y]
    plt.plot(x, y, color = "pink")
    d = start_city.distance(cityB=end_city)
    print(f"Connecting {start_city.name} to {end_city.name}: {d}km")
    total_distance += d



print(f"The total distance for this solution of the Salesman's problem is {total_distance}")
plt.show()
```
