# Process-to-Yield Simulation: Dopant Diffusion, Ion Implantation, and Wafer Yield

An independent (non-institutional) research project simulating semiconductor
fabrication process physics and its link to wafer yield economics, built
entirely in Python with no proprietary/paid tools.

This is a **beginner-level educational research project**, not a peer-reviewed
publication. It was built for self-study and as a portfolio piece.

## What this project does

1. **Diffusion doping simulation** (`src/diffusion.py`)
   Solves Fick's second law analytically for predeposition (erfc profile)
   and drive-in (Gaussian profile) steps, including Arrhenius temperature
   dependence of diffusivity.

2. **Ion implantation simulation** (`src/implant.py`)
   Models implant doping profiles using the Gaussian approximation
   (projected range + straggle), with an optional skew correction.

3. **Wafer yield modeling** (`src/yield_models.py`)
   Implements Poisson, Murphy, and Negative Binomial yield models based
   on defect density and die area.

4. **Combined process-to-yield analysis** (`src/combined_demo.py`)
   Sweeps drive-in furnace temperature to quantify junction-depth
   variability, then proposes a simplified (explicitly illustrative)
   model linking that process variability to effective defect density
   and resulting yield.

## Important honesty note

Section 4/5's link between doping-profile variance and defect density
is a **simplified illustrative model I constructed for this project**,
not a validated industrial relationship. All physical constants used
as defaults (D0, Ea, Rp, dRp, etc.) are placeholder values for testing
the code — **replace them with properly cited values** from textbooks
or SRIM tables before treating results as meaningful, and say so clearly
in the paper.

## Requirements

```
pip install -r requirements.txt
```

## Usage

```bash
cd src
python diffusion.py        # generates figures/diffusion_profile.png
python implant.py          # generates figures/implant_profile.png
python yield_models.py     # generates figures/yield_models.png
python combined_demo.py    # generates the two combined-analysis figures
```

## Suggested citations

**Diffusion & Ion Implantation Physics**
- NPTEL — VLSI Technology (IIT, free) — Lectures 15–22 cover Theory of Diffusion, Diffusion Systems, and Ion Implantation Process directly.

- MIT OpenCourseWare — 6.012 Microelectronic Devices and Circuits — MOSFET structure, doping fundamentals, free PDF lecture notes.

- City University of Hong Kong — AP6120, Chapter 8: Diffusion (free PDF) — the exact erfc/Gaussian diffusion treatment used in your paper.

- arXiv:1701.07087 — "Ion-Beam-Induced Defects in CMOS Technology: Methods of Study" — open-access review paper directly on implantation physics.

 
**Yield Modeling**
- MIT OpenCourseWare — 6.780 Semiconductor Manufacturing (Prof. Duane Boning, free) — explicitly covers "defect and parametric yield modeling," which is exactly your Section 3.3/4.3 topic.

- arXiv:2407.02079 — "Theseus: Exploring Efficient Wafer-Scale Chip Design for LLMs" — states the Murphy yield equation explicitly and cites it, open access.

- arXiv:2310.09568 — "Wafer-scale Computing: Advancements, Challenges, and Future Perspectives" — discusses Murphy's model and defect density in a real industry context (Cerebras WSE-2 example).

 
**CMOS Scaling / Background Context**
- arXiv:2409.07357 — open-access thesis chapter covering CMOS scaling and Moore's Law fundamentals.


- arXiv:1509.00885 — "Exploiting Challenges of Sub-20nm CMOS for Affordable Technology Scaling" — free, and cites the original Moore (1965) and Dennard (1974) papers directly in its reference list, which you can cite through it.


- MRCET VLSI Design Lecture Notes (free PDF) — general fabrication process flow reference (oxidation, diffusion, implantation, metallization).


## Project status

Work in progress — built for self-study and MTech application portfolio,
not for publication. Feedback and corrections welcome via issues.

## License

MIT
