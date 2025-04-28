/* # EmployeePayRollSystem
A project develop using java oops and Data Structure And algorithm concepts.
*/
import java.util.ArrayList;
import java.util.Scanner;

abstract class Employee {
    private int id;
    private String name;

    public Employee(String name, int id) {
        this.name = name;
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public int getId() {
        return id;
    }

    public abstract double calculateSalary();

    @Override
    public String toString() {
        return "Employee[name=" + name + " , id=" + id + " , salary=" + calculateSalary() + "]";
    }
}

class FullTimeEmployee extends Employee {
    private double monthlySalary;

    public FullTimeEmployee(String name, int id, double monthlySalary) {
        super(name, id);
        this.monthlySalary = monthlySalary;
    }

    @Override
    public double calculateSalary() {
        return monthlySalary;
    }
}

class PartTimeEmployee extends Employee {
    private int hoursWorked;
    private double hourlyRate;

    public PartTimeEmployee(String name, int id, int hoursWorked, double hourlyRate) {
        super(name, id);
        this.hoursWorked = hoursWorked;
        this.hourlyRate = hourlyRate;
    }

    @Override
    public double calculateSalary() {
        return hoursWorked * hourlyRate;
    }
}

class PayrollSystem {
    private ArrayList<Employee> employeeList;

    public PayrollSystem() {
        employeeList = new ArrayList<>();
    }

    public void addEmployee(Employee employee) {
        employeeList.add(employee);
    }

    public void removeEmployee(int id) {
        Employee employeeToRemove = null;
        for (Employee employee : employeeList) {
            if (employee.getId() == id) {
                employeeToRemove = employee;
                break;
            }
        }
        if (employeeToRemove != null) {
            employeeList.remove(employeeToRemove);
        }
    }

    public void displayEmployee() {
        for (Employee employee : employeeList) {
            System.out.println(employee);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        PayrollSystem payrollSystem = new PayrollSystem();
        Scanner sc = new Scanner(System.in);

        // Full-time Employee Input
        System.out.println("Enter your Full time Employee Name ");
        String nm = sc.nextLine();
        System.out.println("Enter your Full time Employee Id ");
        int ids = sc.nextInt();
        System.out.println("Enter your Full time Employee Salary");
        double sal = sc.nextDouble();
        
        // Fix: Consume the newline character after nextDouble()
        sc.nextLine();
        
        FullTimeEmployee emp1 = new FullTimeEmployee(nm, ids, sal);

        // Part-time Employee Input
        System.out.println("\nEnter your Part time Employee Name ");
        String nm1 = sc.nextLine();
        System.out.println("Enter your Part time Employee id ");
        int id1 = sc.nextInt();
        System.out.println("Enter your Part time Employee how much hours work");
        int wh = sc.nextInt();
        System.out.println("Enter your Part time Employee hourly rate in rupees ");
        double hr = sc.nextDouble();

        // Fix: Consume the newline character after nextDouble()
        sc.nextLine();

        PartTimeEmployee emp2 = new PartTimeEmployee(nm1, id1, wh, hr);
        
        payrollSystem.addEmployee(emp1);
        payrollSystem.addEmployee(emp2);

        System.out.println("Initial Employee Details:");
        payrollSystem.displayEmployee();

        System.out.println("Removing employees:");
        payrollSystem.removeEmployee(2);

        System.out.println("Remaining Employee Details:");
        payrollSystem.displayEmployee();
    }
}
// Source code is decompiled from a .class file using FernFlower decompiler.
class FullTimeEmployee extends Employee {
   private double monthlySalary;

   public FullTimeEmployee(String var1, int var2, double var3) {
      super(var1, var2);
      this.monthlySalary = var3;
   }

   public double calculateSalary() {
      return this.monthlySalary;
   }
}
class PartTimeEmployee extends Employee {
   private int hoursWorked;
   private double hourlyRate;

   public PartTimeEmployee(String var1, int var2, int var3, double var4) {
      super(var1, var2);
      this.hoursWorked = var3;
      this.hourlyRate = var4;
   }

   public double calculateSalary() {
      return (double)this.hoursWorked * this.hourlyRate;
   }
}import java.util.ArrayList;
import java.util.Iterator;

class PayrollSystem {
   private ArrayList<Employee> employeeList = new ArrayList();

   public PayrollSystem() {
   }

   public void addEmployee(Employee var1) {
      this.employeeList.add(var1);
   }

   public void removeEmployee(int var1) {
      Employee var2 = null;
      Iterator var3 = this.employeeList.iterator();

      while(var3.hasNext()) {
         Employee var4 = (Employee)var3.next();
         if (var4.getId() == var1) {
            var2 = var4;
            break;
         }
      }

      if (var2 != null) {
         this.employeeList.remove(var2);
      }

   }

   public void displayEmployee() {
      Iterator var1 = this.employeeList.iterator();

      while(var1.hasNext()) {
         Employee var2 = (Employee)var1.next();
         System.out.println(var2);
      }

   }
}abstract class Employee {
   private int id;
   private String name;

   public Employee(String var1, int var2) {
      this.name = var1;
      this.id = var2;
   }

   public String getName() {
      return this.name;
   }

   public int getId() {
      return this.id;
   }

   public abstract double calculateSalary();

   public String toString() {
      String var10000 = this.name;
      return "Employee[name=" + var10000 + " , id=" + this.id + " , salary=" + this.calculateSalary() + "]";
   }
}


