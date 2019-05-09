class Animal:
    items_animals = []
    items_class = []
    voice = None
    
    
    @classmethod
    def get_class_weight(cls):
        return sum([item.weight for item in cls.items_animals if isinstance(item, cls)])

    @staticmethod
    def get_biggest_animal_weight():
        return max(Animal.items_animals, key=lambda x: x.weight).name


    def __init__(self, name, weight):
        self.name = name
        self.weight = weight
        self.satiety = 'Hungry'
        self.__class__.items_class = self.__class__.items_class + [self]
        Animal.items_animals = Animal.items_animals + [self]

    def feeding(self):
        self.satiety = 'full'
        print('Fed')

    def get_voice(self):
        return self.__class__.voice


class GiveMilkAnimal(Animal):
    bucket = 'empty'

    def get_milk(self):
        self.bucket = 'full'


class Cow(GiveMilkAnimal):
    voice = 'Muuuu'


class Goat(GiveMilkAnimal):
    voice = 'Meeee'


class GiveWoolAnimal(Animal):
    wool = 'lot'

    def cut(self):
        self.wool = 'few'


class Sheep(GiveWoolAnimal):
    voice = 'Beeee'


class CarryEggsAnimals(Animal):
    egg = 0

    def carry_eggs(self):
        self.egg += 1


class Goose(CarryEggsAnimals):
    voice = 'Gagaga'


class Chicken(CarryEggsAnimals):
    voice = 'Kkoko'


class Duck(CarryEggsAnimals):
    voice = 'Crya'


gray, white = Goose('Серый', 3), Goose('Белый', 4)
manka = Cow('Манька', 250)
barash, kud = Sheep('Барашек', 50), Sheep('Кудрявый', 40)
koko, kuka = Chicken('Ко-Ко', 4), Chicken('Кукареку', 5)
rog, kop = Goat('Рога', 30), Goat('Копыта', 25)
kria = Duck('Кряква', 3)


