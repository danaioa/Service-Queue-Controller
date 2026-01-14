# Service Queue Controller

## General Description

This project implements a small embedded control system designed to manage a sequential service flow.  
The system models a simple queue mechanism where requests are registered and processed in order.

Interaction with the system is performed through physical inputs, while the current system state is made available through a local network interface.  
All logic is executed locally on the embedded device, without relying on external services.

The project emphasizes control flow design, state consistency, and architectural clarity.

---

## Bill Of Materials (BOM)

| Component | Quantity |
|---------|----------|
| ESP32 Development Board | 1 |
| Push Buttons | 2 |
| LEDs | 2 |
| Resistors (220Ω) | 2 |
| Breadboard | 1 |
| Jumper Wires | Several |
| USB Cable | 1 |

---

## Tutorial Source

Individual examples related to:
- ESP32 digital input handling
- ESP32 HTTP server functionality

These examples were used only as reference for isolated components.

---

## Adaptations and Design Decisions

The final system differs from basic examples through:
- a custom-defined control flow model
- explicit separation between input processing, state evolution, and output representation
- non-blocking execution using task-based design
- clearly defined operational boundaries and behavior

---

## Required Architecture Questions

### Q1 – What is the system boundary?

**System includes:**
- ESP32 microcontroller
- physical control inputs
- LED indicators
- internal queue state logic
- embedded web server

**System excludes:**
- any external computation
- cloud services
- remote processing units

---

### Q2 – Where does intelligence live?

All control logic and decision-making are executed on the ESP32:
- event interpretation
- state updates
- output control
- data preparation for visualization

External devices are used strictly for observation.

---

### Q3 – What is the hardest technical problem?

The main challenge is ensuring deterministic behavior in the presence of asynchronous events:
- simultaneous button interactions
- proper debouncing
- synchronization between control logic and user interface tasks

---

### Q4 – What is the minimum demo?

The minimum valid demonstration consists of:
1. generating a new service request via physical input
2. advancing the service state using a separate control input
3. observing the updated system state through LED indicators and the web interface

Successful execution of these steps validates the system.

---

### Q5 – Why is this not just a tutorial?

This project is not a direct tutorial implementation because:
- the control logic is custom-designed
- system behavior is explicitly defined
- architectural constraints are documented and justified
- multiple execution contexts are coordinated intentionally


ESP32 was selected due to its ability to:
- handle concurrent execution contexts
- support local network communication
- integrate control logic and user interaction within a single device

This choice aligns with the architectural principles discussed in the course.
