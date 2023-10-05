# Exercise 1: Implementing a Basic Observer Pattern

## Overview

The Observer pattern is a behavioral design pattern that allows an object, known as the subject, to maintain a list of its dependents, called observers, and notify them of any state changes, typically by calling one of their methods. This pattern is predominantly used to implement distributed event handling systems, where one object (the subject) changes state and all registered observers are notified and updated automatically.

## Objective

To grasp the fundamentals of the Observer pattern and understand its practical implementation in web applications.

## Pre-requisites

- Basic knowledge of JavaScript and web development.
- A code editor and a browser for testing.

## Task Description

You will be creating a simple notification system using the Observer pattern. The system will consist of a main subject (an event generator) and multiple observers (notification components).

### Step 1: Define the Subject

1. Create a class named `EventGenerator`. This will act as the main subject.
2. The class should have:
   - A private list of observers.
   - A method to add observers to this list.
   - A method to remove observers from this list.
   - A method to notify all the observers.

### Step 2: Define the Observers

1. Create a class named `NotificationComponent`.
2. This class will act as the observer and should have:
   - A method named `update` that will be called when the `EventGenerator` notifies it of a change.

### Step 3: Implement the Interaction

1. Instantiate the `EventGenerator`.
2. Add multiple `NotificationComponent` instances as observers to the `EventGenerator`.
3. Trigger a state change in the `EventGenerator` (e.g., simulate a button click event).
4. On this trigger, the `EventGenerator` should notify all registered observers.
5. Each `NotificationComponent` should then react (e.g., display a message on the screen).

## Expected Outcome

Upon simulating the event on the `EventGenerator`, all the registered `NotificationComponent` instances should display their respective messages, proving that they were all notified of the change in the main subject.

## Evaluation Criteria

1. Correct implementation of the Observer pattern.
2. Successful communication between the `EventGenerator` and all the `NotificationComponent` instances.
3. Dynamic addition and removal of observers.
4. Code cleanliness and modularity.

## Tips

- Think of the `EventGenerator` as a central hub. Any changes here should ripple out to all connected components.
- Ensure that the addition and removal of observers is dynamic, allowing for flexibility.
- Remember, the main aim is to decouple the `EventGenerator` from the `NotificationComponent` classes, so changes in one don’t necessitate changes in the other.

## Conclusion

The Observer pattern is a powerful tool in the world of web applications, especially when dealing with dynamic interactions and real-time updates. Through this exercise, you'll get hands-on experience in setting up a basic Observer system, laying the foundation for more complex implementations in the future.