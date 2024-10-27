import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Patient {
    String name;
    int age;
    String ailment;

    Patient(String name, int age, String ailment) {
        this.name = name;
        this.age = age;
        this.ailment = ailment;
    }

    @Override
    public String toString() {
        return name + " (" + age + ") - " + ailment;
    }
}

class Hospital {
    private List<Patient> patients;

    Hospital() {
        patients = new ArrayList<>();
    }

    void addPatient(Patient patient) {
        patients.add(patient);
    }

    void showPatients() {
        for (Patient patient : patients) {
            System.out.println(patient);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Hospital hospital = new Hospital();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("1. Add Patient");
            System.out.println("2. Show Patients");
            System.out.println("3. Exit");
            System.out.print("Enter choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline

            if (choice == 1) {
                System.out.print("Enter patient name: ");
                String name = scanner.nextLine();
                System.out.print("Enter patient age: ");
                int age = scanner.nextInt();
                scanner.nextLine(); // Consume newline
                System.out.print("Enter patient ailment: ");
                String ailment = scanner.nextLine();

                Patient patient = new Patient(name, age, ailment);
                hospital.addPatient(patient);
            } else if (choice == 2) {
                hospital.showPatients();
            } else if (choice == 3) {
                break;
            } else {
                System.out.println("Invalid choice. Try again.");
            }
        }

        scanner.close();
    }
}
