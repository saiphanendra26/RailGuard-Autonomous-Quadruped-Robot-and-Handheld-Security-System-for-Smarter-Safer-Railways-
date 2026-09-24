RailGuard
         Autonomous Quadruped Robot and Handheld
         Security System for Smarter & Safer Railways
                   Technology Details for Narcotics andExplosives Detection in Indian Railways

 Purpose. RailGuard is a technology blueprint for a rugged mobile quadruped robot and companion handheld device
 for RPF screening, surveillance, inspection and incident alerting. It is intended for concept design, prototype
 development and a Smart India Hackathon-style project proposal.

 Safety position. RailGuard is a screening, inspection and decision-support platform. A detection alert must be verified
 by trained RPF, forensic or bomb-disposal personnel under approved SOPs. The robot must not autonomously touch,
 manipulate or neutralise a suspicious object.

 1. Solution at a Glance

  Subsystem                Recommended Implementation                           Operational Role

  Robot software           Ubuntu Linux + ROS 2 Humble/Jazzy                    Sensor integration, robot control, navigation and mission
                                                                                management

  Navigation               LiDAR SLAM, Nav2, IMU and camera/leg-odometry        GPS-denied mapping, obstacle avoidance, patrol routes
                           fusion                                               and safe return

  Edge AI                  NVIDIA Jetson Orin NX/AGX Orin or industrial         Real-time vision, thermal analysis, sensor fusion and local
                           equivalent                                           alerts

  Chemical detection       IMS + Raman or NIR; e-nose as a screening layer      Trace alerts and material-screening workflow

  Vision                   RGB, low-light and radiometric thermal cameras       Surveillance, unattended-baggage alerts, inspection and
                                                                                night patrol

  Connectivity             4G/5G, Wi-Fi 6 and secured mesh-radio backup         Live video, telemetry, remote control and control-centre
                                                                                alerts

  Backend                  MQTT/DDS, FastAPI, PostgreSQL/PostGIS, React         Fleet monitoring, incident records, map view, audit trail
                           dashboard                                            and reporting

  Handheld device          Rugged ARM system with IMS and Raman/NIR             Rapid personnel-operated screening, offline logging and
                                                                                synchronisation

 2. Programming Languages and Frameworks
  Area                       Technology                                      use

  Real-time robotics         C++17/20, ROS 2, rclcpp                         Low-latency sensor drivers, control nodes, navigation and
                                                                             safety interfaces

  Application logic          Python 3, rclpy                                 Rapid prototyping, data processing, AI orchestration and test
                                                                             scripts

  AI and vision              PyTorch, OpenCV, ONNX Runtime,                  Training, detection, tracking, segmentation and accelerated
                             TensorRT, CUDA                                  edge inference

  Navigation                 Nav2, SLAM Toolbox, robot_localization          Path planning, localisation, mapping and sensor fusion

  Simulation                 Gazebo/Ignition or NVIDIA Isaac Sim             Virtual railway-yard/coach scenarios and regression testing

  Area                       Technology                                        Use

  Web dashboard              React, TypeScript, MapLibre/Leaflet               Live control-room interface, map, incidents and fleet status

  Backend/API                FastAPI or Node.js, REST, WebSocket               Device API, alert workflows, user management and
                                                                               dashboard services

  Messaging                  MQTT and/or ROS 2 DDS                             Efficient telemetry, alerts, health data and command
                                                                               messaging

  Data                       SQLite on device; PostgreSQL/PostGIS              Offline event storage, geospatial queries, reporting and
                             centrally                                         retention

  DevOps                     Git, Docker, CI/CD, unit/integration tests        Repeatable builds, version control and secure deployment

 3. Quadruped Hardware Architecture
 3.1 Rugged mobility platform
- Fourindependentlyactuated legsusing brushless motors, joint encoders and torque/current feedback.
- High-clearance chassis and protected lower body for uneven ballast, yard terrain, cables and coach underframe
      access.
- Operating modes: stand, walk, crawl, crouch, precision inspection, teleoperation, return-to-base and emergency

      stop.
