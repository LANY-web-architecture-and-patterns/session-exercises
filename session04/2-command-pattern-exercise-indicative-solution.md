# Designing Commands for a Simple Web App

## 1. Define the Command Interface

```javascript
class Command {
    execute() {}
    undo() {}
}
```

## 2. Create Concrete Command Classes

### AddTaskCommand

```javascript
class AddTaskCommand extends Command {
    constructor(todoList, task) {
        super();
        this.todoList = todoList;
        this.task = task;
    }

    execute() {
        this.todoList.addTask(this.task);
    }

    undo() {
        this.todoList.deleteTask(this.task);
    }
}
```

### DeleteTaskCommand

```javascript
class DeleteTaskCommand extends Command {
    constructor(todoList, task) {
        super();
        this.todoList = todoList;
        this.task = task;
    }

    execute() {
        this.todoList.deleteTask(this.task);
    }

    undo() {
        this.todoList.addTask(this.task);
    }
}
```

### CompleteTaskCommand

```javascript
class CompleteTaskCommand extends Command {
    constructor(todoList, task) {
        super();
        this.todoList = todoList;
        this.task = task;
    }

    execute() {
        this.todoList.completeTask(this.task);
    }

    undo() {
        this.todoList.uncompleteTask(this.task);
    }
}
```

## 3. Implement the Todo List (Receiver)

```javascript
class TodoList {
    constructor() {
        this.tasks = [];
        this.completedTasks = [];
    }

    addTask(task) {
        this.tasks.push(task);
    }

    deleteTask(task) {
        const index = this.tasks.indexOf(task);
        if (index > -1) {
            this.tasks.splice(index, 1);
        }
    }

    completeTask(task) {
        const index = this.tasks.indexOf(task);
        if (index > -1) {
            this.tasks.splice(index, 1);
            this.completedTasks.push(task);
        }
    }

    uncompleteTask(task) {
        const index = this.completedTasks.indexOf(task);
        if (index > -1) {
            this.completedTasks.splice(index, 1);
            this.tasks.push(task);
        }
    }
}
```

## 4. Incorporate Commands in the Application

```javascript
const todoList = new TodoList();

const addCommand = new AddTaskCommand(todoList, "Buy milk");
addCommand.execute();
console.log(todoList.tasks); // ["Buy milk"]

const completeCommand = new CompleteTaskCommand(todoList, "Buy milk");
completeCommand.execute();
console.log(todoList.completedTasks); // ["Buy milk"]

completeCommand.undo();
console.log(todoList.tasks); // ["Buy milk"]
```

In this solution, each concrete command class encapsulates an action and its opposite (for undo). The `TodoList` class contains the primary logic for managing tasks. Commands like `AddTaskCommand`, `DeleteTaskCommand`, and `CompleteTaskCommand` interact with the `TodoList` to perform or undo specific actions. This design ensures that the command pattern's encapsulation principle is adhered to, providing flexibility and a clean separation of concerns.