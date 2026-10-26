# Concrete batching plant: engineering record

This record supports the [portfolio case study](https://mahyoub88.github.io/projects/proj-plc-control/) and the [repository overview](../README.md). It summarizes retained software, database and photograph findings. It is not an as-built drawing package or a replacement for the original PLC program.

## Sources reviewed in the project analysis

| Source | What it contributes |
|---|---|
| SANY application archive, including sany.exe, sany9.exe, cncrt.exe and configuration files | Operator forms, application roles, saved communication settings and database access |
| SQL Server package and copied jxc database files | Legacy engine context and production-record structure; different database copies represent different states |
| Exported jxc.sql DDL | Authoritative exported schema: 35 application tables, 34 primary keys and 29 defaults |
| Controx2000 CoreTask.log | Runtime entries naming one Siemens S7-200 device and eight Mettler Toledo T600 devices |
| Archived STEP 7-MicroWIN installation and recent-file history | Programming-environment context; only templates/samples and historical project names were recovered |
| Plant and control-panel photographs | Physical plant context, Euromecc branding, weighing indicators and operator controls |

The public record summarizes the earlier archive analysis; raw binaries, database rows and private analysis workspaces are not linked here.

## Recorded application architecture

One computer hosts the SANY operational HMI, the production-management application and SQL Server. The programs share the jxc database through ADO/SQLOLEDB. sany.exe has saved configurations for Modbus RTU communication with the PLC and separate serial weighing interfaces.

| Interface | Saved parameters | Boundary |
|---|---|---|
| PC to PLC | COM1, 38400 baud, 8 data bits, even parity, 1 stop bit, Modbus unit 2 | Software configuration; not proof of present physical wiring |
| PLC status polling | Coils, discrete inputs and holding registers; run/stop commands use register writes | Polling pattern does not recover the plant Ladder code or assign field addresses |
| Weighing interfaces | Eight ports, COM3-COM10, 19200 baud, 8N1 | Material assignments and physical cable topology are unknown |
| Database access | ADO/SQLOLEDB, jxc on SQL Server 2000 | Business/production storage; not the real-time field-control path |

## Operational functions

The application forms expose recipe/task selection, target quantity and cycle count, automatic/manual modes, weight setup, coarse-feed and fall compensation, tare, mixing timers, pause charge/discharge, discharge inhibition and alarm display. The production application exposes orders, deliveries, consumption, stock, daily/monthly reports and activity records.

These controls show available operator functions. They do not verify every sequence transition, interlock, communication-loss response or emergency-stop circuit. Those require the PLC source and plant drawings.

## Data model

The exported DDL, rather than an earlier partial binary-catalog extraction, is the schema authority. Its 35 tables include recipe, batch, task/order, delivery, station, stock, weighing-setting, adjustment, alarm and activity records.

The export contains no foreign-key definitions, secondary indexes, views, stored procedures or triggers. That describes this export; it does not prove that every database copy was identical. Application code handles relationships absent from the exported database constraints.

Different retained jxc files have the same size but different contents. They must not be treated as interchangeable. Names, customer records, operator/account details and individual delivery rows are deliberately excluded from this public summary.

## Hardware interpretation

| Observation | Supported conclusion | Still unresolved |
|---|---|---|
| Runtime log names an S7-200 series device | S7-200 family is documented in the archived installation | Exact CPU, order number, firmware and physical rack |
| Runtime log starts eight T600 device entries | Eight logical T600 devices are documented | Whether each maps to one saved serial port, and which material each weighs |
| STEP 7-MicroWIN is installed | S7-200 engineering tools were available in that workstation environment | Authorship and contents of the plant program |
| Euromecc names on photographed panels; SANY names in software | Physical-panel branding and PC-software branding differ | OEM/installer scope, final plant model and complete control-system provenance |
| Panel and mimic bin/silo counts differ | The pictures cannot be combined into a single verified equipment schedule | Actual installed counts and any later modifications |

The HZS60-family brochure is a reference found in the archive. A station record also contains HZS120 text. Neither establishes a verified installed model, throughput, motor rating or equipment count for the photographed plant.

## Evidence still needed for an as-built package

- PLC upload or original project, with CPU identification and hardware configuration.
- Electrical drawings, terminal schedules, I/O list and documented field-device tags.
- Weighing-controller configuration, scale assignments, load-cell wiring and calibration records.
- Drive and motor nameplates and control interfaces.
- Original plant Controx project, if that application was used in production.
- FAT/SAT or service records identifying tested behavior and personal/team responsibilities.

## Interpretation of the portfolio

The project remains presented as implemented industrial work. Technical documentation and later archive analysis are described separately from recovered original code. Generic Ladder, I/O, Ethernet and commissioning figures are educational references and must not be used as evidence that those exact implementations were installed.
