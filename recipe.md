# {{PROBLEM}} Multi-Class Planned Design Recipe

## 1. Describe the Problem

As a car owner
So that I can keep a record of details about my tyres
I want to keep track of the tyres individually, by their position on my car

As a car owner
So that I have the two important pieces of data for a tyre
I want to be able to record both tyre pressure and tyre tread depth

As a car owner
So that I have a history of tyre readings
I want to be able to keep a record of historical readings, when those were, as well as current readings

As a car owner
So that I can see the details of my car at a glance
I want to list the tyres' positions, latest readings and when those were


## 2. Design the Class System

_Consider diagramming out the classes and their relationships. Take care to
focus on the details you see as important, not everything. The diagram below
uses asciiflow.com but you could also use excalidraw.com, draw.io, or miro.com_

```
┌────────────────────────────┐
│ Car                        │
│                            │
│ - car.history              │
│ - car.details              │
│ -                          |
│                            │
└───────────┬────────────────┘
            │
            │ owns a list of
            ▼
┌─────────────────────────┐
│ Tyre                    │
│                         │
│ - tyre pressure         │
│ - tread depth           │
│ - tyre position         │
│                         │
└─────────────────────────┘
```

_Also design the interface of each class in more detail._

```python
class Car:
    # User-facing properties:
    #   tracks: tracks historical/current details of pressure/tread depth readings.

    def __init__(self):
        pass # No code here yet

    def historical_readings(self, tyre_pos = None):
        # Parameters:
        #   tyre_pos = Optional argument. Returns info on specified tyre if called. If not, returns all tyre info.
        # Side-effects:
        #   None
        pass # No code here yet

    def latest_readings(self, tyre_pos = None):
        # Parameters:
        #   tyre_pos = Optional argument. Returns info on specified tyre if called. If not, returns all tyre info.
        # Returns:
        #   None
        pass # No code here yet


class Tyre:
    # User-facing properties:
    #  front_right: list containing dictionaries, which hold date, pressure and tread depth key:value pairs. (3 per dictionary, creates new dictionary for each date)
    #  front_left: ^^^^^^ same as above.
    #  back_right: ^^^^^^
    #  back_left: ^^^^^^^

    def __init__(self):
        # Parameters: None
        # Side-effects:
        #   None
        pass # No code here yet

    def tread_depth(self, position, depth, date):
        #Parameters: 3, position of tyre and depth of tread, date
        #Side-effects: adds a dictionary of info to one of the four above lists.
        pass


    def tyre_pressure(self, position, pressure, date):
        #Parameters: 3, tyre position, tyre pressure and date.
        #side-effects: adds a dictionary of info to one of the four above lists.
        pass


```

## 3. Create Examples as Integration Tests

_Create examples of the classes being used together in different situations and
combinations that reflect the ways in which the system will be used._

```python
# EXAMPLE

"""
Given a car, recall historical readings of a tyre in a certain position
"""
car = Car()
tyre_1 = Tyre()
tyre_1.tread_depth('back_left', '5mm', '08/02/2024')
tyre_1.tread_depth('front_left', '7mm', '08/02/2024')
tyre_1.tyre_pressure('back_left', '100', '08/02/2024')
car.latest_readings # => [{'tyre_position': 'back_left', 'tread_depth': '5mm', 'date': '08/02/2024', 'tyre_pressure': '100'}
                         # {'tyre_position': 'front_left', 'tread_depth': '7mm', 'date': '08/02/2024'}



library = MusicLibrary()
track_1 = Track("Carte Blanche", "Veracocha")
track_2 = Track("Synaesthesia", "The Thrillseekers")
library.add(track_1)
library.add(track_2)
library.tracks # => [track_1, track_2]
```

## 4. Create Examples as Unit Tests

_Create examples, where appropriate, of the behaviour of each relevant class at
a more granular level of detail._

```python
# EXAMPLE

"""
Given a car, recall the most recent readings of a tyre in a certain position
"""
track = Track("Carte Blanche", "Veracocha")
track.title # => "Carte Blanche"
```

_Encode each example as a test. You can add to the above list as you go._

## 5. Implement the Behaviour

_After each test you write, follow the test-driving process of red, green,
refactor to implement the behaviour._
