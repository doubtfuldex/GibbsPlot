# GibbsPlot

**A robust, interactive tool for modeling and visualizing protein folding thermodynamics.**

This application allows researchers to simulate protein stability curves based on the two-state unfolding model. Unlike simple calculators, this tool accounts for **temperature-dependent heat capacity ($\Delta C_p$)** and utilizes **Monte Carlo simulations** to generate error envelopes, providing a rigorous analysis of experimental uncertainty.

## 🚀 Key Features

* **Advanced Thermodynamics:** Implements the Gibbs-Helmholtz equation with a linear temperature dependence for heat capacity ($\alpha$ parameter).
* **Monte Carlo Error Propagation:** Input standard deviations for your parameters ($T_m$, $\Delta H$, etc.) to visualize uncertainty bands (shaded error envelopes) on all plots.
* **Comprehensive Visualization:**
    * **Stability Curves:** $\Delta G$ vs. Temperature.
    * **Thermodynamic Components:** Enthalpy ($\Delta H$) and Entropy ($T\Delta S$) traces.
    * **Population Analysis:** Fraction Unfolded ($f_u$) sigmoid curves.
    * **DSC Simulation:** Excess Heat Capacity ($C_p$) profiles (differential scanning calorimetry simulation).
* **Critical Points Calculation:** Automatically computes:
    * Melting Temperature ($T_m$)
    * Cold Denaturation Temperature ($T_c$)
    * Temperature of Maximum Stability ($T_s$)
    * Extrapolated stability parameters at 25°C (standard state).
* **Multi-Variant Support:** Compare multiple protein variants (e.g., Wild Type vs. Mutants) side-by-side.
* **Publication-Ready Styling:** Full control over axis ranges, fonts, tick marks, line widths, and colors.
* **Session Management:** Save and load your analysis state via JSON.
* **Data Export:** Download summary statistics and raw curve data as CSVs.

## 🧮 Mathematical Model

The tool calculates the Gibbs Free Energy ($\Delta G$) using the modified Gibbs-Helmholtz equation.

### 1. Temperature-Dependent Heat Capacity
The change in heat capacity is modeled as:
$$\Delta C_p(T) = \Delta C_{p,m} + \alpha (T - T_m)$$

* $\Delta C_{p,m}$: Heat capacity change at the melting temperature.
* $\alpha$: The slope of the heat capacity dependence (often ignored in simple models, but critical for broad temperature ranges).

### 2. Enthalpy and Entropy
Integrated from $T_m$ to $T$:

$$\Delta H(T) = \Delta H_m + \int_{T_m}^{T} \Delta C_p(T) dT$$

$$\Delta S(T) = \frac{\Delta H_m}{T_m} + \int_{T_m}^{T} \frac{\Delta C_p(T)}{T} dT$$

### 3. Gibbs Free Energy
$$\Delta G(T) = \Delta H(T) - T\Delta S(T)$$

## 📦 Installation & Usage

### Prerequisites
* Python 3.8+
* pip

### 1. Clone the repository
```bash
git clone [https://github.com/yourusername/protein-thermal-stability.git](https://github.com/yourusername/protein-thermal-stability.git)
cd protein-thermal-stability
