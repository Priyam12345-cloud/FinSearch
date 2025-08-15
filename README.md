# FinSearch
# Delta Sensitivity Analysis: Black-Scholes, Binomial, and Monte Carlo Models



---

## 📌 Introduction
**Delta (Δ)** is one of the most important option Greeks, measuring the sensitivity of an option’s price to changes in the underlying asset’s price.

Mathematically:
\[
\Delta = \frac{\partial V}{\partial S}
\]
Where:  
- **V** = Option value  
- **S** = Underlying stock price

### Key Interpretations
- Measures **directional risk exposure**.
- For a **Call option**: Δ ranges from `0` to `1`.  
- For a **Put option**: Δ ranges from `-1` to `0`.  
- At-the-money (ATM) options have Δ near **0.5** (Call) or **-0.5** (Put).
- Delta also serves as an **approximate hedging ratio**.

---

## 📊 Delta Behavior in Different Models

### 1. Black-Scholes Model
**Formulas**:  
\[
\Delta_{Call} = N(d_1), \quad \Delta_{Put} = N(d_1) - 1
\]
- Produces **smooth, continuous** Delta curves.
- Reacts instantly to price changes.
- Efficient for **European options**.

### 2. Binomial Model
**Formula**:
\[
\Delta = \frac{V_{up} - V_{down}}{S_{up} - S_{down}}
\]
- Delta computed **discretely** at each node.
- Converges to Black-Scholes Delta with more steps.
- Supports **American options** and discrete events.

### 3. Monte Carlo Simulation
Delta estimated using **finite differences**:
\[
\Delta \approx \frac{V(S + \delta S) - V(S - \delta S)}{2 \delta S}
\]
- Requires **re-simulation** for price perturbations.
- Computationally expensive but **model-agnostic**.
- Suitable for **exotic options**.

---

## 🖥 Example Delta Simulation

| Stock Price ($) | Black-Scholes Δ | Binomial Δ (100 Steps) | Monte Carlo Estimated Δ |
|-----------------|----------------|------------------------|--------------------------|
| 100             | 0.5423         | 0.5418                 | 0.545                    |
| 105             | 0.6141         | 0.6135                 | 0.616                    |
| 110             | 0.6793         | 0.6790                 | 0.681                    |

---

## 🌎 Real-World Summary

### Model Preference by Context
| Context                  | Preferred Model | Reason |
|--------------------------|-----------------|--------|
| Academic Teaching        | Black-Scholes   | Analytical clarity, easy to explain. |
| European Options Pricing | Black-Scholes   | Fast closed-form solutions. |
| American Options Pricing | Binomial        | Incorporates early exercise logic. |
| Exotic Options Pricing   | Monte Carlo     | Handles path-dependent and complex payoffs. |
| Employee Stock Options   | Binomial/Lattice| Captures vesting periods and early exercise. |
| Risk Simulations         | Monte Carlo     | Simulates multiple risk factors and paths. |

### Model Limitations
**Black-Scholes**:
- Assumes constant volatility and interest rates.
- Cannot handle American or exotic options.
- Ignores transaction costs and liquidity.

**Binomial**:
- Computational cost increases with steps.
- Still assumes constant volatility per step.

**Monte Carlo**:
- Computationally heavy for Greeks estimation.
- Needs many paths for accuracy.

---

## 📈 Role in Modern Trading
- **Black-Scholes**: Quick benchmark pricing and Greeks.  
- **Binomial**: Practical pricing for American options and structured products.  
- **Monte Carlo**: Extensively used for exotic derivatives, risk management, and portfolio simulations.

---

## 🏁 Final Conclusion

This report systematically analyzed **three key option pricing approaches**:
- **Black-Scholes** → Efficient, analytical, ideal for European options.  
- **Binomial** → Versatile, supports early exercise, discrete events.  
- **Monte Carlo** → Flexible, suitable for exotic and path-dependent derivatives.

### Delta Sensitivity Insights
- **Black-Scholes**: Smooth, continuous Δ.  
- **Binomial**: Discrete Δ, converges to BS as steps increase.  
- **Monte Carlo**: Less efficient but universally applicable.

### Practical Relevance
- No single model fits all situations.
- Advanced models are needed for volatility smiles, stochastic volatility, and jumps.
- Modern quant finance integrates these classics with numerical methods, ML, and real-world calibration.

**Final Verdict**:  
💡 *Master the classics (Black-Scholes, Binomial, Monte Carlo), but adapt to the complexity of real markets.*

---

## 📚 References
- Black, F., & Scholes, M. (1973). *The Pricing of Options and Corporate Liabilities*.  
- Cox, J.C., Ross, S.A., & Rubinstein, M. (1979). *Option Pricing: A Simplified Approach*.  
- Glasserman, P. (2004). *Monte Carlo Methods in Financial Engineering*.

---

## 🛠 How to Use
```bash
# Clone this repository
git clone https://github.com/yourusername/delta-sensitivity-analysis.git

# Navigate into the folder
cd delta-sensitivity-analysis

# Install required packages
pip install -r requirements.txt

# Run the simulation
python delta_analysis.py
