Session-Aware Liquidity & Sweep Detection
A Thinkorswim/ThinkScript portfolio project focused on requirements analysis, QA/UAT, state logic, debugging, session handling, and decision-support design.
Project Overview
I designed and iteratively refined a small family of ThinkScript studies that organizes prior-day, current-session, and overnight liquidity reference levels and adds a configurable sweep/reclaim detector.
The project grew from a simple chart-navigation need into a modular session-aware workflow with explicit rules for when levels form, when they become valid, how long they remain active, and what constitutes a qualifying sweep event.
The system is intended as a decision-support and review tool, not as a standalone trading signal or a claim of predictive performance.
Working System
 ![Session-Aware Liquidity Reference System](Screenshot%202026-10-06%20013515.png)
Working-state chart view showing the session-aware liquidity workflow. Yellow lines mark prior-day high/low references, while cyan lines mark overnight high/low levels. The system keeps these session references structured and visible so sweep/reclaim events can be evaluated consistently.
Modular Study Family
The project is implemented as a coordinated group of ThinkScript studies rather than one monolithic indicator:
- d_ICT_PrevDayHighLow_Liquidity_Map — prior-day regular-session high/low references
- d_ICT_current_day_High_Low — current-session high/low tracking
- d_ICT_overnight_liquidity_maps — completed overnight high/low references
- d_ICT_Sweep_Detection_Label — configurable sweep/reclaim detection and status output
 ![Modular Session and Liquidity Study Stack](Screenshot%202026-10-06%20013323.png)
Configuration view showing the coordinated study stack. Separate modules handle prior-day levels, current-session levels, completed overnight levels, and sweep/reclaim detection.
Sweep Detection Logic
The sweep detector can be configured to:
- monitor prior-day and overnight levels
- require a minimum pierce distance
- optionally require price to close back through the level
- use explicit regular-session and overnight timing
- limit accepted events per session
- display persistent status information
- show historical sweep markers
 ![Sweep Detection Configuration](Screenshot%202026-10-06%20013253.png)
Configuration view of the sweep detector, including prior-day and overnight level selection, minimum pierce distance, optional close-back-through confirmation, session timing, one-signal controls, status labels, and historical sweep bubbles.
Development and QA
The strongest part of the project is the iterative QA/UAT process used to refine behavior.
Testing uncovered issues including:
- ambiguous session ownership and timing
- state persistence and session reset behavior
- a self-blocking event-state defect
- event-only output that could make the study appear inactive even while it was monitoring correctly
- differences between stocks/ETFs and futures session behavior
- the need to distinguish “no event yet” from “study is not working”
A later remediation separated event permission from state updates, added persistent monitoring/status output, preserved historical event markers, and refined session targeting.
The current sweep-detector version compiled successfully in Thinkorswim and produced persistent status output plus plausible historical PDH/PDL and ONH/ONL sweep markers during a basic visual smoke test.
AI supported ThinkScript implementation, debugging hypotheses, and documentation. Requirements, live testing, acceptance decisions, and final validation remained human-controlled.
Skills Demonstrated
- Requirements Analysis
- Quality Assurance
- User Acceptance Testing (UAT)
- Troubleshooting
- State-Machine Reasoning
- Workflow Design
- Systems Thinking
- Decision-Support UX
- ThinkScript
- Technical Documentation
- AI-Assisted Prototyping
Project Evidence
This public repository contains selected portfolio-safe evidence showing:
1. the working session/liquidity reference system
2. the modular study architecture
3. the configurable sweep-detection logic
Additional historical development screenshots, source variants, and testing evidence remain in the private project archive.
Scope and Limitations
This is a technical development and QA portfolio case study.
A detected sweep is not treated as a guaranteed reversal or trade signal. No claim is made regarding predictive accuracy, hit rate, backtested alpha, profitability, or P&L improvement.
