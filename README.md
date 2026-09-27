# Space Bunny: Three Real-World AI Coding Tests

![Model](https://img.shields.io/badge/Model-Space%20Bunny%20Free-7c3aed?style=for-the-badge)
![Projects](https://img.shields.io/badge/Projects-3-06b6d4?style=for-the-badge)
![Tools](https://img.shields.io/badge/Tools-OpenCode%20%7C%20Hermes-f59e0b?style=for-the-badge)

> A reproducible companion to the NetworkCoder video testing Space Bunny across interactive 3D graphics, full-stack application development, and real-time game logic.

---

## 📺 Watch the Video

[![Watch on YouTube](https://img.shields.io/badge/▶_Watch_the_Full_Test-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](YOUR_YOUTUBE_VIDEO_URL)

The video follows three practical builds:

1. **VANTA R7** — an interactive 3D car configurator
2. **SignalTrace** — a full-stack threat-intelligence platform
3. **Driftline Convoy** — a playable 3D delivery game

This repository contains the prompts, setup notes, validation workflow, observed results, and limitations used in the video.

---

## What Is Space Bunny?

Space Bunny Free was available through [OpenCode Zen](https://opencode.ai/docs/en/zen/) at the time of testing.

```text
Model ID: space-bunny-free
Provider used: OpenCode Zen
```

OpenCode also provides a public [Space Bunny usage page](https://stats.opencode.ai/data/unknown/space-bunny).

At the time of recording, the model creator, architecture, parameter count, training process, and official benchmark results had not been publicly confirmed. This repository therefore focuses on observed behaviour rather than speculation about the model's identity.

---

## Test Configuration

| Project | Agent interface | Provider | Reasoning setting |
|---|---|---|---|
| VANTA R7 | OpenCode | OpenCode Zen | Max |
| SignalTrace | Hermes Agent | OpenCode Zen | Medium (default) |
| Driftline Convoy | Hermes Agent | OpenCode Zen | Medium (default) |

These projects are practical capability tests, not controlled benchmarks. Differences between projects must not be attributed only to the reasoning setting because the prompts, tools, and workloads also changed.

---

## Results at a Glance

| Project | Main challenge | Verified outcome | Important limitation |
|---|---|---|---|
| VANTA R7 | Procedural 3D rendering and connected interactions | Working car controls, cameras, animation, pricing, save, and JSON export | Stylized procedural geometry rather than production automotive CAD |
| SignalTrace | Frontend, API, database, imports, and analytics | Connected UI, Python API, SQLite persistence, CSV preview/import, filtering, gap analysis, and report export | Synthetic data; no production authentication or security hardening |
| Driftline Convoy | Real-time vehicle, camera, route, cargo, and scoring state | Playable delivery loop with manual driving, route planning, cameras, autopilot, and scoring | Low-poly prototype with handling and camera behaviour that need refinement |

---

## Project 1 — VANTA R7

### Interactive 3D Car Configurator

VANTA R7 is a browser-based automotive configurator featuring a procedurally generated electric sports car inside a virtual showroom.

### Verified Features

- Manual vehicle orbit and zoom
- Multiple paint finishes
- Three wheel designs
- Animated doors
- Independent exterior and cabin lights
- Exterior, front, rear, and interior camera views
- Automated cinematic tour
- Live specifications and dynamic pricing
- Local configuration saving
- JSON configuration export

<details>
<summary><strong>View the VANTA R7 build prompt</strong></summary>

```text
Build an original interactive 3D automotive configurator called
“VANTA R7 — Electric Performance Studio” inside the current empty folder.

Create a complete browser application, not a static concept page or a
pre-rendered animation. The main product must be an original electric sports
car generated procedurally in code using Three.js or React Three Fiber. Do not
download or embed an existing car model.

The vehicle should be displayed in a premium virtual showroom with controlled
lighting, reflections, a presentation platform, a clean automotive interface,
and responsive desktop behaviour.

Required vehicle interactions:

- Mouse or pointer orbit and zoom
- Multiple selectable paint finishes
- Three visibly different wheel designs
- Animated left and right doors
- Independent headlights and cabin lighting
- Start and stop turntable rotation
- Exterior, front, rear, and interior camera presets
- A smooth automated cinematic camera tour

Required configuration features:

- Live vehicle specifications
- Dynamic pricing connected to selected options
- Local persistence for the selected configuration
- A Save action that survives a browser refresh
- JSON export containing the complete configuration
- A reset action that restores the default build

Organize the application into maintainable systems for vehicle geometry,
showroom rendering, camera behaviour, configuration state, animations, and UI.
Every visible control must be connected to working application logic. Avoid
decorative buttons that do nothing.

Continue beyond planning: create the project, install the required packages,
implement the complete experience, launch it in the browser, test every
interaction, inspect runtime errors, and fix important visual or functional
problems before stopping.
```

</details>

### Run Locally

```powershell
cd "Vanta-Showroom"
npm install
npx vite --host=127.0.0.1 --port=4173
```

Open `http://127.0.0.1:4173/`.

### Validation Checklist

- Change paint and confirm the vehicle updates immediately.
- Change wheels and confirm both appearance and price update.
- Test both doors and both lighting systems.
- Test every camera preset and the cinematic tour.
- Save a configuration, refresh, and confirm it persists.
- Export the build and inspect the downloaded JSON.

---

## Project 2 — SignalTrace

### Full-Stack Threat-Intelligence Platform

SignalTrace explores security events, assets, identities, vendors, and monitoring gaps through a connected React frontend, Python API, and local database.

> **Data notice:** All indicators, people, vendors, and events used in this demonstration are synthetic. No external threat feed or real customer environment is connected.

### Verified Features

- Security overview and threat feed
- Asset, identity, and vendor exploration
- Search, filtering, risk levels, and confidence values
- Python API and SQLite persistence
- CSV upload with validation and preview
- Confirm-before-import workflow
- Coverage-gap and exposure analysis
- Downloadable report export
- API health and route verification

<details>
<summary><strong>View the SignalTrace build prompt</strong></summary>

```text
Build an original full-stack threat-intelligence workspace called SignalTrace.
It must be a connected application rather than a static dashboard or mock-up.

Create a polished React frontend for security analysts to explore assets,
identities, vendors, incidents, and normalized external security signals.
Create a Python FastAPI backend and use a local SQLite database for persistence.

Required application areas:

- Security overview dashboard
- Threat-feed table with search and compound filters
- Assets and exposed-service views
- Identity records, including privileged and matched status
- Vendor records with criticality and risk context
- Investigations and incident views
- Exposure and coverage-gap analysis
- Reports page with downloadable export

Required data workflow:

- Accept CSV threat-event uploads
- Parse and validate the uploaded structure
- Show a row preview before writing anything
- Display useful validation errors and warnings
- Require explicit confirmation before import
- Store confirmed records in the active database
- Refresh dashboard and analytics data after import
- Preserve imported data across browser refreshes and backend restarts

Required engineering behaviour:

- Expose documented API endpoints
- Connect every dashboard value to backend data
- Support useful search, filtering, pagination, and empty states
- Include health checks and reproducible seed/demo data
- Clearly label the environment as simulated and synthetic
- Avoid hard-coded dashboard totals presented as live API values

Add automated backend and frontend tests where practical. Launch both services,
test the CSV preview and confirmation flow end to end, verify identity and vendor
routes, generate a report, and resolve runtime, database-path, and integration
errors before stopping.
```

</details>

### Run the Backend

```powershell
cd "SignalTrace\backend"
python -m pip install -r requirements.txt
python -m uvicorn app.main:app --host 127.0.0.1 --port 8000
```

API documentation: `http://127.0.0.1:8000/docs`

### Run the Frontend

```powershell
cd "SignalTrace\frontend"
npm install
npx vite --host=127.0.0.1 --port=4174
```

Open `http://127.0.0.1:4174/`.

### Sample Import

The sample file used during testing was:

```text
SignalTrace/datasets/threat_events_sample_import.csv
```

Test sequence:

1. Note the current threat-feed count.
2. Open **Threat Feed** and select **Import signals**.
3. Upload `threat_events_sample_import.csv`.
4. Review parsed rows, column validation, warnings, and errors.
5. Confirm the import only after validation succeeds.
6. Verify that dashboard and feed values update.
7. Refresh the page and confirm that imported data remains.
8. Test identity and vendor searches, filters, exposure gaps, and report export.
9. Use the API documentation or included health-check script to verify backend routes.

### Database Note

During testing, one backend run was connected to an empty SQLite database while an earlier run had used a database containing event data. After identifying the active database and importing the sample dataset again, the dashboard updated correctly and the API checks passed.

This highlights an important validation lesson: a polished interface does not prove that the active backend and database contain the expected data.

---

## Project 3 — Driftline Convoy

### Playable 3D Delivery Simulation

Driftline Convoy is an original low-poly driving prototype built around route planning, cargo delivery, manual control, and autopilot.

### Verified Features

- Controllable 3D rover
- Steering, acceleration, and braking
- Route map and path selection
- Cargo pickup and delivery
- Multiple camera views
- Pause and restart controls
- Route-following autopilot
- Delivery time, fuel, cargo condition, and final scoring

<details>
<summary><strong>View the Driftline Convoy build prompt</strong></summary>

```text
Build an original playable 3D logistics game called “Driftline Convoy” inside
the current empty folder.

Create a complete browser game rather than a static 3D scene or an animated
background with decorative controls. Use React and Three.js or React Three
Fiber to create a readable low-poly world and a working vehicle-delivery loop.

Core gameplay loop:

1. Review the mission and cargo.
2. Inspect the route map.
3. Select or understand a delivery path.
4. Drive the rover manually or activate autopilot.
5. Reach the delivery point with the cargo intact.
6. Receive a final performance score.

Required systems:

- Responsive vehicle steering, acceleration, braking, and reverse
- A visible route through the environment
- Route-planning or route-selection interface
- Cargo state and delivery destination
- Multiple useful camera views
- Pause, resume, restart, and clear gameplay instructions
- Autopilot that follows the intended route instead of only moving forward
- Delivery completion state
- Scoring based on time, fuel, cargo condition, and mission completion
- HUD showing the information needed to play
- Environmental movement and visual feedback that make the world feel active

Keep the camera, vehicle, route, cargo, scoring, and pause state synchronized.
Prevent common failures such as stuck vehicles, off-route autopilot, broken
restart behaviour, camera clipping, and a mission that cannot be completed.

Continue until the game is playable from start to finish. Launch it in the
browser, complete at least one manual or assisted delivery, test every camera
and control, verify the final score, and fix serious runtime or gameplay issues
before stopping.
```

</details>

### Run Locally

```powershell
cd "Driftline-Convoy"
npm install
npx vite --host=127.0.0.1 --port=4175
```

Open `http://127.0.0.1:4175/`.

### Validation Checklist

- Complete the opening instructions or briefing.
- Test manual steering, acceleration, braking, and reverse.
- Inspect the route map and confirm the route is readable.
- Switch through every camera view.
- Pause and resume without losing the mission state.
- Activate autopilot and confirm the rover follows the route.
- Complete a delivery and verify the final scoring breakdown.

---

## Suggested Repository Structure

```text
space-bunny-real-world-builds/
├── README.md
├── prompts/
│   ├── 01-vanta-r7.md
│   ├── 02-signaltrace.md
│   └── 03-driftline-convoy.md
├── sample-data/
│   └── threat_events_sample_import.csv
├── screenshots/
└── results/
    └── test-notes.md
```

The generated application source can be published separately if desired. Do not upload local databases, credentials, environment files, dependency folders, or machine-specific paths.

---

## Practical Takeaways

- Detailed prompts mattered, especially for 3D work.
- Visual quality varied and still required human judgment.
- Browser testing was essential because a good screenshot could hide broken controls.
- Full-stack validation required checking the live API and active database, not only the frontend.
- The strongest result was the model's ability to work across many files, install packages, run commands, inspect failures, and continue refining the project.
- AI-generated code still requires security review, dependency review, testing, and production hardening.

---

## Important Limitations

- These are prototypes, not production products.
- The three tests used different prompts and two agent interfaces.
- VANTA used Max reasoning; SignalTrace and Driftline used Medium.
- The tests were not repeated enough to measure reliability statistically.
- SignalTrace uses synthetic data and is not connected to a commercial threat feed.
- No claim is made about the model's undisclosed architecture or creator.
- Availability and free access may change after the recording date.

---

## Reproduce the Tests

1. Install [OpenCode](https://opencode.ai/docs/).
2. Connect the OpenCode Zen provider.
3. Select `space-bunny-free` if it is still available.
4. Create a new empty folder for the chosen project.
5. Paste the corresponding prompt without removing its validation requirements.
6. Let the agent implement, launch, test, and refine the application.
7. Verify every claimed feature manually before evaluating the result.

Because model availability, agent tooling, dependencies, and generated output can change, another run may not reproduce the exact same interface or implementation.

---

## About NetworkCoder

NetworkCoder publishes practical AI engineering tests focused on working applications, reproducible workflows, honest limitations, and real execution evidence.

- YouTube: `YOUR_CHANNEL_URL`
- Video: `YOUR_YOUTUBE_VIDEO_URL`

If you reproduce one of these tests, share what worked, what failed, and what the model built differently in your environment.

---

## Disclaimer

This repository is provided for educational and testing purposes. Review generated code and dependencies before running them, use only synthetic security data, and do not deploy these prototypes to production without appropriate engineering and security review.
