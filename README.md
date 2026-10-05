# Industrial Automation & PLC-Based Control Systems

Design and integration of industrial automation and PLC-based control systems for concrete batching and industrial process operations. The work covers PLC programming, HMI interfaces, sensor integration, industrial communication and real-time monitoring, with the aim of accurate, safe and efficient plant operation, remote monitoring and centralised control.

**Author:** Mohammed Mahyoub · [Portfolio](https://mahyoub88.github.io/)

![Industrial Automation & PLC-Based Control Systems: project poster](img/00_project_poster.jpg)

## At a glance

| Aspect | Detail |
|---|---|
| Main application | Concrete batching plant control |
| Controllers | PLC (Siemens / Modicon / Delta) with digital and analog I/O modules |
| Operator interface | HMI panels (Weintek / Siemens / Delta) |
| Supervision | SCADA / WinCC monitoring, alarms, trends and historical logs |
| Communication | RS485 / Modbus, Industrial Ethernet |
| Field devices | Level, pressure, flow, proximity and weight sensors; motors, valves, cylinders and pumps |
| Tools | TIA Portal / STEP 7, Unity Pro, WPLSoft / ISPSoft, WinCC, AutoCAD Electrical |

## Key features

- PLC-based process automation
- Concrete batching control system
- Real-time monitoring and control
- HMI / operator interface panels
- Sensor and actuator integration
- Industrial communication modules
- Alarm and safety management
- Data acquisition and process logging
- Scalable, modular system design

## 1. Control system architecture

The system is organised in four levels. Field sensors and actuators are wired to the PLC's I/O modules in the control panel. The PLC runs the sequences, interlocks and timing. HMI panels give operators set-points, recipes and manual or automatic modes, and SCADA supervises the whole process with alarms, trends and historical records. Safety logic lives in the PLC, so the plant stays safe even if the supervisory level or the network fails.

![Control system architecture: field, control, operator interface and supervision levels](img/01_control_architecture.svg)

## 2. Concrete batching sequence

Each batch follows the same automated sequence: the operator selects a recipe, the PLC doses aggregates, cement, water and admixture, the load cells check every material against its target, the mixer runs for the set time, and the discharge gate empties the mixer into the truck. The PLC checks conditions before every step and stops the sequence with an alarm on any fault.

![Concrete batching sequence: recipe, dose, weigh, mix, discharge, with the checks between steps](img/02_batching_sequence.svg)

## 3. Project workflow

1. Process requirements analysis
2. System design and architecture
3. PLC programming and logic development
4. HMI design and interface configuration
5. Panel wiring and hardware integration
6. Testing, commissioning and validation
7. Monitoring and performance optimisation

![Project workflow: seven stages from requirements to optimisation](img/03_project_workflow.svg)

## System components

| Component | Role |
|---|---|
| PLC | Central processing unit for the control logic |
| HMI | Human-machine interface for operation |
| I/O modules | Digital and analog input/output |
| Sensors | Level, pressure, flow, weight |
| Actuators | Motors, valves, cylinders, pumps |
| Communication | RS485 / Modbus / Industrial Ethernet |
| Power supply | 24 V DC power supply units |
| Control panel | Panel assembly and wiring integration |

## Applications

Concrete batching plants, material handling systems, industrial process automation, water and wastewater systems, manufacturing and production lines, chemical and cement industries, power and energy plants, factory and infrastructure automation.

## Design goals

- Better process efficiency and accuracy, with less manual operation and fewer errors
- Real-time monitoring and control
- Reliable, stable operation with alarm and safety management
- A scalable design that is easy to extend
- Lower maintenance and operating cost
- Data logging for performance analysis

## Technologies

PLC (Siemens, Modicon, Delta), HMI (Weintek, Siemens, Delta), SCADA, WinCC, TIA Portal / STEP 7, Unity Pro, WPLSoft / ISPSoft, AutoCAD Electrical, RS485, Modbus, Industrial Ethernet, load cells, motor control, control panel design

## Related

- [Embedded Systems, IoT & Industrial Automation](https://github.com/Mahyoub88/embedded-iot-automation)
- [Embedded EEPROM Data Storage & Retrieval System](https://github.com/Mahyoub88/eeprom-data-storage-pic)
- [All projects](https://mahyoub88.github.io/#work)
