# ToDoListApplication-using-Java

1. **Task Class (Abstract)
   - This abstract class serves as the base for different types of tasks (`WorkTask` and `PersonalTask`). 
   - It contains fields for `title`, `deadline`, `priority`, and `isComplete`, along with methods to manage these fields.
   - Encapsulation is demonstrated through private fields and public methods to access and modify these fields.

2. **WorkTask and PersonalTask Classes**:
   - These classes inherit from `Task`, representing specific types of tasks.
   - They do not add any additional behavior or fields but demonstrate inheritance and polymorphism, allowing for the possibility of adding task-specific behavior in the future.

3. **ToDoList Class**:
   - This class manages a collection of `Task` objects. 
   - It provides methods to add, remove, update, and mark tasks as complete. 
   - Additionally, it includes methods for sorting tasks by `deadline` or `priority`, demonstrating polymorphism by sorting using different criteria.

4. **Main Class (ToDoListApplication)**:
   - This class contains the main method and serves as the entry point for the application.
   - It uses a `Scanner` object to interact with the user through a console interface.
   - The user can add tasks, remove them, update tasks, mark them as complete, sort tasks by deadline or priority, and display all tasks.

### Key OOP Concepts Demonstrated:
- **Classes**: `Task`, `WorkTask`, `PersonalTask`, and `ToDoList` are used to organize the application's data and behavior.
- **Inheritance**: `WorkTask` and `PersonalTask` inherit from `Task`, allowing for different types of tasks.
- **Encapsulation**: Fields in the classes are private, with public methods provided for accessing and modifying the data.
- **Polymorphism**: The `sortTasksByDeadline()` and `sortTasksByPriority()` methods demonstrate polymorphism by allowing the same operation (sorting) to be performed differently based on the sorting criteria.

This code provides a foundation for a to-do list application that can be extended with more features or refined further.
