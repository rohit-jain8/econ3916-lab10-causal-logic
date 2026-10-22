# econ3916-lab10-causal-logic
# Correlation & Causality: Confounders, Colliders and the Limits of Controls

## Objective

In this lab, I explored how correlation can be misleading when estimating causal relationships and how controlling for different variables can either reduce or introduce bias.

## Methodology

- Simulated three different scenarios involving true causation, confounding, and selection bias to compare correlations with actual causal effects.
- Used NetworkX to create directed graphs showing the relationships between confounders, colliders, and mediators.
- Ran OLS regressions to compare estimates with and without controlling for confounding variables and colliders.
- Simulated M-bias to demonstrate how controlling for a variable measured before treatment can still introduce bias.
- Created a function called `coef_on_d()` to estimate the treatment coefficient using different combinations of control variables.
- Used the LaLonde (1986) dataset to compare experimental results with an observational comparison group from the CPS and examine how adding covariates changes the estimated treatment effect.

## Key Findings

The three simulated scenarios produced correlations of **0.654, 0.664, and 0.632**, despite having true causal effects of 2.0, 0.0, and 0.0, respectively. This showed me that even strong correlations don't necessarily indicate causation.

Controlling for a confounder brought the estimated effect from **2.476 to 1.500**, matching the true effect of 1.5. However, controlling for a collider produced an estimate of **-0.592**, even though the true causal effect was zero.

The M-bias simulation showed that controlling for a pre-treatment variable could still introduce bias, producing an estimate of **-0.191**. When I also controlled for u1, the estimate returned to **0.006**, much closer to the true effect of zero.

Finally, the LaLonde analysis produced an experimental benchmark of **$1,794**, compared to a naive observational estimate of **-$8,498**. After adding controls, the observational estimate increased to **$699**, closing **89% of the gap** between the original estimate and the experimental benchmark.

Overall, this lab helped me understand that adding more control variables doesn't automatically improve a regression. What matters is understanding the causal relationships between variables and determining which controls are actually appropriate.
