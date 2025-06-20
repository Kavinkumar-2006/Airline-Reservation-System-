# Airline-Reservation-System-

Creating an **Airline Reservation System using Java** is a great way to apply core programming concepts like OOP (Object-Oriented Programming), file handling, GUI (Graphical User Interface), and possibly databases. Here's a basic project overview, structure, and sample code snippets to get you started.

---

### 🔧 **Project Overview: Airline Reservation System (Java)**

#### 🎯 **Features**

* User Registration/Login
* Search Flights (By source, destination, date)
* Book/Cancel Tickets
* View Booking History
* Admin Panel (Add/Remove Flights)

#### 💻 **Tech Stack**

* **Frontend (GUI)**: Java Swing / JavaFX (optional for console-based)
* **Backend**: Core Java
* **Database**: File-based (for beginner level) or MySQL (for intermediate)

---

### 📁 **Project Structure**

```
AirlineReservationSystem/
│
├── Main.java
├── Flight.java
├── User.java
├── Reservation.java
├── Admin.java
├── Database.java  (for file or DB management)
└── utils/
    └── InputValidator.java
```

---

### 🔑 **Core Classes**

#### 1. `Flight.java`

```java
public class Flight {
    private String flightId;
    private String source;
    private String destination;
    private String date;
    private int seatsAvailable;

    public Flight(String flightId, String source, String destination, String date, int seats) {
        this.flightId = flightId;
        this.source = source;
        this.destination = destination;
        this.date = date;
        this.seatsAvailable = seats;
    }

    // Getters & Setters
    public String getFlightId() { return flightId; }
    public int getSeatsAvailable() { return seatsAvailable; }
    public void bookSeat() { this.seatsAvailable--; }

    // toString() override for display
    public String toString() {
        return flightId + " | " + source + " -> " + destination + " | " + date + " | Seats: " + seatsAvailable;
    }
}
```

#### 2. `User.java`

```java
public class User {
    private String username;
    private String password;
    private List<String> bookings = new ArrayList<>();

    public User(String username, String password) {
        this.username = username;
        this.password = password;
    }

    public boolean checkPassword(String input) {
        return this.password.equals(input);
    }

    public void addBooking(String flightId) {
        bookings.add(flightId);
    }

    public void showBookings() {
        System.out.println("Bookings for " + username + ": " + bookings);
    }
}
```

#### 3. `Main.java`

```java
import java.util.*;

public class Main {
    static List<Flight> flights = new ArrayList<>();
    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {
        // Sample flight
        flights.add(new Flight("AI101", "Delhi", "Mumbai", "2025-06-25", 50));

        while (true) {
            System.out.println("1. View Flights\n2. Book Flight\n3. Exit");
            int choice = sc.nextInt();
            switch (choice) {
                case 1: viewFlights(); break;
                case 2: bookFlight(); break;
                case 3: System.exit(0);
            }
        }
    }

    static void viewFlights() {
        for (Flight f : flights) {
            System.out.println(f);
        }
    }

    static void bookFlight() {
        System.out.print("Enter Flight ID to book: ");
        String id = sc.next();
        for (Flight f : flights) {
            if (f.getFlightId().equals(id) && f.getSeatsAvailable() > 0) {
                f.bookSeat();
                System.out.println("Booking Confirmed!");
                return;
            }
        }
        System.out.println("Flight not found or full.");
    }
}
```

---

### 🧱 Optional Enhancements

* Connect to a **MySQL database** instead of using in-memory lists
* Add **user authentication** (Registration/Login system)
* Implement **GUI** using `JFrame`, `JButton`, `JTextField`, etc.
* Add **Admin login** to manage flights
* Create a **booking receipt** using text files

---

### 📂 Sample Files (If File-Based DB)

* `users.txt` – stores usernames/passwords
* `flights.txt` – stores flight data
* `bookings.txt` – logs user bookings

---

### ✅ Example Use Case

```
Welcome to Airline Reservation System
1. Register
2. Login
3. Search Flights
4. Book Flight
5. View My Bookings
6. Admin Panel
```

---

Would you like:

* A **complete console-based version** of this project?
* A **Java GUI version** using Swing?
* A version **with MySQL integration**?
