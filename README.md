# Hopper
A series of training modules designed to build GNC fundamentals in Rust and apply them in GTPL Fall 2026 Deliverables

## Block A · Sim tooling (Sep 28 – Oct 11)
- Week of Sep 28: build and run rust_rocket_sim and Lander locally. Do Hopper M0. Read simulation.rs and main.rs end to end. Ask on #53 exactly what it covers.
- Week of Oct 5: open the FS #1 pull request (MCAP logging of truth, estimate and commands in Simulation::step). Then the headless part of #53: replace the hard-coded mode_tune = false switch in main.rs with a CLI flag or config that defaults to headless tuning, then verify the same run is deterministic.
- Done when: cargo run --release -- --headless --seed 7 --mcap out.mcap flies a full mission with no viewer, two runs produce identical files, and the log opens in Foxglove.
- Why first: control #1 says to "use the Rust simulation in headless mode." A tuner is only trustworthy if the same weights always get the same score.

## Block B · Control tuning (Oct 12 – Nov 1)
- Week of Oct 12: the PID, LQR and MPC sections of the team's training page, plus exercise 1. Do Hopper M1. Read the MPC report the issue mentions (Hansel's) and rust_rocket_sim/src/mpc_tuning.rs.
- Week of Oct 19: Hopper M4 (LQR) and exercise 2, so you know what each Q and R weight trades off. Write the flight-scoring function the issue asks for, as a pure function over one flight log.
- Week of Oct 26: Hopper M7 (Monte Carlo with rayon) and exercise 3. Run the search on the issue's starting case, a straight vertical descent from 50 m.
- Done when: the tuning program outputs a weight set and a short report comparing it with the current per-phase default weights, averaged over at least 20 seeds.

## Block C · Estimation (Nov 2 – Nov 22)
- Week of Nov 2: Hopper M2. Post the FS #4 design note in #gnc, then open the PR.
- Week of Nov 9: Hopper M3. Open the FS #2 PR: readings stay None until real data arrives, and the navigator skips prediction without them.
- Week of Nov 16: Hopper M6. Nav #1: the LiDAR measurement model and its Jacobian tests.
- Done when: all three PRs are open, each with tests and a before/after plot from the sim.

## Block D · Architecture and timing (Nov 23 – Dec 11)
- Week of Nov 23 (Thanksgiving): Hopper M5. Read #54 and claim the sensor and plant interface piece, reusing the ImuSource design from FS #4.
- Week of Nov 30: Hopper M8. FS #3: measure loop timing and write up the findings.
- Week of Dec 7 (finals): get the #54 piece into review or leave it as a draft PR, with hand-off notes on each issue.
- Done when: the FS #3 write-up is posted and the #54 piece is in review.
