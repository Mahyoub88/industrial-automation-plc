# Industrial Automation & PLC-Based Control Systems

**Concrete batching control integrating a PC-based operator interface, PLC communication, serial weighing and production management.**

[Project case study](https://mahyoub88.github.io/projects/proj-plc-control/) · [Software interface guide](docs/SOFTWARE_WALKTHROUGH.md) · [Engineering record](docs/ENGINEERING_RECORD.md) · [Professional profile summary](docs/PROFILE_DESCRIPTION.md)

## Project Overview

This implemented industrial automation project covers the control and information layers of a central concrete batching plant: material handling, recipe-based dosing, weighing, mixing, discharge and production reporting. Its architecture combines the SANY operational HMI, a separate production-management application and a shared SQL Server database on one operator workstation.

The case study explains how operator commands, PLC status, weighing interfaces and production records fit together. Original software screenshots support the interface walkthrough, while technical diagrams describe the control and data architecture.

**Mohammed Mahyoub** · [Engineering portfolio](https://mahyoub88.github.io/projects/)

## System Architecture

| Component | Function |
|---|---|
| SANY operational HMI | Process visualization, batch parameters, automatic/manual operation, weighing adjustments, mixing and discharge commands |
| CNCRT production management | Recipes, tasks, orders, deliveries, material consumption, inventory and production reports |
| PLC interface | Process command and status exchange over Modbus RTU |
| Serial weighing interfaces | Dedicated workstation connections for weighing-device communication |
| SQL Server 2000 — jxc | Shared recipe, batch, delivery, configuration, alarm and activity records |

![PC-based batching control architecture](img/10_recorded_control_architecture.svg)

### Communication Configuration

| Interface | Configuration recorded in the application |
|---|---|
| PC to PLC | COM1; Modbus RTU; 38400 baud; 8 data bits; even parity; 1 stop bit; unit address 2 |
| Weighing channels | Eight serial ports, COM3–COM10; 19200 baud; 8 data bits; no parity; 1 stop bit |
| Application data access | ADO/SQLOLEDB connection to the shared jxc database |

An archived runtime log identifies Siemens S7-200 and Mettler Toledo T600 device families. Exact CPU identification and the association between logged weighing devices and physical serial channels remain subject to the original hardware configuration.

## Operator Interface — SANY

The operational screen brings together recipe selection, production quantities, material readouts, process visualization and operator controls. It provides automatic/manual selection, charge/discharge pause, run/stop commands, mixing parameters and discharge inhibition.

![SANY process monitoring and operator interface](img/software/sany-operator-interface.webp)

The [software interface guide](docs/SOFTWARE_WALKTHROUGH.md) explains each visible control group and includes close-ups of batch settings and process commands.

## Production Management — CNCRT

The management application organizes the production context around the batch: recipes, orders, customers, trucks, deliveries, material consumption and reports. Its delivery view presents individual batch quantities alongside cumulative delivery totals, with document preview and printing functions.

![CNCRT production and delivery management interface](img/software/cncrt-production-interface.webp)

### Planned Versus Actual Quantities

The report uses Scheme for the target quantity, Fact for the recorded actual quantity and Error for percentage deviation:

**Deviation (%) = (Actual − Target) / Target × 100**, for a nonzero target.

In the illustrated record, a target of 400.0 and an actual quantity of 378.0 produce −5.50%; a target of 1000.0 and an actual quantity of 1026.0 produce +2.60%. These examples explain the historical report rather than establish new calibration results.

## Shared Production Database

The exported jxc schema contains 35 application tables. Principal groups include recipes and batches, production tasks and orders, deliveries, weighing settings, inventory, station information, alarms and activity history.

![Shared SANY and CNCRT production-data architecture](img/software/jxc-shared-data.svg)

| Tables | Application purpose |
|---|---|
| recipe; manufacture | Recipe targets and planned-versus-actual batch quantities |
| Task; Orders; OrderDetail; OutMaster | Production planning, orders and deliveries |
| exactitude; fall; adjcfg | Weighing tolerances, in-flight compensation and mix adjustments |
| products; stock; Station | Material, inventory and station information |
| Alarm; LogInfo | Alarm and activity records |

## Operating Workflow

1. Define the recipe, production task and delivery requirements.
2. Select the task and configure batch parameters in the operational HMI.
3. Exchange process commands and status with the PLC while acquiring weighing information through the configured serial interfaces.
4. Coordinate charging, mixing and discharge through the available operator functions and process conditions.
5. Store batch quantities and production context, then review individual batches and cumulative deliveries in the management application.

## Engineering Documentation

- [Software interface guide](docs/SOFTWARE_WALKTHROUGH.md): original screenshots, detailed field descriptions, reporting examples, application-function inventory and technical glossary.
- [Engineering record](docs/ENGINEERING_RECORD.md): communication settings, schema interpretation, hardware identification and documentation limits.
- [Project index](docs/PROJECTS.md): canonical project links and publication scope.
- [Professional profile summary](docs/PROFILE_DESCRIPTION.md): concise project description for professional profiles.

The original I/O, Ladder, weighing, network, alarm and commissioning figures remain available in the image archive as general engineering references. Their example brands, addresses and wiring are not presented as the plant's as-built configuration.

## Documentation Scope

This case study draws on application records, original screenshots, the database export and plant/control-panel photographs. The physical panels carry Euromecc branding, while the PC applications are SANY; differences in equipment counts and model references are retained in the engineering record. A single installed model or rated capacity is therefore not asserted.

The original plant Ladder program, exact CPU/order number, as-built I/O schedule, electrical drawings, scale assignments and complete commissioning records are not available in the reviewed archive. Published screenshots have identifying fields masked. Proprietary executables, complete databases, account details and private business records are not distributed.

## Related Engineering Projects

- [PIC-Based Equipment Room Monitoring & Control System](https://github.com/Mahyoub88/embedded-iot-automation)
- [PIC EEPROM Implementation Archive](https://github.com/Mahyoub88/eeprom-data-storage-pic)
- [Complete Engineering Portfolio](https://mahyoub88.github.io/projects/)
