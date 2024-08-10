import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.Scanner;

// Abstract Task class
abstract class Task {
    private String title;
    private String deadline;
    private boolean isComplete;
    private int priority;

    public Task(String title, String deadline, int priority) {
        this.title = title;
        this.deadline = deadline;
        this.priority = priority;
        this.isComplete = false;
    }

    public String getTitle() {
        return title;
    }

    public String getDeadline() {
        return deadline;
    }

    public int getPriority() {
        return priority;
    }

    public boolean isComplete() {
        return isComplete;
    }

    public void markComplete() {
        isComplete = true;
    }

    public void markIncomplete() {
        isComplete = false;
    }

    public void setDeadline(String deadline) {
        this.deadline = deadline;
    }

    public void setPriority(int priority) {
        this.priority = priority;
    }
}

// WorkTask class inheriting from Task
class WorkTask extends Task {
    public WorkTask(String title, String deadline, int priority) {
        super(title, deadline, priority);
    }
}

// PersonalTask class inheriting from Task
class PersonalTask extends Task {
    public PersonalTask(String title, String deadline, int priority) {
        super(title, deadline, priority);
    }
}

// ToDoList class
class ToDoList {
    private ArrayList<Task> tasks;

    public ToDoList() {
        tasks = new ArrayList<>();
    }

    public void addTask(Task task) {
        tasks.add(task);
    }

    public void removeTask(String title) {
        tasks.removeIf(task -> task.getTitle().equalsIgnoreCase(title));
    }

    public void updateTask(String title, String newDeadline, int newPriority) {
        for (Task task : tasks) {
            if (task.getTitle().equalsIgnoreCase(title)) {
                task.setDeadline(newDeadline);
                task.setPriority(newPriority);
                break;
            }
        }
    }

    public void markTaskComplete(String title) {
        for (Task task : tasks) {
            if (task.getTitle().equalsIgnoreCase(title)) {
                task.markComplete();
                break;
            }
        }
    }

    public void sortTasksByDeadline() {
        tasks.sort(Comparator.comparing(Task::getDeadline));
    }

    public void sortTasksByPriority() {
        tasks.sort(Comparator.comparingInt(Task::getPriority));
    }

    public void displayTasks() {
        for (Task task : tasks) {
            System.out.println("Title: " + task.getTitle() + ", Deadline: " + task.getDeadline() +
                    ", Priority: " + task.getPriority() + ", Complete: " + task.isComplete());
        }
    }
}

// Main class for testing the system
public class ToDoListApplication {
    public static void main(String[] args) {
        ToDoList toDoList = new ToDoList();
        Scanner scanner = new Scanner(System.in);

        boolean exit = false;

        while (!exit) {
            System.out.println("To-Do List Application");
            System.out.println("1. Add Task");
            System.out.println("2. Remove Task");
            System.out.println("3. Update Task");
            System.out.println("4. Mark Task as Complete");
            System.out.println("5. Sort Tasks by Deadline");
            System.out.println("6. Sort Tasks by Priority");
            System.out.println("7. Display All Tasks");
            System.out.println("8. Exit");
            System.out.print("Choose an option: ");

            int choice = scanner.nextInt();
            scanner.nextLine();  // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter task title: ");
                    String title = scanner.nextLine();
                    System.out.print("Enter deadline (YYYY-MM-DD): ");
                    String deadline = scanner.nextLine();
                    System.out.print("Enter priority (1-10): ");
                    int priority = scanner.nextInt();
                    scanner.nextLine();  // Consume newline
                    System.out.print("Enter task type (1 for Work, 2 for Personal): ");
                    int type = scanner.nextInt();
                    scanner.nextLine();  // Consume newline

                    if (type == 1) {
                        toDoList.addTask(new WorkTask(title, deadline, priority));
                    } else if (type == 2) {
                        toDoList.addTask(new PersonalTask(title, deadline, priority));
                    }
                    System.out.println("Task added.");
                    break;
                case 2:
                    System.out.print("Enter task title to remove: ");
                    title = scanner.nextLine();
                    toDoList.removeTask(title);
                    System.out.println("Task removed.");
                    break;
                case 3:
                    System.out.print("Enter task title to update: ");
                    title = scanner.nextLine();
                    System.out.print("Enter new deadline (YYYY-MM-DD): ");
                    deadline = scanner.nextLine();
                    System.out.print("Enter new priority (1-10): ");
                    priority = scanner.nextInt();
                    scanner.nextLine();  // Consume newline
                    toDoList.updateTask(title, deadline, priority);
                    System.out.println("Task updated.");
                    break;
                case 4:
                    System.out.print("Enter task title to mark as complete: ");
                    title = scanner.nextLine();
                    toDoList.markTaskComplete(title);
                    System.out.println("Task marked as complete.");
                    break;
                case 5:
                    toDoList.sortTasksByDeadline();
                    System.out.println("Tasks sorted by deadline.");
                    break;
                case 6:
                    toDoList.sortTasksByPriority();
                    System.out.println("Tasks sorted by priority.");
                    break;
                case 7:
                    toDoList.displayTasks();
                    break;
                case 8:
                    exit = true;
                    break;
                default:
                    System.out.println("Invalid option. Try again.");
            }
        }

        scanner.close();
    }
}