- Ingress-protected enclosure, vibration isolation, protected sensor windows and corrosion-resistant fasteners.
- Hot-swappable battery packs with battery-management system, thermal monitoring and low-battery safe-return
- logic.
      Independent hardwired emergency stop, remote stop command and watchdog-controlled safe shutdown.
 3.2 Compute and control
  Component                    Recommended Specification                                 Purpose

  Primary edge computer        Jetson Orin NX for prototype; AGX Orin/industrial GPU     Runs AI, video processing, sensor fusion, SLAM
                               computer for high payload                                 and mission control

  Safety MCU                   STM32 or safety-oriented TI/automotive-class              Motor interlocks, e-stop, battery monitoring and
                               controller                                                independent watchdog

  Memory/storage               16–32 GB RAM; 512 GB–2 TB industrial NVMe SSD             Models, maps, encrypted logs and locally buffered
                                                                                         video

  Power                        Isolated DC-DC rails and fused power distribution         Separates sensitive compute/sensors from
                                                                                         actuator noise

  Time source                  RTC plus NTP/PTP; GNSS time outdoors                      Accurate incident timestamps and sensor-data
                                                                                         alignment

 4. Sensor Payload
  Sensor             Technology / Interface                Primary Use                               Important Limitation

  3D LiDAR           360-degree 3D LiDAR;                  SLAM, obstacle detection, mapping         Performance can degrade in heavy
                     Ethernet/UDP                          and route planning                        rain, dense dust or reflective surfaces

  IMU and            9-axis IMU, joint encoders,           Attitude estimation, odometry and         Requires calibration and fusion with
  encoders           CAN/Ethernet                          stable walking                            other sensors

  Sensor             Technology / Interface              Primary Use                                Important Limitation

  RGB cameras        Wide-angle/4K, global shutter       Visual patrol, package/person              Low-light performance varies
                     preferred                           detection, teleoperation

  Thermal camera     Radiometric thermal imager          Night visibility, heat anomalies,          Does not identify narcotics or
                                                         fire/smoke support                         explosives chemically

  IMS                Swab and/or vapour                  Trace screening for explosives and         Requires approved sampling,
                     trace-detection module              narcotics                                  calibration and consumables

  Raman              Portable Raman spectrometer on      Material screening/identification where    Opaque packaging, fluorescence and
                     pan-tilt mount                      optical access exists                      contamination may limit results

  NIR (optional)     Near-infrared spectrometer          Bulk material screening through some       Not a substitute for trace detection or
                                                         packaging                                  forensic confirmation

  E-nose             Gas-sensor array, pump,             Broad anomaly indication and               Not definitive substance identification
                     humidity/temperature                prioritised inspection
                     compensation

  Metal detector     EMI/magnetic anomaly sensor         Hidden metal, wiring and metallic          Cannot detect non-metallic threats
                                                         anomalies                                  alone

  GNSS/UWB           GNSS outdoors; UWB/beacons          Event tagging and improved indoor          GNSS unavailable in tunnels and many
                     indoors                             positioning                                covered areas

 5. AI, Analytics and Decision Support
 5.1 Vision and thermal analytics
- Objectdetectionfor people,luggage,parcels, vehicles, track obstacles and restricted-zone intrusions.
- Multi-object tracking to identify unattended baggage using location, owner association and dwell-time logic.
- Underframe/coach inspection using image comparison and anomaly-detection models trained on approved
     inspection imagery.
