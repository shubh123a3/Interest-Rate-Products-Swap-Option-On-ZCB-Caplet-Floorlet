# Interest Rate Products: Swap, Option on ZCB, Caplet, and Floorlet


https://github.com/user-attachments/assets/ea687616-ecfa-468e-9130-c0778b964ce7


## Overview
This project implements various **Interest Rate Derivatives** using financial engineering techniques. It covers **Swaps, Zero-Coupon Bond (ZCB) Options, Caplets, and Floorlets** using the **Hull-White (HW) Model**. The implementation includes both theoretical pricing formulas and Monte Carlo simulations for numerical approximations.

## Features
- **Swap Pricing**: Implements Interest Rate Swaps using discount factor methods.
- **Option on ZCB**: Uses Hull-White short rate model to price options on Zero-Coupon Bonds.
- **Caplets & Floorlets**: Models interest rate caps and floors using the Hull-White framework.
- **Mathematical Derivations**: Implements analytical formulas and Monte Carlo simulations.
- **Streamlit UI**: A user-friendly interface to visualize results interactively.

## Mathematical Formulation

The **Hull-White Model** assumes that the short rate follows:

$$ dr_t = (\theta(t) - a r_t) dt + \sigma dW_t $$

where:
- \( r_t \) is the short rate at time \( t \)
- \( a \) is the mean reversion speed
- \( \sigma \) is the volatility
- \( \theta(t) \) is a function ensuring the model fits the initial term structure
- \( W_t \) is a Wiener process (Brownian motion)

### 1. **Zero-Coupon Bond Pricing under Hull-White**
The price of a **Zero-Coupon Bond** maturing at \( T \) is given by:

$$ P(0,T) = A(0,T) e^{-B(0,T) r_0} $$

where:

$$ B(0,T) = \frac{1 - e^{-a(T-0)}}{a} $$

$$ A(0,T) = \frac{P(0,T)}{P(0,0)} e^{B(0,T)f(0,0) - \frac{\sigma^2}{2a^2} (B(0,T))^2} $$

### 2. **Swap Pricing**
A **Fixed-Floating Interest Rate Swap** value is given by:

$$ V_{swap} = \sum_{i=1}^{n} \tau_i P(0, t_i) (F_i - K) $$

where:
- \( \tau_i \) is the time fraction for each period
- \( P(0,t_i) \) is the discount factor
- \( F_i \) is the forward rate
- \( K \) is the fixed rate

### 3. **Caplet and Floorlet Pricing**
A **Caplet** (interest rate caplet) price under the Hull-White model is given by:

$$ V_{caplet} = N (1 + (T_2 - T_1) K) P(0, T_2) N(d_1) - N P(0, T_2) N(d_2) $$

where:

$$ d_1 = \frac{\ln(1 + (T_2 - T_1) K) + 0.5 \sigma^2}{\sigma} $$

$$ d_2 = d_1 - \sigma $$

A **Floorlet** price follows a similar formulation but considers put options on interest rates.

## Implementation Details
The implementation is structured as follows:

- **`app.py`**: The main script that implements the interest rate derivative models and provides a Streamlit UI.
- **`pricing.py`**: Core mathematical functions for Hull-White model, swap pricing, and caplet/floorlet pricing.
- **`utils.py`**: Helper functions for numerical computations and Monte Carlo simulations.
- **`requirements.txt`**: Dependencies for running the project.

## Installation
Clone the repository and install the dependencies:
```bash
$ git clone https://github.com/shubh123a3/Interest-Rate-Products-Swap-Option-On-ZCB-Caplet-Floorlet.git
$ cd Interest-Rate-Products-Swap-Option-On-ZCB-Caplet-Floorlet
$ pip install -r requirements.txt
```

## Running the Streamlit App
To launch the interactive visualization:
```bash
$ streamlit run app.py
```

## Future Improvements
- **Add Stochastic Volatility Models** (e.g., SABR Model)
- **Enhance Monte Carlo Simulations** for faster convergence
- **Implement Alternative Short-Rate Models** like Vasicek
- **Backtesting with Real Market Data**

## References
- Hull, J. C. (Options, Futures, and Other Derivatives)
- Brigo, D., & Mercurio, F. (Interest Rate Models - Theory and Practice)

## Author
**Shubh Shrishrimal**

---
This project aims to bridge the gap between financial theory and practical implementation by modeling complex interest rate derivatives using quantitative finance techniques.

