# Engineering Record — Concrete Batching Control

This record defines the technical basis of the [project case study](https://mahyoub88.github.io/projects/proj-plc-control/) and [software interface guide](SOFTWARE_WALKTHROUGH.md). It distinguishes application configuration, database structure, hardware-family identification and the information required to complete an as-built engineering package.

## 1. Control and Information Architecture

One operator workstation hosts the SANY operational HMI, CNCRT production-management application and SQL Server 2000 database jxc. Both applications access production data through ADO/SQLOLEDB. The operational application also provides a Modbus RTU path to the PLC and separate serial weighing interfaces.

| Interface | Recorded configuration | Engineering interpretation |
|---|---|---|
| PLC communication | COM1, 38400 baud, 8E1, Modbus unit 2 | Command/status exchange between workstation and PLC |
| Status and command data | Coils, discrete inputs and holding registers; register writes for run/stop | Application communication pattern; field-address assignments require the plant program |
| Weighing communication | COM3–COM10, 19200 baud, 8N1 | Eight configured workstation serial interfaces |
| Database access | ADO/SQLOLEDB, SQL Server 2000, jxc | Persistent application and production records |

The data-storage path and field-control paths serve different purposes. The database holds production context and history; serial interfaces carry PLC and weighing communication.

## 2. Application Responsibilities

SANY presents the process mimic, task/recipe selection, production quantities, weighing adjustments, automatic/manual selection, mixing parameters and charge/discharge controls. CNCRT manages recipes, tasks, orders, deliveries, stock, consumption, reporting and administration.

The detailed interface guide identifies the visible controls in the supplied screenshots and separately lists functions documented in the application-form analysis. Screenshots describe historical interface states; they do not constitute a live plant test.

## 3. Database Structure

The exported jxc.sql DDL is the schema reference. It defines 35 application tables, 34 primary keys and 29 defaults. It contains no foreign-key, secondary-index, view, stored-procedure or trigger definitions. These observations apply to that export rather than every possible database copy.

Principal functional groups are recipe/batch records, production tasks and orders, deliveries, weighing settings, mix adjustments, inventory, station information, alarms and activity history. The published database diagram groups tables by purpose and does not assert SQL foreign-key relationships.

Different jxc files in the archive have equal sizes but different contents. They represent different database states and must be distinguished by provenance and file content rather than size alone.

## 4. Hardware and System Identification

| Source observation | Supported identification | Information still required |
|---|---|---|
| Controx2000 CoreTask.log names an S7-200 device | Siemens S7-200 family in the archived installation | Exact CPU, order number, firmware and installed hardware configuration |
| The same log names eight T600 devices | Mettler Toledo T600 device-family entries | Physical device identity, serial-port correspondence and material assignments |
| STEP 7-MicroWIN installation and recent-file history | S7-200 engineering environment | Original plant project and program contents |
| Euromecc names on physical-panel photographs; SANY names in PC software | Distinct physical-panel and software branding | OEM/installer boundaries and final system configuration |
| Equipment counts differ between panels and software mimic | The sources cannot be treated as one verified equipment schedule | As-built equipment inventory and modification history |

The archive includes HZS60-family reference material and an HZS120 station entry. These references do not establish the installed plant model, capacity, motor ratings or equipment counts. A Controx2000 runtime entry or website footer also does not independently identify the production front end for the SANY applications.

## 5. Source Register

| Source | Technical contribution |
|---|---|
| SANY application files and configuration | Application roles, forms and communication settings |
| CNCRT interface and application-form analysis | Production administration, delivery comparison and reporting functions |
| jxc.sql schema export | Table definitions, keys and defaults |
| Copied SQL Server/jxc files | Legacy engine context and distinguishable production-data states |
| Controx2000 runtime log | Historical device-family entries |
| STEP 7-MicroWIN environment | Programming-tool context and historical project references |
| Plant and control-panel photographs | Physical equipment context, branding and operator controls |

## 6. Requirements for a Complete As-Built Package

- Original PLC project or a controlled upload with CPU and hardware identification.
- Electrical drawings, terminal schedules, I/O list and field-device tags.
- Scale assignments, weighing-controller parameters, load-cell wiring and calibration records.
- Motor/drive nameplates and control interfaces.
- Original plant Controx project where applicable.
- FAT/SAT, service and handover records documenting tested behavior and individual/team responsibilities.

## Publication Scope

The portfolio presents implemented industrial work and clearly identifies subsequent technical analysis and general engineering illustrations. It does not attribute every OEM program to the portfolio author or claim recovered Ladder code, verified safety logic, new calibration measurements or measured performance improvements. Public material excludes complete databases, proprietary executables, customer identities and account data.
