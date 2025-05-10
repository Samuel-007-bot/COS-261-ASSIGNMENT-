# COS-261-ASSIGNMENT-
No 1. 
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}

No 2. 
String str1 = new String("Java");
String str2 = new String("Java");

System.out.println(str1 == str2);      // false (different objects)
System.out.println(str1.equals(str2)); // true (same value)

No 4.
import java.util.Scanner;

public class AddNumbers {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter first number: ");
        int num1 = sc.nextInt();
        System.out.print("Enter second number: ");
        int num2 = sc.nextInt();
        int sum = num1 + num2;
        System.out.println("Sum: " + sum);
        sc.close();
    }
}

No 6.
import java.util.Scanner;

public class EvenOdd {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a number: ");
        int num = sc.nextInt();
        System.out.println(num % 2 == 0 ? "Even" : "Odd");
        sc.close();
    }
}

No 7
public class LargestNumber {
    public static void main(String[] args) {
        int a = 10, b = 25, c = 18;
        int largest = (a > b) ? (a > c ? a : c) : (b > c ? b : c);
        System.out.println("Largest: " + largest);
    }
}

No 9
import java.util.Scanner;

public class MultiplicationTable {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a number: ");
        int num = sc.nextInt();
        for(int i = 1; i <= 10; i++) {
            System.out.println(num + " x " + i + " = " + (num * i));
        }
        sc.close();
    }
}

No 11
class Student {
    String name;
    String matricNo;
    double score;

    Student(String name, String matricNo, double score) {
        this.name = name;
        this.matricNo = matricNo;
        this.score = score;
    }

    void displayInfo() {
        System.out.println("Name: " + name);
        System.out.println("Matric No: " + matricNo);
        System.out.println("Score: " + score);
    }
}

public class StudentTest {
    public static void main(String[] args) {
        Student student = new Student("Onwuka", "NSK123", 85.5);
        student.displayInfo();
    }
}

No 12
class MathUtils {
    static int add(int a, int b) {
        return a + b;
    }
    static double add(double a, double b) {
        return a + b;
    }
}

public class OverloadingExample {
    public static void main(String[] args) {
        System.out.println(MathUtils.add(2, 3));    // 5
        System.out.println(MathUtils.add(2.5, 3.5)); // 6.0
    }
}

No 13
class Person {
    String name;

    Person(String name) {
        this.name = name;
    }

    void displayInfo() {
        System.out.println("Name: " + name);
    }
}

class Teacher extends Person {
    String subject;

    Teacher(String name, String subject) {
        super(name);
        this.subject = subject;
    }

    void displayTeacherInfo() {
        displayInfo();
        System.out.println("Subject: " + subject);
    }
}

public class InheritanceExample {
    public static void main(String[] args) {
        Teacher teacher = new Teacher("Mr. Onwuka", "Mathematics");
        teacher.displayTeacherInfo();
    }
}

No 16.
public class HelloWorld {
    public static void main(String[] args) {
        // Variables follow camelCase
        String myName = "Onwuka";
        System.out.println("Hello, " + myName);
    }
}

No 18.
public class Calculator {

    // Reusable add method
    public int add(int a, int b) {
        return a + b;
    }

    // Method for adding three numbers reusing the above add method
    public int addThreeNumbers(int a, int b, int c) {
        return add(add(a, b), c); // DRY in action!
    }

    public static void main(String[] args) {
        Calculator calc = new Calculator();
        int sum = calc.addThreeNumbers(2, 3, 4);
        System.out.println("Sum: " + sum);  // Expected output: Sum: 9
    }
}

No 22.
public class AverageCalculator {
    public double calculateAverage(double a, double b, double c, double d, double e) {
        return (a + b + c + d + e) / 5;
    }

    public static void main(String[] args) {
        AverageCalculator calc = new AverageCalculator();
        // Example test with expected average 3.0 for inputs 1, 2, 3, 4, 5
        double avg = calc.calculateAverage(1, 2, 3, 4, 5);
        System.out.println("Average: " + avg);  // Expected output: Average: 3.0
    }
}

No 25.
/**
 * Calculates the factorial of a non-negative integer.
 *
 * @param n the number for which the factorial is to be computed; must be non-negative
 * @return the factorial of n
 * @throws IllegalArgumentException if n is negative
 */
