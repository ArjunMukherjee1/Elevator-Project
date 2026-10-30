# Elevator Simulation

A tick-based elevator simulator in Java. It's built around a 7-state finite state machine, a call-prioritization scheduler and passengers who behave realistically. It includes a JavaFX visualization and 89 JUnit 5 tests across 70+ scenarios.

*Capstone project for Advanced Data Structures and Embedded Systems.*

## Features

- State machine: Seven states (`STOP`, `MVTOFLR`, `OPENDR`, `OFFLD`, `BOARD`, `CLOSEDR`, `MV1FLR`), updated every tick.
- Smart scheduling: Serves the busier direction first. Only turns around when no calls are left ahead.
- Realistic passengers: Capacity limits cause skips. Riders give up after waiting too long. Some riders force the closing doors to reopen.
- Configurable timing: Floor travel, door speed and boarding rate are all set in ticks.
- Analytics: Logs every event and exports each passenger's wait and trip times to CSV.

## Structure

```
src/building/      Building (state machine engine), Elevator, CallManager, Floor
src/passengers/    Passenger group model
src/genericqueue/  Generic bounded queue
src/               Controller, JavaFX GUI, JUnit test suites
test_data/         Scenario CSVs
```

The code is split MVC-style: the JavaFX GUI is the view, `ElevatorSimController` runs the tick loop, and `Building` is the model.

## Running

Requires Java, JavaFX, JUnit 5 and `library/cmpElevator.jar` on the classpath.

1. Set the building parameters in `ElevatorSimConfig.csv` (floors, capacity, timing, passenger file).
2. Launch `ElevatorSimulation`, then use Run or Step.
3. Run the `BuildingFSM*Test` suites. They check the simulator's logs against reference logs.

Tech: Java · JavaFX · JUnit 5 · State Machines · MVC
