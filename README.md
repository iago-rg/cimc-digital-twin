# CIM-C Digital Twin

3D digital twin of the **CIM-C didactic plant** (De Lorenzo) installed at the Laboratory of Flexible Manufacturing Cells and Robotics of CEFET-MG, Leopoldina campus, Brazil.

> 🚧 This repository is under construction. More material about the project will be added soon.

## Overview

The digital twin reproduces the two stages of the CIM-C plant:

- **CIM-A**: conveyor with inductive, capacitive and optical sensors, linear transfer unit and Cartesian manipulator (developed in a previous work by L. F. S. de Souza, 2023);
- **CIM-B**: six-position rotary table, drilling module, vision system, horizontal handling unit and weighing module (developed in this work).

The plant is controlled by a PLC simulated in **CODESYS**, programmed in **Ladder** from a **GRAFCET** model. The PLC communicates with the digital twin, developed in **Unity**, through the **OPC UA** protocol, using the **Software-in-the-Loop (SiL)** technique to implement and validate the control logic in a simulated environment. The system processes three types of workpieces: polymer, aluminum and steel.

## Tools

| Purpose | Tool |
|---|---|
| 3D modeling | Autodesk Inventor |
| Hierarchy, materials and pivots | Blender |
| Digital twin and animation (C#) | Unity 2021.3.16f1 |
| Simulated PLC and OPC UA server | CODESYS V3.5 SP20 Patch 5 |
| OPC UA server inspection | UaExpert 1.7.2 |

## Coming soon

- Detailed description of the system and of each module
- OPC UA communication setup (CODESYS and Unity)
- Input/output variables of the plant
- GRAFCET and Ladder control logic
- Demonstration videos

## Publications

- I. R. Gomes, *Modelagem e Desenvolvimento de um Gêmeo Digital 3D Aplicado à Planta Didática CIM-C*, B.Sc. thesis (Control and Automation Engineering), CEFET-MG, Leopoldina, Brazil, 2025 (in Portuguese).
- I. R. Gomes, R. L. Valle, M. F. dos Santos, M. Morais, J. Mendes, and P. Mercorelli, *Software-in-the-Loop Validation of PLC Logic with a 3D Digital Twin of a Didactic Computer-Integrated Manufacturing Plant* (to appear).

## Authors

- **Iago Rangel Gomes** – iagorg2000@gmail.com
- **Rodolfo Lacerda Valle** (advisor) – rodolfolacerda@cefetmg.br

Department of Electroelectronics, Federal Center of Technological Education of Minas Gerais (CEFET-MG), Leopoldina, Brazil.