public static long factorial(int n) {
    if (n < 0) {
        throw new IllegalArgumentException("n must be non-negative");
    }
    long result = 1;
    for (int i = 2; i <= n; i++) {
        result *= i;
    }
    return result;
}

// Sample main method to test the factorial method.
public static void main(String[] args) {
    System.out.println("Factorial of 5: " + factorial(5)); // Expected output: Factorial of 5: 120
}

No 31.
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Student {
    String id;
    String name;
    double grade;

    Student(String id, String name, double grade) {
        this.id = id;
        this.name = name;
        this.grade = grade;
    }

    @Override
    public String toString() {
        return "ID: " + id + ", Name: " + name + ", Grade: " + grade;
    }
}

public class StudentGradesApp {
    static Scanner sc = new Scanner(System.in);
    static List<Student> students = new ArrayList<>();

    public static void main(String[] args) {
        int choice;
        do {
            printMenu();
            choice = Integer.parseInt(sc.nextLine());
            switch(choice) {
                case 1:
                    addStudent();
                    break;
                case 2:
                    updateStudent();
                    break;
                case 3:
                    viewStudents();
                    break;
                case 4:
                    System.out.println("Exiting...");
                    break;
                default:
                    System.out.println("Invalid choice!");
            }
        } while(choice != 4);
        sc.close();
    }

    static void printMenu() {
        System.out.println("\nStudent Grades Management:");
        System.out.println("1. Add Student");
        System.out.println("2. Update Student");
        System.out.println("3. View Students");
        System.out.println("4. Exit");
        System.out.print("Enter your choice: ");
    }

    static void addStudent() {
        System.out.print("Enter student ID: ");
        String id = sc.nextLine();
        System.out.print("Enter student name: ");
        String name = sc.nextLine();
        System.out.print("Enter student grade: ");
        double grade = Double.parseDouble(sc.nextLine());
        students.add(new Student(id, name, grade));
        System.out.println("Student added successfully.");
    }

    static void updateStudent() {
        System.out.print("Enter the student ID to update: ");
        String id = sc.nextLine();
        Student student = null;
        for (Student s : students) {
            if (s.id.equals(id)) {
                student = s;
                break;
            }
        }
        if (student == null) {
            System.out.println("Student not found.");
            return;
        }
        System.out.print("Enter new name (press enter to skip): ");
        String name = sc.nextLine();
        if (!name.isEmpty()) {
            student.name = name;
        }
        System.out.print("Enter new grade (-1 to skip): ");
        double grade = Double.parseDouble(sc.nextLine());
        if (grade >= 0) {
            student.grade = grade;
        }
        System.out.println("Student updated successfully.");
    }

    static void viewStudents() {
        if(students.isEmpty()) {
            System.out.println("No student records available.");
            return;
        }
        System.out.println("\nStudent Records:");
        for (Student s : students) {
            System.out.println(s);
        }
    }
}

No 32
import java.util.Scanner;

public class ATMSimulator {
    static Scanner sc = new Scanner(System.in);
    static double balance = 1000.00;

    public static void main(String[] args) {
        int option;
        do {
            printMenu();
            option = Integer.parseInt(sc.nextLine());
            switch(option) {
                case 1:
                    checkBalance();
                    break;
                case 2:
                    deposit();
                    break;
                case 3:
                    withdraw();
                    break;
                case 4:
                    System.out.println("Exiting ATM Simulator.");
                    break;
                default:
                    System.out.println("Invalid option!");
            }
        } while(option != 4);
        sc.close();
    }

    static void printMenu() {
        System.out.println("\nATM Menu:");
        System.out.println("1. Check Balance");
        System.out.println("2. Deposit");
        System.out.println("3. Withdraw");
        System.out.println("4. Exit");
        System.out.print("Choose an option: ");
    }

    static void checkBalance() {
        System.out.println("Your current balance is: $" + balance);
    }

    static void deposit() {
        System.out.print("Enter amount to deposit: ");
        double amount = Double.parseDouble(sc.nextLine());
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposit successful. New balance: $" + balance);
        } else {
            System.out.println("Invalid deposit amount.");
        }
    }

    static void withdraw() {
        System.out.print("Enter amount to withdraw: ");
        double amount = Double.parseDouble(sc.nextLine());
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawal successful. New balance: $" + balance);
        } else {
            System.out.println("Invalid withdrawal amount or insufficient funds.");
        }
    }
}



