# python-finalls
## 1) დაწერეთ პროგრამა რომელიც მიიღებს სტრიქონების მასივს და დაითვლის რამდენი ელემენტია ისეთი, რომლის სიგრძეც არის 2 ან მეტი და მისი პირველი და ბოლო სიმბოლოები ერთმანეთს ემთხვევა.
მაგ: ['abc','xyc','aba','1221',] მასივისთვის პროგრამამ უნდა დააბრუნოს პასუხი 2.
```py
def counting(arr):
    count = 0
    for x in arr:
        if len(x) >= 2 and x[0] == x[-1]:
            count += 1
    return count
my_arr = ['abc', 'xyc', 'aba', '1221']
changed = counting(my_arr)
print(changed) 
```
## 2) დაწერეთ პროგრამა რომელიც მიიღებს სტრიქონს და შეუცვლის მაღალი რეგისტრის  სიმბოლოებს დაბალი რეგისტრებით და პირიქით.
მაგ: Python Exercises - სტრიქონისთვის
უნდა დააბრუნოს pYTHON eXERCOSES.
```py
def change_letter(my_string):
    str = ""
    for char in my_string:
        if char.islower():
            str += char.upper()
        elif char.isupper():
            str += char.lower()
        else:
            str += char
    return str

my_string = input()
changed = change_letter(my_string)
print(changed)
```
## 3) დაწერეთ პროგრამა რომელიც ციკლის მეშვეობით ააგებს შემდეგ გამოსახულებას:

1 <br>
22 <br>
333 <br>
4444 <br>
55555 <br>
666666 <br>
7777777 <br>
88888888 <br>
999999999 <br>
```py
for i in range(10):
    print(f"{i}"*i)
```
## 4) დაწერეთ ფუნქცია რომელსაც გადაეცემა ორი  dictionary და გააერთიანებს მათ. მათი მნიშვნელობები უნდა წარმოადგინოთ მასივის სახით.
მაგ:
{'w':50,'x':100,'y':'Green','z':400}
{'x':300,'y':'Red','z':600}
ამ ორი dictionary-სთვის ფუნქციამ უნდა დააბრუნოს შემდეგი:
{'w':50,'x':[100,300],'y':['Green','Red'],'z':[400,600]}

```py
def objects(obj1, obj2):
    changed = {}
    
    for indexes in set(obj1) | set(obj2):
        index1 = obj1.get(indexes)
        index2 = obj2.get(indexes)
        
        if index1 is not None and index2 is not None:
            changed[indexes] = [index1, index2]
        elif index1 is not None:
            changed[indexes] = [index1]
        elif index2 is not None:
            changed[indexes] = [index2]
    
    return changed


obj1 = {'w': 50, 'x': 100, 'y': 'Green', 'z': 400}
obj2 = {'x': 300, 'y': 'Red', 'z': 600}

changed = objects(obj1, obj2)
print(changed)
```

## 5) შექმენით Vehicle კლასი, რომელსაც გადაეცემა ფერი, კარებების რაოდენობა და ტიპი. ყველა პარამეტრს უნდა ქონდეს getter და  setter მეთოდები. drive მეთოდი რომელიც თუ ფერია blue და ტიპია car, დააბრუნებს სტრიქონს: "I'm driving a blue car!"

ასევე შექმენით მისი შვილობილი კლასი car, რომელიც დამატებით მიიღებს price და tank პარამეტრებს.
უნდა ქონდეს drive მეთოდი რომელიც დააბრუნებს
მსგავსი ტიპის სტრიქონს: "I'm driving a Black Sedan that costs 500$ and has 20 liters in tank".
add_tank მეთოდი, რომელიც მიღებულ რიცხვს დაუმატებს პარამეტრს.
sub_tank მეთოდი, რომელიც მიღებულ რიცხვს გამოაკლებს პარამეტრს.
თუმცა მისი მნიშვნელობა 0-ის ქვემოთ არ უნდა ჩამოვიდეს.
მეთოდი __eq__, რომელიც შეადერებს ორ მანქანას და დააბრუბნებს True-ს თუ
ისინი ემთხვევიან, წინააღმდეგ შემთხვევაში დააბრუნებს False-ს.
```py
class Vehicle(object):
    def __init__(self):
        self.color = ""
        self.doorAmount = 0
        self.type = ""
    
    def setColor(self, _color):
        self.color = _color
    
    def setDoorAmount(self, _amount):
        self.doorAmount = _amount
    
    def setType(self, _type):
        self.type = _type
    
    def getColor(self):
        return self.color.lower()
    
    def getAmount(self):
        return self.doorAmount
    
    def getType(self):
        return self.type.lower()
    
    def drive(self):
      return "I'm driving a " + self.getColor() + " " + self.getType() + "!"

class Car(Vehicle):
    def __init__(self):
        Vehicle.__init__(self)
        self.price = 0
        self.tank = 0
    
    def setPrice(self, _price):
        self.price = _price
    
    def setTank(self, _tank):
        self.tank = _tank
    
    def add_tank(self, _add):
        self.tank += _add
    
    def sub_tank(self, _sub):
        temp = self.tank - _sub
        
        if temp < 0:
            self.tank = 0
    
    def getTank(self):
        return self.tank
    
    def getPrice(self):
        return self.price
    
    def drive(self):
        return "I'm driving a " + self.getColor() + " " + self.getType() + " that costs " + str(self.getPrice()) + "$ and has " + str(self.getTank()) + " liters in tank."
    
    def __eq__(self, other):
        if self.getType() == other.getType() and self.getColor() == other.getColor() and self.getAmount() == other.getAmount() and self.getTank() == other.getTank() and self.getPrice() == other.getPrice():
            return True
        return False

obj1 = Car()
obj2 = Car()

obj1.setType("car")
obj1.setColor("red")
obj1.setDoorAmount(4)
obj1.setTank(20)
obj1.setPrice(50)
print(obj1.drive())
obj2.setType("car")
obj2.setColor("red")
obj2.setDoorAmount(4)
obj2.setTank(20)
obj2.setPrice(50)
print(obj2.drive())
print(obj1 == obj2)
```

## 6) ჩაიწერეთ datascience_salaries.csv ფაილი. წაიკითხეთ მონაცემები ფაილიდან, გამოითვალეთ და დაბეჭდეთ Senior, Mid, Entry დონეებისთვის რომელ ქვეყანაშია ყველაზე მაღალი საშუალო ხელფასი. პროგრამამ უნდა დაბეჭდოს შემდეგნაირად: გამოცდილების დონე - ლოკაცია - საშუალო ხელფასი.


# ქვევით მოცემულია მაგალითი თუ როგორ უნდა დაიწეროს ეს დავალება ზუსტად არ არის დაწერილი !
```py
import csv

hotel_data = {}
higher_than_1k = []
lower_than_1k = []

with open("./ski_hotels.csv", "r") as file:
    csv_reader = csv.DictReader(file)

    for row in csv_reader:
        if int(row["altitude (m)"]) > 1000:
            higher_than_1k.append(row["resort"])
        else:
            lower_than_1k.append(row["resort"])

        if row["country"] in hotel_data:
            hotel_data[row["country"]]["price_total"] += int(row["price (£)"])
            hotel_data[row["country"]]["amount_encountered"] += 1
        else:
            hotel_data[row["country"]] = {
                "price_total": int(row["price (£)"]),
                "amount_encountered": 1,
            }

country_averages = {}
for country, data in hotel_data.items():
    country_averages[country] = data["price_total"] / data["amount_encountered"]
```
