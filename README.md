# ⚡ CPU Scheduling Algorithm Simulator

> **12-Hour College Hackathon Project**  
> _Target Audience:_ 3rd-Semester B.Tech Computer Science Students & Hackathon Examiners  
> _Tech Stack:_ Pure HTML5, CSS3, Vanilla JavaScript (Zero External Dependencies, 100% Offline Ready)

---

## 📌 1. Project Title

**CPU Scheduling Algorithm Simulator & Performance Benchmark Tool**

---

## 🎯 2. Problem Statement

In modern operating systems, CPU scheduling determines the order in which processes access CPU execution time. Understanding how different scheduling algorithms (FCFS, SJF, Priority, Round Robin) affect process throughput, turnaround time, waiting time, and CPU utilization is a fundamental concept in Computer Science.

This web application provides an interactive, visual simulator that executes a given set of process workloads against all four standard CPU scheduling algorithms simultaneously, rendering chronological Gantt charts, detailed performance metric tables, comparative benchmark charts, and a step-by-step process state visualizer.

---

## 🚀 3. Objectives

- Implement standard textbook versions of FCFS, SJF (non-preemptive), Priority (non-preemptive), and Round Robin (preemptive).
- Handle arbitrary process arrival times, CPU idle periods, preemption, context switching, and deterministic tie-breaking.
- Automatically calculate Completion Time ($CT$), Turnaround Time ($TAT$), Waiting Time ($WT$), Average $WT$, and Average $TAT$.
- Render visual Gantt charts and side-by-side comparative charts.
- Offer an intuitive, zero-dependency web interface suitable for a 3–5 minute live demo to examiners.

---

## ✨ 4. Key Features

- **Dynamic Process Management**: Add, delete, edit, or clear processes easily.
- **Preset Test Case Workloads**: Instant loading of 7 standard textbook test cases (staggered arrivals, idle gaps, ties, Round Robin rotations).
- **Interactive Round Robin Quantum**: Real-time adjustment of Time Quantum ($TQ$) with instant recalculation.
- **Visual Gantt Charts**: Rendered with start/end time markers, hover tooltips, and distinct process color-coding (including CPU IDLE periods).
- **Comprehensive Results Table**: Displays $CT$, $TAT$, and $WT$ per process, plus aggregate averages.
- **Automatic Algorithm Comparison**: Side-by-side metric comparison table and custom visual bar chart.
- **Performance Recommendation Engine**: Identifies best-performing algorithms for the current input based on minimum average waiting time.
- **Process State Stepper (Innovation Feature)**: Interactive timeline slider showing process movement across **Ready Queue $\rightarrow$ Running on CPU $\rightarrow$ Completed**.
- **Strong Input Validation**: Catches empty IDs, duplicate IDs, negative arrival times, non-positive burst times, and invalid time quanta before execution.

---

## 🧠 5. Algorithms Implemented

1. **First-Come, First-Served (FCFS)**: Non-preemptive scheduling based strictly on arrival order.
2. **Shortest Job First (SJF)**: Non-preemptive scheduling selecting the ready process with the shortest burst time.
3. **Priority Scheduling**: Non-preemptive scheduling selecting the ready process with the highest priority (lowest numerical priority value).
4. **Round Robin (RR)**: Preemptive scheduling allocating CPU time in fixed slices ($TQ$).

---

## 📋 6. Scheduling Assumptions

- **Preemption Types**: FCFS (Non-preemptive), SJF (Non-preemptive), Priority (Non-preemptive), Round Robin (Preemptive).
- **Priority Convention**: Lower numerical value indicates higher priority (e.g., Priority 1 > Priority 3).
- **Tie-Breaking Rule**: When two ready processes are equal in selection criteria (e.g., equal BT or Priority), tie is broken by:
  1. Earlier Arrival Time ($AT$)
  2. Smaller Process ID (alphanumeric order, e.g., P1 before P2).
