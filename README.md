# Pure-Fluid PVT Solver

A browser tool that calculates the compressibility factor Z, molar volume and density of pure gases and liquids with eight methods, and tells you which answer to trust and why.

**Live page:** https://krshn-a.github.io/pvt-solver/ 

## What it does

- **Inputs:** one of 28 common fluids (or your own Tc, Pc, ω, Zc and M), plus temperature and pressure, or temperature and molar volume. The acentric factor ω can come from the built-in table, be typed in, or be estimated from one vapour-pressure value at T = 0.7·Tc.
- **Step 1, where is the state?** From Tr = T/Tc, Pr = P/Pc and the boiling pressure it decides: gas, vapour, liquid, at the boiling point, or near the critical point.
- **Step 2, eight methods:** ideal gas; two-term virial equation (Pitzer correlation for B); generalized compressibility chart (Lee–Kesler); van der Waals, Redlich–Kwong, Soave–Redlich–Kwong and Peng–Robinson cubic equations; Rackett liquid correlation.
- **Step 3, a verdict:** every method is graded for that state (Recommended / Acceptable / Use with caution / Not recommended / Not applicable) with a one-line reason; the best answer is shown with the reason it was chosen, plus warnings.
- **Plots:** Z versus P for all methods (with NIST measured data for some fluids); the P–V isotherm of a cubic equation with its three roots and the equal-area line; the generalized Z–Pr chart with the range where the virial equation works.
- **Common mistakes:** nine worked cases where applying an equation blindly gives a wrong answer, each with the correct answer and the reason.
- **Optional:** residual enthalpy, residual entropy and fugacity coefficient.

## Use it

Open `index.html` in any modern browser. No installation and no server; nothing is uploaded.

## Accuracy checks

- Reproduces published worked examples (Smith, Van Ness & Abbott, *Introduction to Chemical Engineering Thermodynamics*, Ch. 3) for n-butane and liquid ammonia within 0.1 %, and Lee–Kesler table values to four decimals.
- Against NIST measured data, the Lee–Kesler method's average error in Z is about 1 % for non-polar fluids (CO₂, propane, H₂).
- 45 automated checks: from the `source` folder run `node tests/test_core.mjs`.

## Source

`source/src/` holds the readable code: `thermo-core.js` (all thermodynamics), `app.js` (interface), `plot.js` (SVG plots), `styles.css` and `body.html`. Running `python3 build.py` in `source/` bundles them into the single file `dist/index.html`.

Made by Krishna Gaur, IIT Delhi–Abu Dhabi.
