
# Exercises on Python classes

## Exercise 1

Write a Python program to create a `Vehicle` class with `name`, `seats` and `trunk_space` instance attributes.

Once you do, this code

<!-- 
```python
class Vehicle:

    def __init__(self, name, seats, trunk_space):
        self.name = name
        self.seats = seats
        self.trunk_space = trunk_space

``` -->

```python
car = Vehicle("Dodge", 2, 1)
print(f'The {car.name} has {car.seats} seats and {car.trunk_space} units of trunk space')
```

should produce this output:

    The Dodge has 2 seats and 1 units of trunk space


## Exercise 2

Add a `__str__` method to the class to that this code

```python
car = Vehicle("Jeep", 4, 2)
print(car)
```

produces this output:

    Jeep

## Exercise 3

Add a method  `at_capacity`, which returns `True` if the Vehicle is overfull and `False` otherwise. The method should take two arguments: `passengers` and `suitcases`. Passengers take up one seat each. Suitcases take up one seat or one trunk space unit - and you cannot put passengers in the trunk.

<!-- 
```python
class Vehicle:

    fuel = 'gasoline'

    def __init__(self, name, seats, trunk_space):
        self.name = name
        self.seats = seats
        self.trunk_space = trunk_space

    def __str__(self):
        return self.name

    def at_capacity(self, people, suitcases):
        seats_left = self.seats - people
        trunk_units_left = self.trunk_space - suitcases
        return seats_left < 0 or seats_left + trunk_units_left < 0

class Bus(Vehicle):

    fuel = 'diesel'

    def at_capacity(self, people, suitcases):
        return people > self.seats or suitcases > self.seats

``` -->

Once you do, this code

```python
car = Vehicle("Volvo", 4, 3)
print(f'It is {car.at_capacity(5, 1)} that the {car.name} is over capacity')
```

should produce this output:

    It is True that the Volvo is over capacity


## Exercise 4

Create a `Bus` class that inherits from the `Vehicle` class. A `Bus` is different from a `Vehicle` in that passengers can sit with a suitcase in their lap, but cannot put any in the trunk. So add an `at_capacity` method that overrides the `Vehicle` method of the same name, so that this difference is taken into account.

Once you do, this code:

```python
school_bus = Bus("School bus", 22, 10)
print(f'The {school_bus.name} has {school_bus.seats} seats and {school_bus.trunk_space} units of trunk space')
print(f'It is {school_bus.at_capacity(22, 11)} that the {school_bus.name} is over capacity')
```

should produce this output:

    The School bus has 22 seats and 10 units of trunk space
    It is False that the School bus is over capacity


## Exercise 5

Define a property that must have the same value for every class instance (object)

Define a class attribute `fuel` to the `Vehicle` and `Bus` classes with a default values `"gasoline"` and `"diesel"`. I.e., Every Bus should use diesel and every Vehicle uses gasoline.

Once you do, this code:

```python
tour_bus = Bus("Dodge", 30, 20)
convertible =  Vehicle("Saab", 4, 1)
print(f'The {tour_bus.name} uses {tour_bus.fuel}')
print(f'The {convertible.name} uses {convertible.fuel}')

```

should produce this output:

    The Dodge uses diesel
    The Saab uses gasoline

## Exercise 6

Look up the `super()` builtin function. What attributes does this class have?

```python
class Truck(Vehicle):

    def __init__(self, name, passengers, trunk_units, trailer_units):
        super().__init__(name, passengers, trunk_units)
        self.trailer_units = trailer_units
```

What will this print:

```python
sixteen_wheeler = Truck('Man', 2, 2, 542)
print(sixteen_wheeler)
```

## Exercise 7

Add a `load` method to this function:

<!-- 
```python
class AutoTransport(Vehicle):

    def __init__(self, name, passengers, trunk_units):
        super().__init__(name, passengers, trunk_units)
        self.loaded_cars = []

    def __str__(self):
        return f"{self.name} with: {', '.join(map(str, self.loaded_cars))}"

    def load(self, car):
        self.loaded_cars.append(car)
```
 -->

