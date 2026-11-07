# 8. Project history and future work

**Contents:** [Timeline](#timeline) · [Contributions of each phase](#contributions-of-each-phase) · [Challenges](#challenges) · [Future work](#future-work)

---

## Timeline

| When | Milestone |
|---|---|
| 2020–2021 | The Integrated Manufacturing Systems course is taught remotely during the COVID-19 pandemic; a single physical plant, operated through a camera, is shared by several teams — the motivation for the twin ([Souza, 2023](references.md)) |
| July 2023 | **Phase 1** — B.Sc. thesis of Lucas Faria Schuenck de Souza, approved on 7 July 2023: digital twin of CIM-A, controlled from Siemens TIA Portal / PLCSIM Advanced |
| July 2025 | **Phase 2** — B.Sc. thesis of Iago Rangel Gomes, defended on 17 July 2025: digital twin of CIM-B, integration with CIM-A and migration to CODESYS |

The project is authored by **Iago Rangel Gomes** and **Lucas Faria Schuenck de Souza**. Both theses were developed in the Control and Automation Engineering program of CEFET-MG, Leopoldina campus, under the supervision of Prof. Rodolfo Lacerda Valle; phase 1 was co-supervised by Prof. Thiago Campos Acácio Paschoalin. In the same line of research, a Software-in-the-Loop simulator of a dairy-product filling process was also developed at the institution ([Andrade, 2024](references.md)).

## Contributions of each phase

| Phase 1 — CIM-A ([Souza, 2023](references.md)) | Phase 2 — CIM-B and integration ([Gomes, 2025](references.md)) |
|---|---|
| 3D models of the conveyor unit, linear transfer unit and Cartesian handling unit (Inventor → Blender → Unity) | 3D models of the rotary table, drilling module, vision system, horizontal handling unit and weighing module (Inventor → Blender → Unity) |
| Animation and sensor emulation of the CIM-A modules | Behavior scripts of the CIM-B modules: table indexing, drilling, hole inspection, handling unit and weighing |
| OPC UA client in Unity (`clientOPCUA` class), based on the OPC Foundation libraries | Reuse of the phase 1 client and integration of CIM-B with CIM-A, allowing a unified simulation of both stages |
| OPC UA server in TIA Portal V17 + PLCSIM Advanced V4 (S7-1500) | Migration of the PLC and OPC UA server to CODESYS — free, with native OPC UA support and compatible with several manufacturers |
| User interface: main menu, address configuration and information panel | Configuration screen covering the 38 variables of both stages, with annotated views of CIM-A and CIM-B |
| GRAFCET for CIM-A programmed in TIA Portal, with start/stop function | Control logic restructured to cover both stages: GRAFCET (steps M0–M50) implemented in Ladder |
| Application for Windows and Linux | Validation with the three workpiece types (polymer, aluminum and steel) |

## Challenges

- **Phase 1:** the greatest difficulty was the communication between the OPC UA client and server ([Souza, 2023](references.md)).
- **Phase 2:** the greatest challenge was continuing a previously started project, which required understanding and interpreting the code and the whole architecture of the application. Implementing the behavior of the 3D models in Unity was also challenging, as it was a new experience for the author: it required studying and applying C# programming, animation, modeling and interaction between objects in the virtual environment, so that the modules correctly simulated the behavior of the physical plant ([Gomes, 2025](references.md)).

## Future work

Suggested in phase 2 ([Gomes, 2025](references.md)):

1. Extend the virtualization to the whole CIM-C plant, integrating the modules not yet developed.
2. Develop a human–machine interface (HMI) to make the process more intuitive and interactive, with buttons, indicators and graphs to facilitate the monitoring of the system.
3. Perform practical tests with the real plant, comparing its operation times with those of the virtual environment, in order to equalize the digital twin and the physical plant.
4. Improve the motion of the modules, focusing on visual smoothness and on the accuracy of the displacements.
5. Implement the workpiece clamping actuator of the drilling module, which is present in the physical plant but not yet in the simulation.

Suggested in phase 1 ([Souza, 2023](references.md)):

- Continue the project towards the digital twin of the whole CIM-C plant, refining the movement of the actuators — partially addressed by phase 2, which added the CIM-B stage.
- Develop an OPC UA server that communicates directly with the twin, without the need for other software.
- Apply augmented reality to the twin, for a better student experience.
- Improve the graphics, optimize the twin, display time charts and provide an interface with more information about the communication between client and server.
