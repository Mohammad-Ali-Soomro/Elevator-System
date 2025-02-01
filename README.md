# Digital Elevator Control System - CE221 Project  
*A Real-Time, Logic-Based Elevator Prototype Built with Digital Circuits*  

---

## 📝 Overview  
This project designs and implements a **fully functional elevator control system** using fundamental digital logic components. The system simulates real-world elevator operations, including **multi-floor navigation**, **user request prioritization**, **real-time floor tracking** (via a 7-segment display), and **directional feedback** (via LEDs). Built with combinational and sequential logic circuits, the prototype demonstrates how digital systems solve practical automation challenges while adhering to strict hardware constraints.  

---

## 🎯 Features  
- **Floor Selection**: Push buttons for requesting floors.  
- **Direction Indicators**: LEDs for "Up," "Down," and "Stop" states.  
- **Real-Time Feedback**: 7-segment display shows current floor.  
- **Sequential Logic**: Smooth transitions between floors using counters and clock pulses (555 Timer).  
- **Emergency Stop**: Dedicated button to halt operations instantly.  
- **Modular Design**: Scalable architecture for future expansion.  

---

## 🔧 Components & Specifications  
| **Component**          | **Specifications**                                                                 |  
|-------------------------|-----------------------------------------------------------------------------------|  
| **7-Segment Display**   | Common cathode, 0.5" digit size, displays floor numbers (0-9).                   |  
| **Push Buttons**        | 5V-12V tactile switches for floor requests and emergency stop.                   |  
| **LEDs**                | Red (2V, 20mA) for "Stop," Green (3V, 20mA) for "Up/Down" direction indicators.  |  
| **4-bit Comparator (4063)** | Compares current floor (binary) with requested floor; determines direction.    |  
| **555 Timer**           | Generates adjustable clock pulses (4.5V-16V) for counter synchronization.        |  
| **8-to-3 Encoder (10165)** | Encodes 8 floor requests into a 3-bit binary output.                           |  
| **Counter (74LS190)**   | Synchronous 4-bit up/down counter (5V, 25MHz) to track floor positions.          |  
| **BCD-to-7-Segment (7447)**| Converts counter output (BCD) to 7-segment display inputs.                      |  
| **Logic Gates**         | AND, OR, NOT, XOR gates for control signal manipulation.                         |  

---

## 🛠️ Circuit Design  
### Logic Flow  
1. **User Input**: Floor request via push button → encoded into 3-bit binary (8-to-3 Encoder).  
2. **Comparison**: 4-bit Comparator checks requested floor against current floor (from Counter).  
   - **A > B**: "Up" LED activates.  
   - **A < B**: "Down" LED activates.  
   - **A = B**: "Stop" LED activates.  
3. **Counter Operation**:  
   - 555 Timer sends clock pulses to 74LS190 Counter.  
   - Counter increments/decrements based on comparator output.  
4. **Display**: BCD-to-7-Segment converter translates counter output to decimal floor number.  

### Key Design Elements  
- **Synchronous Counting**: Ensures precise floor transitions.  
- **Invalid Input Handling**: Circuit constraints prevent undefined BCD states.  
- **Directional Logic**: Comparator outputs drive LED indicators via combinational logic.  

---

## ⚙️ Simulation & Implementation  
### Tools Used  
- **Proteus**: Circuit design and simulation (primary tool).  
- **Logisim/Multisim**: Validation of truth tables and logic diagrams.  
- **Breadboard & ICs**: Physical implementation with 74LS series ICs and LEDs.  

### Steps  
1. **Simulation**:  
   - Designed circuit in Proteus with modular blocks (encoder, comparator, counter).  
   - Validated using truth tables and K-Maps (e.g., comparator logic: `A>B = A·B'`).  
2. **Hardware Assembly**:  
   - Wired components on a breadboard with color-coded connections.  
   - Tested subsystems (e.g., encoder-to-comparator link) before full integration.  
3. **Debugging**:  
   - Resolved invalid BCD states by adding input constraints.  
   - Simplified Proteus wiring using modular design.  

---

## 📊 Results  
- **Successful Operation**: System handles simultaneous floor requests, updates display in real-time, and indicates direction accurately.  
- **Efficiency**: Smooth transitions between floors with <1s delay per floor.  
- **Scalability**: Design supports expansion to 8 floors (3-bit encoding limit).  

---

## 🚧 Challenges & Solutions  
| **Challenge**               | **Solution**                                      |  
|------------------------------|--------------------------------------------------|  
| **3-bit Comparator Unavailable** | Used 4-bit comparator (4063) and masked the 4th bit. |  
| **Invalid BCD Inputs**       | Added logic gates to restrict inputs to 0-7.     |  
| **Proteus Wiring Complexity**| Broke design into modules (encoder, counter, display). |  

---

## 🔮 Future Work  
- **Expand Floors**: Use 4-bit encoding for 16 floors.  
- **Microcontroller Integration**: Add smart scheduling with Arduino/Raspberry Pi.  
- **Safety Features**: Overload sensors, fire alarms, and emergency communication.  
- **Energy Optimization**: Low-power modes during idle states.  

---

 ## 👥 Team  
- **Mohammad Ali** (2023326) - Circuit Design & Simulation  
- **Zohaib Shah** (2023703) - Hardware Assembly & Testing  
- **Moaz Nadeem** (2023322) - Logic Optimization & Documentation  
- **Mumtaz Ali** (2023559) - Component Sourcing & Debugging  

---

## 📚 References  
- **74LS190 Datasheet**: Synchronous counter specifications.  
- **4063 Comparator Guide**: Bitwise comparison logic.  
- **555 Timer Tutorial**: Astable multivibrator configuration.  
- **Digital Logic Fundamentals (Textbook)**: K-Map simplification techniques.  

---

**🌟 Want to replicate or contribute?**
Clone this repo, check the schematics in `/design`, and reach out with questions!  
