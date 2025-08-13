# Biometric Attendance System

## 📌 Overview
The **Biometric Attendance System** is a hardware-software project that uses a **fingerprint sensor** and **Arduino** to automate student attendance marking.  
When a student places their finger on the sensor, their identity is verified and attendance is automatically recorded in an **Excel file** via a Python script.

This system eliminates manual attendance entry, reduces errors, and ensures accurate record keeping.

---

## 🛠️ Features
- Fingerprint-based authentication for students.
- Automatic attendance marking in Excel.
- Real-time data transfer from Arduino to PC via serial communication.
- Secure and accurate identification process.
- Easy to maintain and scalable for more users.

---

## ⚙️ Hardware Components
- **Arduino Uno** (or compatible board)
- **Fingerprint Sensor Module** (R305 or similar)
- **Jumper Wires** & **Breadboard**
- **USB Cable** for Arduino-PC connection

---

## 💻 Software Requirements
- **Arduino IDE**
- **Python 3.x**
- Python Libraries:
  - `pyserial` → for serial communication
  - `openpyxl` → for Excel file handling
- **Excel** (or LibreOffice Calc)

---
## Block Diagram
![Block Diagram](images/block_diagram.png)

**Explanation:**
- **Fingerprint Sensor** → Captures fingerprint and sends data to Arduino.  
- **Arduino Uno** → Compares with stored templates and sends matching ID to PC.  
- **PC (Python Script)** → Updates attendance Excel sheet.  
- **Excel File** → Stores attendance records with date & time.

---

## Flowchart
![Flowchart](images/flowchart.png)

**Explanation:**
1. Start system and initialize hardware.
2. Wait for fingerprint input.
3. Capture and compare fingerprint.
4. If match found → send ID to PC and update Excel.
5. If no match → display error and wait for next input.
6. Repeat for each student.

---
## Working Principle 

1. **System Initialization**  
   - The **Arduino Uno** initializes the **fingerprint sensor** and establishes a **serial communication link** with the PC.  
   - The fingerprint sensor loads the stored **fingerprint templates** of enrolled students.  
   - The Python script on the PC starts and waits for incoming data from the Arduino.

2. **Fingerprint Capture**  
   - A student places their finger on the fingerprint sensor.  
   - The sensor scans the **unique fingerprint pattern** and converts it into a **digital template** internally.

3. **Verification Against Stored Templates**  
   - The fingerprint sensor compares the captured template with those stored in its memory.  
   - If a match is found, the sensor sends the **associated student ID** to the Arduino.

4. **Data Transmission to PC**  
   - The Arduino receives the **student ID** and sends it to the connected PC over **serial communication** (via USB cable).  
   - The data is formatted so that the Python script can interpret it correctly.

5. **Python Script Processing**  
   - The Python script continuously listens to the serial port for incoming data.  
   - When a **student ID** is received, the script opens the **attendance Excel file** (via `openpyxl`).  
   - The script locates the row corresponding to that student’s ID.

6. **Attendance Marking in Excel**  
   - If no attendance record exists for the current date, the script marks the student as **"Present"**.  
   - It also logs the **current date** and **exact time** from the PC clock.  
   - If the student is already marked present, the script skips to avoid duplication.

7. **Record Storage & Security**  
   - The updated Excel file is saved immediately to prevent data loss.  
   - The records remain secure and can be audited at any time.

8. **System Ready for Next Student**  
   - The system returns to the **“Waiting for Fingerprint”** state and is ready for the next scan without restarting.

---

### 📌 Key Advantages
- **High Accuracy** – Fingerprints are unique, eliminating proxy attendance.  
- **Fully Automated** – No manual marking required; updates happen instantly in Excel.  
- **Fast Operation** – From scan to record, the process takes only a few seconds.  
- **Scalable** – More fingerprints can be added easily to support more students.
