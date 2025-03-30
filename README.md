# soc-estimation
# 🔋 Estimating Battery SoC with an Extended Kalman Filter and an Arduino

## Project Overview
This project implements an Extended Kalman Filter (EKF) to estimate the State of Charge (SoC) of a battery. Accurate SoC estimation helps prevent battery degradation and extends battery life. The implementation is based on an Arduino for basic hardware processing and real-time estimation.

## What is an Extended Kalman Filter?
An EKF is a powerful algorithm that combines a physics-based model with a machine learning approach to estimate battery SoC accurately. It is the same principle used in smartphones to determine battery percentage. The algorithm continuously updates its predictions based on past errors, improving accuracy over time.

## Creating the Physics-Based Model
To build the EKF, we first needed to derive equations representing the battery’s physical behavior. This involved:

1. **OCV-SOC Curve Generation**: The battery was discharged from 100% to 0% at a constant low current to create an Open Circuit Voltage (OCV) vs. SoC curve. OCV represents the battery voltage when not connected to a load.
   
2. **Thevenin Equivalent Circuit Model (ECM)**: Since terminal voltage (measurable) differs from OCV, we used an ECM to relate them. The ECM consists of resistors and a capacitor that model the battery’s internal characteristics. To determine the values of R1, R2, and C1, we conducted a pulse discharge test.

### Hardware Setup
The circuit consists of:
- An Arduino for real-time processing
- Sensors for voltage and current measurement
- Battery and discharge circuitry


And here’s the circuit diagram:

![image](https://github.com/user-attachments/assets/bc5d41b6-fe5e-4c78-9b7b-0db249be8241)



Calculations :

![image](https://github.com/user-attachments/assets/0060d195-82ec-4481-923b-966dd575ef26)

![image](https://github.com/user-attachments/assets/e3338443-0165-40f5-868b-6feec4aa1fb1)




## The EKF Algorithm
The EKF works by predicting SoC using:
1. **State Transition Model (f function)**: Uses discharge current, battery efficiency, and other parameters to estimate SoC.
2. **Measurement Model**: Compares the predicted SoC value with the “measured” value derived from voltage readings and the physics-based model.
3. **Kalman Gain Computation**: The algorithm assigns weightings to predictions based on past errors, refining the final SoC estimate.

## Implementation
### Arduino Integration
- The Arduino reads real-time voltage and current sensor data.
- The EKF algorithm runs on the Arduino to update SoC estimates dynamically.

### Software & Tools
- **Microcontroller**: Arduino
- **Languages**: C++ (Arduino IDE)
- **Modeling**: MATLAB for parameter estimation

## How to Use
1. Connect the battery and sensors to the Arduino.
2. Upload the EKF algorithm code to the Arduino.
3. Start the system to begin real-time data acquisition.
4. View the estimated SoC on the output display.

## Future Improvements
- Optimizing the EKF algorithm for faster processing.
- Exploring deep learning models for enhanced accuracy.
- Expanding compatibility with various battery chemistries.


## Contributors
- Sharan Mahajan
- Sanegha Sakhare
- Ojal Jha
- Madhumita


