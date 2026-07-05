# Sumo Robot: Object-Oriented C++ Architecture 🤖

## 📌 Project Overview
This project upgrades a standard Arduino-based Sumo Robot by refactoring its software architecture into a clean, Object-Oriented Programming (OOP) design[cite: 1]. 

**The Problem:** In standard Arduino projects, logic is typically crammed into the `setup()` and `loop()` functions, resulting in messy, repeated, and hard-to-maintain code[cite: 1]. 
**The Solution:** This project utilizes C++ OOP principles—specifically **Encapsulation, Abstraction, Composition, and Modularity**—to create a scalable, easily updatable robot control system[cite: 1].

**Contributors:** Talal Arshad Abbasi[cite: 1].

---

## 🏗️ Software Architecture & Class Design

Instead of raw pin manipulation, this system is divided into modular classes with strict responsibilities:

### 1. `Motor` Class (Encapsulation)
*   **Purpose:** Represents a single DC motor[cite: 1].
*   **Logic:** Stores pin numbers as private variables to protect internal implementation, while providing simple public methods like `forward()`, `backward()`, and `stop()`[cite: 1]. 
*   **Benefit:** Eliminates repetitive `digitalWrite()` commands throughout the main codebase[cite: 1].

### 2. `MotorDriver` Class (Composition & Abstraction)
*   **Purpose:** Controls both motors synchronously[cite: 1]. 
*   **Logic:** This class is composed of two `Motor` objects (left and right)[cite: 1]. It abstracts the movement logic so the user only needs to call high-level functions such as `moveForward()`, `moveBackward()`, `turnLeft()`, and `turnRight()`[cite: 1].
*   **Benefit:** The main program does not need to know which specific motor spins in which direction to execute a turn[cite: 1].

### 3. `Robot` Class (Modularity)
*   **Purpose:** Acts as the central "brain" of the robot[cite: 1].
*   **Logic:** Contains the `MotorDriver` object and maps high-level directional commands ('F', 'B', 'L', 'R') to actual physical movements via functions like `goForward()`[cite: 1].
*   **Benefit:** Completely separates hardware-level logic from the robot's high-level behavior, making it easy to integrate sensors in the future[cite: 1].

### 4. `Bluetooth Controller` Class
*   **Purpose:** Manages wireless smartphone communication[cite: 1].
*   **Logic:** Reads incoming characters via Bluetooth and passes the command to the `Robot` class[cite: 1].
*   **Benefit:** Decouples the communication protocol from the movement logic, drastically improving code readability[cite: 1].

---

## 🚀 Why This Design Matters
By implementing this architecture, the final codebase is:
*   **Cleaner & Reusable:** Functions can be exported and reused in future robotics projects[cite: 1].
*   **Easy to Debug:** Hardware faults are isolated to specific classes (e.g., if Bluetooth fails, only the `Bluetooth Controller` class needs debugging)[cite: 1].
*   **Expandable:** New hardware (like ultrasonic or IR sensors) can be added as isolated classes without breaking the existing motor logic[cite: 1].

---
*Note: To see the robot in action, refer to the included video files demonstrating the Bluetooth-controlled directional movement.*
