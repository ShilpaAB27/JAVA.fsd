# JAVA.fsd
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Employee {
    private int id;
    private String name;
    private int age;

    public Employee(int id, String name, int age) {
        this.id = id;
        this.name = name;
        this.age = age;
    }

    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String toString() {
        return "Employee{" +
                "id=" + id +
                ", name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}

public class EmployeeManagement {
    private List<Employee> EmployeeList;
    private int EmployeeIdCounter;

    public EmployeeManagement() {
        EmployeeList = new ArrayList<>();
        EmployeeIdCounter = 1; 
    }

    public void createEmployee(String name, int age) {
        Employee newEmployee = new Employee(EmployeeIdCounter, name, age);
        EmployeeList.add(newEmployee);
        EmployeeIdCounter++;
        System.out.println("Employee added: " + newEmployee);
    }

    public void readEmployee() {
        System.out.println("List of Employee:");
        for (Employee Employee : EmployeeList) {
            System.out.println(Employee);
        }
    }

    public void updateEmployee(int EmployeeId, String newName, int newAge) {
        for (Employee Employee : EmployeeList) {
            if (Employee.getId() == EmployeeId) {
                Employee.setName(newName);
                Employee.setAge(newAge);
                System.out.println("Employee updated: " + Employee);
                return;
            }
        }
        System.out.println("Employee not found with ID: " + EmployeeId);
    }

    public void deleteEmployee(int EmployeeId) {
        for (Employee Employee : EmployeeList) {
            if (Employee.getId() == EmployeeId) {
                EmployeeList.remove(Employee);
                System.out.println("Employee deleted: " + Employee);
                return;
            }
        }
        System.out.println("Employee not found with ID: " + EmployeeId);
    }

    public static void main(String[] args) {
        EmployeeManagement EmployeeManagement = new EmployeeManagement();
        Scanner scanner = new Scanner(System.in);

        EmployeeManagement.createEmployee("Shilpa", 25);
        EmployeeManagement.createEmployee("Alok", 30);
        EmployeeManagement.readEmployee();

        System.out.print("Enter the ID of the Employee to update: ");
        int EmployeeIdToUpdate = scanner.nextInt();
        scanner.nextLine(); 

        System.out.print("Enter the new name for the Employee: ");
        String newName = scanner.nextLine();

        System.out.print("Enter the new age for the Employee: ");
        int newAge = scanner.nextInt();

        EmployeeManagement.updateEmployee(EmployeeIdToUpdate, newName, newAge);
        EmployeeManagement.readEmployee();

        System.out.print("Enter the ID of the Employee to delete: ");
        int EmployeeIdToDelete = scanner.nextInt();

        EmployeeManagement.deleteEmployee(EmployeeIdToDelete);
        EmployeeManagement.readEmployee();

        scanner.close();
    }
}
