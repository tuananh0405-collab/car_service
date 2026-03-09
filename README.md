# 🚗 CarService — AAOS Learning Project

A hands-on project to learn and practice **Android Automotive OS (AAOS)** concepts, focusing on `CarService` architecture, Vehicle HAL abstraction, and automotive UI development.

**Author:** anhvt86  
**Started:** March 9, 2026

---

## 📋 Progress Tracker

### Phase 1: Android Service & IPC Foundations *(Weeks 1–2)*

#### 1.1 — Bound Services & AIDL
- [ ] #1 — Create a basic `CarPropertyService` (Bound Service holding vehicle state)
- [ ] #2 — Define `ICarPropertyService.aidl` interface
- [ ] #3 — Implement the AIDL `Stub` backed by `SparseArray`
- [ ] #4 — Build client Activity to bind, call get/set, and display values

#### 1.2 — Callbacks & Observers
- [ ] #5 — Define `ICarPropertyCallback.aidl` with `onPropertyChanged()`
- [ ] #6 — Use `RemoteCallbackList` to manage listeners
- [ ] #7 — Simulate sensor changes with `Handler` + `Runnable`

#### 1.3 — Permissions & Security
- [ ] #8 — Define signature-level custom permission
- [ ] #9 — Enforce permission in service via `enforceCallingPermission()`
- [ ] #10 — Multi-client testing (second app module denied without permission)

---

### Phase 2: Vehicle Property System — HAL Abstraction *(Week 3)*

#### 2.1 — Property Model
- [ ] #11 — Define `VehicleProperty` constants (mirror real AAOS property IDs)
- [ ] #12 — Build generic `CarPropertyValue<T>` class
- [ ] #13 — Create `CarPropertyConfig` (access mode, change mode, ranges)

#### 2.2 — HAL Simulation Layer
- [ ] #14 — Build `VehicleHal` interface
- [ ] #15 — Implement `SimulatedVehicleHal` with realistic data generation
- [ ] #16 — Wire HAL → `CarPropertyService`

---

### Phase 3: Car API Manager Pattern *(Week 4)*

#### 3.1 — Manager Pattern
- [ ] #17 — Build `Car` entry-point class with `createCar()` and `getCarManager()`
- [ ] #18 — Create `CarPropertyManager` wrapper with clean public API
- [ ] #19 — Build `CarHvacManager` with HVAC-specific methods

#### 3.2 — Area IDs & Zone Mapping
- [ ] #20 — Implement `VehicleAreaSeat` and `VehicleAreaWindow` constants
- [ ] #21 — Multi-zone properties (per-seat HVAC temperature)
- [ ] #22 — UI: Dual-zone HVAC screen

---

### Phase 4: CarService Architecture Deep-Dive *(Week 5)*

#### 4.1 — Multi-Service Architecture
- [ ] #23 — `CarServiceBase` abstract class with lifecycle hooks
- [ ] #24 — Service registry initializing all sub-services
- [ ] #25 — `CarDiagnosticService` (anomaly detection, DTC logging)

#### 4.2 — Power Management
- [ ] #26 — Vehicle power state machine
- [ ] #27 — Deep sleep / hibernation with state persistence
- [ ] #28 — Garage mode simulation

---

### Phase 5: Instrument Cluster & Infotainment UI *(Weeks 6–7)*

#### 5.1 — Instrument Cluster
- [ ] #29 — Speedometer custom `View` with animated needle
- [ ] #30 — Tachometer (RPM gauge)
- [ ] #31 — Full dashboard Activity (speedometer + tachometer + gear + fuel)

#### 5.2 — HVAC Control Panel
- [ ] #32 — Temperature UI with dual-zone sliders
- [ ] #33 — Fan speed & direction controls
- [ ] #34 — Seat heater / AC toggle

---

### Phase 6: Advanced AAOS Topics *(Week 8)*

#### 6.1 — User Management
- [ ] #35 — User-scoped HVAC settings
- [ ] #36 — User switching flow (`ACTION_USER_SWITCHED`)

#### 6.2 — OEM Customization
- [ ] #37 — Vendor extension properties
- [ ] #38 — Config overlays per vehicle model

#### 6.3 — Car Watchdog & Health
- [ ] #39 — `CarWatchdogService` (heartbeat checks, restart)
- [ ] #40 — I/O overuse detection and logging

---

## 📊 Summary

| Phase | Status | Completed |
|-------|--------|-----------|
| Phase 1 — IPC Foundations | ⬜ Not Started | 0 / 10 |
| Phase 2 — Vehicle Properties | ⬜ Not Started | 0 / 6 |
| Phase 3 — Manager Pattern | ⬜ Not Started | 0 / 6 |
| Phase 4 — Architecture | ⬜ Not Started | 0 / 6 |
| Phase 5 — UI | ⬜ Not Started | 0 / 6 |
| Phase 6 — Advanced | ⬜ Not Started | 0 / 6 |
| **Total** | | **0 / 40** |

---

## 📚 Resources

- [AAOS Architecture](https://source.android.com/docs/automotive)
- [Android for Cars Overview](https://developer.android.com/training/cars)
- AOSP CarService source: `packages/services/Car/service/src/com/android/car/`
- Vehicle HAL: `hardware/interfaces/automotive/vehicle/`
