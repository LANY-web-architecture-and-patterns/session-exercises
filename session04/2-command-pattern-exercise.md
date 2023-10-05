# Exercise 2: Designing Commands for a Simple Web App

## Overview

The Command pattern is a behavioral design pattern that turns a request into a stand-alone object that contains information about the request, such as the method name, the object that owns the method, and the method parameters. By decoupling sender and receiver objects, the Command pattern allows for parameterization of objects with operations, and the decoupling of operations from their invocation.

## Objective

To understand the encapsulation of actions as command objects and see how they can be used to provide features like undo and redo in web applications.

## Pre-requisites

- Familiarity with JavaScript and Object-Oriented Programming concepts.
- A code editor and a browser for testing.

## Task Description

You will design and implement a basic web app, a todo list, and incorporate commands to perform actions like adding a task, deleting a task, and marking a task as completed.

### Step 1: Define the Command Interface

1. Create an interface (or an abstract class in languages that support it) named `Command`.
2. The interface should define two main methods:
   - `execute()`: This will carry out the command's action.
   - `undo()`: This will revert the action performed by the `execute` method.

### Step 2: Create Concrete Command Classes

1. Create a class `AddTaskCommand` that implements the `Command` interface. This class will handle adding tasks to the todo list.
2. Create a class `DeleteTaskCommand` that implements the `Command` interface. This class will handle the removal of tasks.
3. Create a class `CompleteTaskCommand` that implements the `Command` interface. This class will handle marking tasks as completed.

Each of these classes will need a reference to the main application (todo list) and possibly some additional data, like the task details.

### Step 3: Implement the Todo List

1. Create a class named `TodoList` that will be the receiver in this pattern.
2. This class should have methods corresponding to each of the commands, e.g., `addTask()`, `deleteTask()`, and `completeTask()`.
3. It should also have a history stack to keep track of executed commands, allowing for the undo functionality.

### Step 4: Incorporate Commands in the Application

1. Instantiate the `TodoList`.
2. For each user action (like adding a task), create the corresponding command object (e.g., `AddTaskCommand`), execute it, and push it onto the history stack.
3. Implement an undo button that pops the last command from the history stack and calls its `undo` method.

## Expected Outcome

A functional todo list where tasks can be added, deleted, and marked as completed. Additionally, any action performed should be undoable using the command pattern.

## Evaluation Criteria

1. Correct and clear implementation of the Command pattern.
2. Proper encapsulation of actions as command objects.
3. Successful execution and undoing of commands.
4. Code modularity and readability.

## Tips

- It's essential to keep the commands and the application logic (in `TodoList`) decoupled. The command's `execute` method should simply delegate the action to the appropriate method in `TodoList`.
- Maintain a history stack efficiently. Consider edge cases like what happens when you undo multiple times or if the history stack is empty.

## Conclusion

The Command pattern provides a powerful way to encapsulate actions as objects, making features like undo/redo more manageable and modular. Through this exercise, you'll gain a deeper appreciation for the flexibility and organization that design patterns can introduce into your applications.