- **CPU Idle State**: If no process has arrived by current time $t$, CPU remains idle until the next arrival.
- **RR Queue Management**: Processes arriving during an active time quantum are added to the ready queue _before_ the current pre-empted process is re-enqueued.

---

## 📐 7. Mathematical Formulas

$$\text{Turnaround Time (TAT)} = \text{Completion Time (CT)} - \text{Arrival Time (AT)}$$

$$\text{Waiting Time (WT)} = \text{Turnaround Time (TAT)} - \text{Burst Time (BT)}$$

$$\text{Average Waiting Time} = \frac{\sum_{i=1}^{N} \text{WT}_i}{N}$$

$$\text{Average Turnaround Time} = \frac{\sum_{i=1}^{N} \text{TAT}_i}{N}$$

---

## 🛠️ 8. Tech Stack

- **Frontend**: HTML5, CSS3 (Modern Flexbox/Grid, Dark Theme, Custom Bar Charts), Vanilla JavaScript (ES6+).
- **Testing**: Node.js automated unit test suite.
- **Dependencies**: **Zero external dependencies** (no npm install, no CDN link required, runs 100% offline).

---

## 📁 9. Project Structure

```
cpu-scheduling-simulator/
├── index.html           # Main Application UI Entry Point
├── src/
│   ├── css/
│   │   └── style.css    # Custom Dark Theme & Responsive Stylesheet
│   └── js/
│       ├── simulator.js # Decoupled Algorithm Logic (FCFS, SJF, Priority, RR)
│       └── app.js       # UI Event Handler, Chart Renderer, & Stepper Engine
├── tests/
│   ├── test-runner.js   # Automated Node.js Unit Test Suite
│   └── test-cases.md    # Hand-Calculated Verification & Examiner Reference
└── README.md            # Comprehensive Hackathon Documentation
```

---

## 💻 10. How to Run

### Option 1: Directly in Browser (No Server Required)

1. Double click `index.html` or right-click `index.html` $\rightarrow$ **Open with Browser** (Chrome / Firefox / Edge / Safari).
2. The application opens immediately and is ready for interaction.

### Option 2: Using Node.js Local HTTP Server (Optional)

```bash
# Navigate to project directory
cd cpu-scheduling-simulator

# Run local web server using npx or python
npx serve .
# OR
python -m http.server 8000
```

Then open `http://localhost:8000` in your web browser.

---

## 🧪 11. Testing & Verification

Run the automated Node.js test suite to verify algorithm correctness:

```bash
node tests/test-runner.js
```

### Verified Test Cases:

1. **TC1: All Processes Arriving at $t=0$** (Verified against Silberschatz OS textbook).
2. **TC2: Staggered Arrival Times** (Proves dynamic process selection at time $t$).
3. **TC3: CPU Idle Time Handling** (Proves accurate timeline gap creation).
4. **TC4 & TC5: Equal Burst Times & Equal Priorities** (Verifies deterministic tie-breaking).
5. **TC6: Round Robin Multiple Rotations** (Verifies preemption & quantum slices).
6. **TC7: Mid-Execution Arrival** (Verifies strict FIFO ready queue insertion order).
7. **TC8: Single Process Execution**.
8. **TC9: Input Validation Edge Cases** (Negative AT, Zero BT, Duplicate IDs, Invalid TQ).

---

## 👥 12. Team Contribution Placeholders

- **Team Member 1**: Core Algorithm Implementation (`simulator.js`) & Unit Testing.
- **Team Member 2**: Frontend Dashboard Design, CSS Styling, & Gantt Chart Component.
- **Team Member 3**: Interactive Comparison Engine, Stepper Visualizer, & Documentation.

---

## 🔮 13. Future Scope

- Support for Preemptive Shortest Remaining Time First (SRTF) and Preemptive Priority Scheduling.
- Multilevel Queue (MLQ) and Multilevel Feedback Queue (MLFQ) visualization.
- Export results to CSV or PDF report for lab submission.
