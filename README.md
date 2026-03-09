# 🚗 CarService — AAOS Learning Project

A hands-on project to learn and practice **Android Automotive OS (AAOS)** using **real AOSP source and emulator**, focusing on `CarService` architecture, Vehicle HAL, and Car APIs.

**Author:** anhvt86  
**Started:** March 9, 2026  
**Environment:** Ubuntu + AOSP source + AAOS Emulator

---

## 📋 Progress Tracker

### Phase 1: Android Service & IPC Foundations *(Weeks 1–2)*

> Using real AAOS CarService source code and APIs

#### 1.1 — Understand CarService Binding (Car API client)
- [ ] #1 — Create an app that uses `Car.createCar()` to connect to the system CarService
- [ ] #2 — Use `CarPropertyManager` to read vehicle properties (`PERF_VEHICLE_SPEED`, `GEAR_SELECTION`, `FUEL_LEVEL`)
- [ ] #3 — Use `CarPropertyManager.registerCallback()` to listen for property changes in real-time
- [ ] #4 — Build a UI displaying live vehicle property values from the emulator's simulated VHAL

#### 1.2 — AIDL & IPC Deep-Dive
- [ ] #5 — Study the real `ICarProperty.aidl` in AOSP source (`packages/services/Car/car-lib/`)
- [ ] #6 — Trace the IPC flow: `CarPropertyManager` → `ICarProperty.aidl` → `CarPropertyService` → `VehicleHal`
- [ ] #7 — Build a custom AIDL service (separate process) that wraps `CarPropertyManager` and exposes a simplified API to other apps

#### 1.3 — Permissions & Security
- [ ] #8 — Study `CarService` permission model: `android.car.permission.CAR_SPEED`, `CAR_ENERGY`, etc.
- [ ] #9 — Request car permissions in your app manifest and handle runtime permission grants
- [ ] #10 — Test access denial: try reading properties without the required permission

---

### Phase 2: Vehicle HAL & Property System *(Week 3)*

> Exploring the hardware abstraction layer that bridges CarService to vehicle hardware

#### 2.1 — VHAL Architecture
- [ ] #11 — Study the VHAL AIDL interface in AOSP (`hardware/interfaces/automotive/vehicle/`)
- [ ] #12 — Explore the default VHAL implementation and how it generates simulated data
- [ ] #13 — Understand `VehiclePropConfig` — property metadata (access mode, change mode, area type, ranges)

#### 2.2 — Property Types & Areas
- [ ] #14 — Read properties of different types: `INT32` (gear), `FLOAT` (speed), `BOOLEAN` (parking brake)
- [ ] #15 — Work with area-based properties: `HVAC_TEMPERATURE_SET` per seat zone (`VehicleAreaSeat`)
- [ ] #16 — Set writable properties via `CarPropertyManager.setProperty()` (e.g., HVAC temperature)

---

### Phase 3: CarService Internal Architecture *(Week 4)*

> Reading and understanding the real CarService source code in AOSP

#### 3.1 — System Service Structure
- [ ] #17 — Study `ICarImpl.java` — the main service that initializes all sub-services
- [ ] #18 — Map the sub-service registry: `CarPropertyService`, `CarHvacService`, `CarPowerManagementService`, `CarUxRestrictionsManagerService`, etc.
- [ ] #19 — Study the `CarServiceBase` lifecycle: `init()`, `release()`, `dump()`

#### 3.2 — CarPropertyService Internals
- [ ] #20 — Trace a `getProperty()` call from Car API → AIDL → CarPropertyService → PropertyHalService → VehicleHal
- [ ] #21 — Study how `CarPropertyService` manages subscriptions and dispatches callbacks
- [ ] #22 — Study `PropertyHalService` — the bridge between CarPropertyService and VehicleHal

---

### Phase 4: Power Management & Garage Mode *(Week 5)*

> Understanding vehicle power states and background processing

#### 4.1 — Power Management
- [ ] #23 — Study `CarPowerManagementService` and vehicle power states
- [ ] #24 — Understand the power state machine: `ON → SHUTDOWN_PREPARE → DEEP_SLEEP / SHUTDOWN`
- [ ] #25 — Study how apps receive power state notifications via `CarPowerManager`

#### 4.2 — Garage Mode
- [ ] #26 — Study Garage Mode: when/how it triggers after vehicle is parked
- [ ] #27 — Build an app component that runs background work during Garage Mode using `JobScheduler`
- [ ] #28 — Study `GarageModeService` source code in AOSP

---

### Phase 5: Building Automotive Apps *(Weeks 6–7)*

> Creating real automotive applications using Car APIs

#### 5.1 — Instrument Cluster Client
- [ ] #29 — Build a cluster app displaying real-time speed from `CarPropertyManager`
- [ ] #30 — Add RPM, gear indicator, and fuel gauge reading live VHAL data
- [ ] #31 — Use `CarUxRestrictionsManager` to handle driver distraction restrictions

#### 5.2 — HVAC Control Panel
- [ ] #32 — Build an HVAC app using `CarPropertyManager` for temperature control per zone
- [ ] #33 — Implement fan speed and direction controls
- [ ] #34 — Handle seat heater / AC toggle with real `HVAC_*` properties

---

### Phase 6: Advanced AAOS Topics *(Week 8)*

> System-level features that distinguish AAOS from standard Android

#### 6.1 — Multi-User & Multi-Display
- [ ] #35 — Study AAOS multi-user architecture: driver vs passenger profiles
- [ ] #36 — Handle `ACTION_USER_SWITCHED` and per-user settings
- [ ] #37 — Explore multi-display support for passenger entertainment

#### 6.2 — OEM Customization
- [ ] #38 — Study vendor property extensions (`VENDOR_PROPERTY_*` range)
- [ ] #39 — Explore Runtime Resource Overlays (RROs) for OEM theming

#### 6.3 — Car Watchdog
- [ ] #40 — Study `CarWatchdogService` — health monitoring and I/O overuse detection

---

## 📊 Summary

| Phase | Status | Completed |
|-------|--------|-----------|
| Phase 1 — IPC & Car API | ⬜ Not Started | 0 / 10 |
| Phase 2 — VHAL & Properties | ⬜ Not Started | 0 / 6 |
| Phase 3 — CarService Internals | ⬜ Not Started | 0 / 6 |
| Phase 4 — Power & Garage Mode | ⬜ Not Started | 0 / 6 |
| Phase 5 — Automotive Apps | ⬜ Not Started | 0 / 6 |
| Phase 6 — Advanced | ⬜ Not Started | 0 / 6 |
| **Total** | | **0 / 40** |

---

## 🛠 Environment Setup

- **AOSP source**: Built and flashed on Ubuntu
- **Emulator**: AAOS emulator with simulated VHAL
- **Key AOSP paths**:
  - `packages/services/Car/` — CarService source
  - `packages/services/Car/car-lib/` — Car API (client library)
  - `hardware/interfaces/automotive/vehicle/` — Vehicle HAL interface
  - `packages/services/Car/tests/` — Test apps and examples

## 📚 Resources

| Resource | Link |
|----------|------|
| AAOS Architecture | [source.android.com/docs/automotive](https://source.android.com/docs/automotive) |
| Car API Reference | [developer.android.com/reference/android/car](https://developer.android.com/reference/android/car/package-summary) |
| AOSP CarService | `packages/services/Car/service/src/com/android/car/` |
| Vehicle HAL | `hardware/interfaces/automotive/vehicle/` |
| Sample Car Apps | `packages/apps/Car/` |
