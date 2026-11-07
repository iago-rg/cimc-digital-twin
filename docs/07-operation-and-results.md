# 7. Operation and results

**Contents:** [Operating the twin](#71-operating-the-twin) · [Workpiece routes](#72-workpiece-routes) · [Results](#73-results) · [Benefits](#74-benefits) · [Limitations](#75-limitations) · [Demo videos](#76-demo-videos)

---

## 7.1 Operating the twin

The general procedure described in the theses is ([Souza, 2023](references.md); [Gomes, 2025](references.md)):

1. **Start the simulated PLC.** Run CODESYS Control Win V3, which simulates the PLC and runs the OPC UA server. Optionally, check that the server is listening on port 4840 (see [OPC UA communication](04-opc-ua-communication.md#42-opc-ua-server-in-codesys-phase-2)).
2. **Configure the addresses.** In the configuration screen of the twin, enter the address of the OPC UA server (for example, `opc.tcp://127.0.0.1:4840`) and the NodeId of each input and output variable, so that all variables are correctly mapped between CODESYS and Unity.
3. **Start the twin.** Unity establishes the connection with the PLC, which executes the programmed logic, with the data exchange taking place in real time.
4. **Add a workpiece.** In phase 1, a workpiece is added by clicking on one of the three pieces located in the box at the end of the conveyor of the twin.
5. **Operate the push buttons of the twin.** Release the emergency button and press Start to begin the process; the operator also presses Start at the inspection points of the sequence (see [Control logic](06-control-logic.md#control-sequence)).

> Detailed setup instructions — installing the tools and opening the Unity and CODESYS projects — will be added together with the source code.

## 7.2 Workpiece routes

The main purpose of the plant is to process three types of workpieces, each with its own route and processing method ([Gomes, 2025](references.md)):

| | Polymer | Aluminum | Steel |
|---|---|---|---|
| Classification on the conveyor | Capacitive sensor only → non-metallic (`M01`) | Capacitive + inductive → metallic (`M00`) | Capacitive + inductive → metallic (`M00`) |
| Transfer to the rotary table | Linear transfer + Cartesian manipulator; operator presses Start at the inspection point | Same | Same |
| Drilling | Yes | 3 mm hole | 6 mm hole |
| Vision inspection | No — the table carries the workpiece to the removal station | Hole must be 3 mm (bank 100) | Hole must be 6 mm (bank 010) |
| Weighing | No | 95–105 g | 115–125 g |
| End | Removal station | Returned to the table → removal station | Returned to the table → removal station |

If the hole of a metallic workpiece does not match its material, the system generates an error and waits for the operator to restart the process. A complete flowchart is shown in [The CIM-C plant](02-the-cim-c-plant.md#process-flow).

## 7.3 Results

### Phase 2 — integrated twin (CIM-A + CIM-B)

All the elements of CIM-B were integrated into the virtual scene, compatible with the previously implemented CIM-A stage. Through the OPC UA connection between the PLC simulated in CODESYS and the twin, the system could be tested under conditions close to those of the physical plant ([Gomes, 2025](references.md)):

- the control logic developed in Ladder and the virtual model in Unity made it possible to **simulate and validate the operational flows** of the metallic and polymer workpieces;
- the system proved **functional and stable** during the tests with the three workpiece types (steel, aluminum and polymer), correctly following the defined flows and respecting the operating conditions of each one;
- the use of sensors, actuators and a structured validation logic made it possible to **replicate the acceptance and rejection criteria** of the workpieces, giving the twin a behavior consistent with that of the real plant;
- the results validate the **communication between Unity and CODESYS** and reinforce the feasibility of using digital twins in educational environments.

The results were satisfactory regarding all the objectives initially proposed: the CIM-B components were modeled, integrated into the virtual environment in Unity, the communication with the PLC simulated in CODESYS was configured through OPC UA, a functional control logic was developed in Ladder, and the integration with CIM-A was carried out, allowing the operation of both stages of the CIM-C plant to be simulated digitally ([Gomes, 2025](references.md)).

### Phase 1 — CIM-A twin

The application allows the implementation of industrial automation projects to be tested in a simulated environment, using the OPC UA protocol. With the implemented GRAFCET, the twin responded satisfactorily, being able to work and respond similarly to the real plant to any implemented logic. The results were achieved satisfactorily in all aspects of the initial proposal ([Souza, 2023](references.md)).

## 7.4 Benefits

According to the conclusions of the theses ([Souza, 2023](references.md); [Gomes, 2025](references.md)):

- **Academic:** efficiency in the teaching–learning process, since students can explore the operation of automated systems virtually, without depending on the physical structure. The twin can be used as a didactic tool in the Integrated Manufacturing Systems course, allowing students to implement and test the logic developed in class in a realistic and practical virtual environment.
- **Industrial:** efficiency in the validation of control logic, reducing the time and cost of tests on real equipment. Prior simulation makes it possible to identify failures and make adjustments before implementation in the physical system, reinforcing the safety and reliability of the processes.
- **Mobility:** the plant can be accessed, simulated and monitored remotely through the virtual environment, regardless of geographic location, providing flexibility in development and training.
- **Flexibility:** since the plant is controlled from an OPC UA server, the virtual PLC can be replaced by other controllers that support the protocol, so the application is not limited to a specific environment or manufacturer.

## 7.5 Limitations

- **Timing:** although the control logic is the same, the operation times in the virtual environment may not correspond exactly to the real ones; the approximation allows the logical and functional behavior of the system to be validated ([Gomes, 2025](references.md)).
- **Vision system:** the simulated camera reads the hole property of the workpiece; image-based hole detection was not implemented ([Gomes, 2025](references.md)).
- **Security:** to limit the scope of the projects, the client accepts untrusted certificates and anonymous connections are allowed ([Souza, 2023](references.md); [Gomes, 2025](references.md)).
- **Coverage:** only the CIM-A and CIM-B stages are twinned; the workpiece clamping actuator of the drilling module, present in the physical plant, is not yet part of the simulation ([Gomes, 2025](references.md)).

The next steps are listed in [Project history and future work](08-history-and-future-work.md#future-work).

## 7.6 Demo videos

| Video | Content |
|---|---|
| [youtu.be/hlPfECJXHF8](https://www.youtube.com/watch?v=hlPfECJXHF8) | Phase 2 — complete operation of the integrated twin ([Gomes, 2025](references.md)) |
| [youtu.be/78XFZRFa8hI](https://youtu.be/78XFZRFa8hI) | Phase 1 — configuration and operation of the CIM-A twin ([Souza, 2023](references.md)) |
