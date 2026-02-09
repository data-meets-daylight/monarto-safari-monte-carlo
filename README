# Safari Park Shuttle Bus Wait-Time Simulation (Monarto) 🦁🚌
Year: 2026

_A Monte Carlo simulation testing shuttle-bus boarding policies on a 7-stop safari loop to reduce downstream consecutive “unable to board” events due to no seats available and improve visitor experience on peak days - built as a proof of concept from observations (no official park data yet)._

## Project Overview
Monarto Safari Park uses a shuttle bus loop to move visitors between exhibits. On a hot, busy day I noticed a pattern: buses filled up at the Visitor Centre (Stop 7), then arrived at downstream stops already full. Larger families were hit hardest because groups board as a unit (no splitting), so a full bus can repeatedly block them.

This project is a Monte Carlo simulator of the bus loop that compares two simple boarding policies:
- **Fill All Seats**: fill buses to full capacity at the first stop whenever there is demand
- **Reserve 5 Seats**: deliberately hold back 5 seats at the first stop to protect downstream capacity

**Proof-of-concept note:** This simulator uses best-guess assumptions to reproduce the mechanics of the system I experienced (capacity limits, group boarding, downstream stops and random alighting). The absolute numbers will shift when calibrated with real park inputs, but the simulator is built to compare policies fairly and identify which rules reduce tail-risk and improve downstream access.

## Key Technical Highlights
- **Monte Carlo simulation** over 1,200 peak-day runs per policy (apples-to-apples comparison)
- **Discrete-event style bus loop** (staggered bus starts, fixed headway, fixed segment times)
- **Group-based boarding logic** (groups do not split, capacity constraints enforced). Groups are assigned randomly between simulation runs using a normal distribution.
- **Stop-specific churn** probabilities (groups alight at stops based on configurable probabilities)
- **Dwell time modelling** (groups rejoin queues after an exhibit visit delay)
- **Tail-risk focus** using an exceedance (survival) curve to compare severe-day outcomes and can be used to compare multiple boarding policies at once. 

## Plot Outputs
To support decision making:  

![Plot 1: Tail Exceedance Curve](/Outputs/plot1-exceedance-tail-curve.png)

![Plot 2: Stacked Bar Chart](/Outputs/plot2-stacked-bar-chart.png)

![Plot 3: Radar](/Outputs/plot3-radar.png)

## Features

### Feature 1
**Policy testing framework**
- Swap in different seat-reserve policies (and extend to more stops) without rewriting the simulation core
- Parameters are easy to adjust from a single location in the code

### Feature 2
**Fair comparison via reproducible runs**
- Each `run_id` uses the same random seed across policies so the “same day” is tested under different rules

### Outputs
The project produces three main visuals:
1. **Exceedance Tail Curve** - probability a day is “this bad or worse” (severity score based on worst consecutive missed boardings)
2. **Stacked Bar Chart (Bad Day P95)** - maximum consecutive “unable to board” runs by group size band (with 0s removed for clarity)
3. **Radar Charts (Typical vs Bad Day)** - total downstream refused-boardings by stop to identify pinch points

## Dependencies
- Python 3.x
- numpy
- pandas
- matplotlib

## How to Run
1. Clone the repo
2. Install dependencies
3. Run the main script / notebook that:
   - runs `runMonteCarlo()` for both policies
   - generates summary tables
   - saves plots to the `Outputs/` folder

## Additional Features
Ideas already supported or simple to add:
- Test multiple reserve values (e.g., reserve 3, 5, 7 seats) and compare on the same exceedance plot
- Reserve seats at multiple stops (e.g., Stop 7 + Stop 1) and observe downstream impacts
- Time-varying arrival rates (morning surge, lunch surge)
- Time-varying churn (e.g., cafe stop behaviour changes over the day)
- More realistic segment travel times (random travel/dwell distributions instead of fixed)



Data required for accurate calibration (rather than assumptions):
1. Daily Attendance totals and visitor group sizes
2. Visitor arrival and exit patterns to be matched to a distribution
3. Number of buses and bus capacity in practice (usable seats)
4. Realistic bus travel time between stops and estimated exhibit visitor dwell times
5. Bus rider departing behaviour at each stop (rough probabilities would be fine)
6. Cafe Stop churn at different times of day (rough probabilities would be fine)  

## Important Notes for the User:
- This is a proof-of-concept model: inputs are assumptions designed to reproduce system mechanics, not to claim operational truth
- The model is most valuable for:
  - comparing policies fairly
  - identifying tail-risk / worst-day behaviour
 

## Credits
- Built and written by Saf Flatters (2026)
- Inspiration: real-world observation while visiting Monarto Safari Park

## Connect with Me
📫 [LinkedIn](https://www.linkedin.com/in/safflatters/)

## License and Usage
![Personal Use Only](https://img.shields.io/badge/Personal%20Use-Only-blueviolet?style=for-the-badge)

This project is intended for personal, educational, and portfolio purposes only.

You are welcome to view and learn from this work, but you may not copy, modify, or submit it as your own for academic, commercial, or credit purposes.