- Thermal anomaly detection for unusual heating, fire/smoke indicators and night-time situational awareness.
- Optical character recognition for coach identifiers, parcel labels and station-area markers where permitted.
- Facial matching should be optional, access-controlled, legally authorised and operated only against approved

     watchlists.
 5.2 Chemical-sensor fusion
 Chemicaloutputsshould be treated as confidence-scored alerts. The fusion engine combines IMS peak information,
 Raman/NIR spectra, e-nose anomaly scores, location, sampling method and sensor-health status. It should explicitly
 support inconclusive and repeat sample outcomes rather than forcing a positive/negative declaration.

  Output Field                            Example

  Result category                         Suspected explosive; suspected narcotic; no alert; inconclusive

  Confidence                              Low / medium / high with a calibrated threshold

  Evidence source                         IMS swab, Raman scan, NIR scan, e-nose anomaly or combined result

  Context                                 Robot/device ID, operator ID, location, timestamp, camera clip reference

  Required action                         Rescan, isolate area, supervisor review, EOD/RPF escalation

 6. Navigation and Mission Software

 RailGuard should run a ROS 2 graph in which each sensor publishes time-stamped data, a localisation layer produces
 the robot pose, and Nav2 plans and controls a safe path. LiDAR, IMU, visual odometry and leg/joint odometry should
 be fused using an Extended Kalman Filter or factor-graph approach.

  ROS 2 Module                                   Function

  Sensor driver nodes                            Acquire LiDAR, cameras, thermal imagery, IMU, GNSS, IMS/Raman status and motor
                                                 telemetry

  robot_state_publisher                          Publishes robot body and leg transforms

  robot_localization                             Fuses IMU, visual, LiDAR and leg-odometry data

  slam_toolbox                                   Builds and updates a map in GPS-denied station, tunnel and yard environments

  Nav2 planner/controller/costmaps               Plans routes, avoids obstacles and manages motion constraints

  Quadruped gait controller                      Converts body-motion commands into leg motions while enforcing stability limits

  Mission manager                                Runs patrol, inspection, return-to-base and alert-response workflows

  Safety supervisor                              Monitors e-stop, tilt, collision, lost-communications, low-battery and fault conditions

 7. Handheld Detection Device
  Area                                 Recommended Details

  Form factor                          Target below 1.5 kg; drop-resistant, weather-resistant, sunlight-readable 5–7 inch touch display

  Core sensing                         IMS for trace swab/vapour screening; Raman or NIR for material screening; temperature/humidity
                                       monitoring

  Processing                           Industrial ARM processor with secure element; optional small AI accelerator

  User alerts                          Buzzer, vibration, high-visibility LED, text result and confidence indicator

  Connectivity                         4G/5G, Wi-Fi, Bluetooth Low Energy; secure store-and-forward when disconnected

  Offline operation                    Encrypted local database, timestamping, device/operator ID and automatic sync when a network
                                       returns

  Languages                            Hindi and English first; modular localisation for regional languages

  Audit trail                          Scan ID, sample type, location, operator acknowledgement, calibration state and chain-of-custody
                                       fields

 8. Communications, Dashboard and Data
 8.1 Communications
- Primary communications: encrypted 4G/5G or private LTE; local station Wi-Fi 6 where authorised.
- Fallback communications: secured mesh radio for commands, health telemetry and emergency alerts.
- Use adaptive video streaming: preserve control and alerts first, then reduce video bitrate during poor connectivity.
- Use store-and-forward queues so incidents are not lost during tunnel, yard or network outages.

 8.2 Control-centre dashboard
- Live position of robot andhandheld assets on station, yard or geographic maps.
- Live RGB and thermal streams with device health, battery, link quality and sensor-calibration state.
- Alert queue showing incident level, confidence, sensor evidence, time, location, operator and recommended
     escalation.