```python
class AutoTransport(Vehicle):

    def __init__(self, name, passengers, trunk_units):
        super().__init__(name, passengers, trunk_units)
        self.loaded_cars = []

    def __str__(self):
        return f"{self.name} with: {', '.join(map(str, self.loaded_cars))} loaded"
```

Once you do, this code:

```python
auto_trans = AutoTransport('Man', 2, 2)
auto_trans.load(Vehicle('Mustang', 4, 1))
auto_trans.load(Vehicle('Charger', 4, 1))
auto_trans.load(Vehicle('Corvette', 4, 1))
auto_trans.load(Vehicle('Challenger', 4, 1))
print(auto_trans)

```

should produce this output:

    Man with: Mustang, Charger, Corvette, Challenger loaded

## Exercise 8
Now you have learned a little about classes, you can try to create your own classes. 

Create a class called DNA that takes a string as input. The class should have the following methods:

- `__init__` that takes a string as input and stores it as an attribute
- `count_nucleotides` that counts the number of each nucleotide in the string and returns a dictionary with the counts
- `gc_content` that calculates the GC content of the string and returns the value
- `codons` that returns a list of codons in the string
- `translate` that translates the string into a protein sequence and returns the protein sequence as a string
- `reverse_complement` that returns the reverse complement of the string

A subclass called RNA that inherits from DNA. The RNA class should have the following methods:

- `__init__` that takes a either a DNA string or an RNA string as input and stores it (translated) to/as an RNA string as an attribute
- `reverse_complement` (updated to RNA) that returns the reverse complement of the string
- `codons` (updated to RNA) that returns a list of codons in the string 
- `translate` (updated to RNA; RNA has U instead of T but you can just translate right back to use the old table) that translates the string into a protein sequence and returns the protein sequence as a string.

[command-line-ex]: https://github.com/birc-ctib/command-lines-and-pipes
[intro-to-github-ex]: https://github.com/birc-ctib/intro-to-git-and-github

[w02-prog-ex]: https://github.com/birc-ctib/basic-python
[w02-commandline-ex]: https://github.com/birc-ctib/command-line-python

[w03-merge-ex]: https://github.com/birc-ctib/merging
[w03-guessing-ex]: https://github.com/birc-ctib/guessing
[w03-base-ex]: https://github.com/birc-ctib/changing-base
[w03-sieve-ex]: https://github.com/birc-ctib/sieve
[w03-substring-ex]: https://github.com/birc-ctib/lis
[w03-powerset-ex]: https://github.com/birc-ctib/powerset
[w03-subseq-ex]: https://github.com/birc-ctib/liseq

[w05-bucket-ex]: https://github.com/birc-ctib/bucket-sort

[w06-simple-funcs-ex]: https://github.com/birc-ctib/simple-funcs
[w06-kmers-ex]: https://github.com/birc-ctib/kmer
[w06-codon-ex]: https://github.com/birc-ctib/codon-translation
[w06-reduce-ex]: https://github.com/birc-ctib/reduce

[w07-lists-ex]: https://github.com/birc-ctib/lists-and-recursion

[w09-mm-ex]: https://github.com/birc-ctib/markov

[w11-sllists-ex]: https://github.com/birc-ctib/singly-linked-lists
[w11-dllists-ex]: https://github.com/birc-ctib/doubly-linked-lists

[w12-list-set-ex]: https://github.com/birc-ctib/list-set
[w12-search-tree-set-ex]: https://github.com/birc-ctib/st-balance-1
[w12-hash-table-ex]: https://github.com/birc-ctib/hash-set

[w13-linked-list-stack-ex]: https://github.com/birc-ctib/linked-list-stack
[w13-newick-ex]: https://github.com/birc-ctib/newick
[w13-dllist-queue-ex]: https://github.com/birc-ctib/linked-list-queue

[w14-huffmann-ex]: https://github.com/birc-ctib/huffman
[w14-prim-ex]: https://github.com/birc-ctib/prim
[w14-search-tree-pqueue-ex]: https://github.com/birc-ctib/st-pqueue
[w14-leftist-heap-ex]: https://github.com/birc-ctib/leftist
[w14-binary-heap-ex]: https://github.com/birc-ctib/binary-heap
[w14-heap-sort-ex]: https://github.com/birc-ctib/heap-sort