- Searchable encrypted incident history, patrol replay, maintenance schedule and exportable incident reports.
- Role-based views for field officer, station supervisor, divisional officer and system administrator.

 9. Cybersecurity, Privacy and Safety
  Control                                   Implementation

  Secure device identity                    Hardware-rooted identity, secure boot and signed firmware/model packages

  Data protection                           AES-256 encryption at rest; TLS 1.3/mutual authentication in transit

  Access control                            Role-based access, strong authentication, audit logs and no default credentials

  Network separation                        Separate control, video, chemical-alert and administrative networks

  Privacy controls                          Purpose limitation, retention policy, access audit and legally approved workflow for biometric data

  Functional safety                         Physical e-stop, remote stop, collision avoidance, speed limits near public areas and fall detection

  Fail-safe behaviour                       Stop/hold, return to safe point or controlled shutdown after critical fault, low battery or loss of control
                                            link

  Incident handling                         No autonomous evidence handling; trained RPF/EOD staff verify and manage suspicious items

 10. Prototype Build Plan
  Phase                 Work Package                                                          Main Deliverable

  1. Core platform      Mobility integration, e-stop, power management and                    Safe controllable quadruped base
                        teleoperation

  2. Navigation         LiDAR, IMU, cameras, mapping and obstacle avoidance                   Indoor/outdoor GPS-denied patrol demonstration

  3. Perception         RGB/thermal analytics and event logging                               Unattended-object, intrusion and anomaly
                                                                                              demonstration

  4. Chemical           Integrate approved commercial/lab IMS and Raman/NIR                   Sensor health, scan workflow and confidence alerting
  interface             interface

  5. Handheld           Rugged handheld UI, offline store and synchronisation                 Field-operable screening workflow

  6. Backend            Encrypted messaging, dashboard and role-based access                  Central alert and fleet-management platform

  7. Validation         Dust, heat, vibration, low-light, outage and battery tests            Test evidence and deployment readiness report

 11. Recommended Prototype Bill of Materials
  Item                       Prototype Recommendation                                      Notes

  Quadruped base             Commercial research/developer platform or                     Prefer a platform with documented SDK, payload
                             indigenous actuator prototype                                 capacity and e-stop

  Edge computer              Jetson Orin NX development carrier                            Scale to AGX Orin/industrial system for multi-camera
                                                                                           production configuration

  LiDAR                      One 3D top-mounted LiDAR plus short-range                     Choose industrial-grade interface and environmental
                             coverage                                                      sealing

  Item                    Prototype Recommendation                             Notes

  Vision                  Front RGB, side/rear cameras, low-light camera and   Synchronise timestamps where possible
                          thermal unit

  Chemical module         Commercial IMS and Raman/NIR interface               Use certified reference/testing arrangements; do not
                                                                               manufacture or handle prohibited materials

  Network                 4G/5G router, Wi-Fi 6, radio fallback                Use external, protected antennas

  Power                   Hot-swap battery, BMS, isolated DC-DC rails          Size power budget for peak actuator load and sensor
                                                                               payload

  Mechanical              Aluminium/composite enclosure, vibration mounts,     Maintain serviceability and safe centre of gravity
                          mast and pan-tilt

 12. Testing and Acceptance Criteria
- Navigation:autonomousmappingandsupervisedpatrolinaGPS-denied indoor test route; safe stop for people and
     obstacles.
- Mobility: stable movement on representative railway-like uneven terrain without sensor-mast instability.
- Perception: measurable detection/false-alarm metrics for packages, intrusion and low-light conditions.
- Chemical workflow: calibration, blank checks, known safe reference materials, repeatability and documented
     false-alarm testing by authorised experts.
- Communications: alert delivery with delayed/offline queue recovery; no loss of audit records after a network
    interruption.
- Cybersecurity: signed updates, credential management, encrypted storage and access-log verification.
- Operational usability: RPF-oriented UI trial with short training, clear alarms and documented escalation SOP.

 13. Final Recommended Architecture
 Robotlayer: Ruggedquadruped+Jetsonedgecomputer+ROS2+ LiDAR/IMU/camera fusion + Nav2/SLAM +
 RGB/thermal surveillance + IMS/Raman/NIR sensor interfaces.

 Handheld layer: Rugged encrypted field device + IMS and Raman/NIR workflow + offline-first records + multilingual
 alert interface.

 Command layer: MQTT/DDS telemetry + FastAPI/Node services + PostgreSQL/PostGIS + React dashboard +
 encrypted video/event storage.

 Safety layer: Human-supervised operations, independent emergency stop, confidence-scored chemical alerts,
 cybersecurity controls and RPF/EOD verification before response actions.

 References and Technical Basis
 The design uses ROS2 Nav2 and SLAMToolboxformapping/navigation; NVIDIA Jetson Orin for edge robotics AI;
 and IMS with Raman/NIR as complementary field-screening approaches for explosives and narcotics. Final production
 selection must be validated through accredited laboratory testing, environmental trials and Railway/RPF procurement
 and safety approvals.
