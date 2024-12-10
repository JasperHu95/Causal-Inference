# DiD Method

## Classic DID: Two-Way Fixed Effects Model

### Example: Minimum Wage Law and Employment Rate
- **Research Background**:
  - Traditional economic theory suggests that raising the minimum wage reduces employment for low-income workers.
  - **Card & Krueger (1994)**: Studied the impact of New Jersey's minimum hourly wage increase from $4.25 to $5.05 in 1992 on employment rates.
  - **Data**: Compared 410 fast-food restaurants in New Jersey and Pennsylvania, using two-wave survey data (March 1992 and December 1992).
  - **Result**: DID analysis showed that raising the minimum wage did not significantly reduce employment.

### 2×2 DID Causal Identification

- **Basic Concepts**:
  
  - DID leverages the differences in time (before and after the treatment) and between groups (treated and control groups) to identify causal effects.
  - **Causal Effect**:
    $$
    \tau \equiv Y_{it}(1) - Y_{it}(0)
    $$
  - **ATT (Average Treatment Effect on the Treated)**:
    $$
    ATT = E[Y_{i,t=1}(1)|D_i = 1] - E[Y_{i,t=1}(0)|D_i = 1]
    $$
  - **ATU (Average Treatment Effect on the Untreated)**:
    $$
    ATU = E[Y_{i,t=1}(1)|D_i = 0] - E[Y_{i,t=1}(0)|D_i = 0]
    $$
  - **ATE (Average Treatment Effect)**:
    $$
    ATE = E[Y_{i,t=1}(1) - Y_{i,t=1}(0)]
    $$
  
- **Key Assumptions**:
  1. **Parallel Trend Assumption**:
     $$
     E[Y_{i,t=1}(0)|D_i = 1] - E[Y_{i,t=0}(0)|D_i = 1] = E[Y_{i,t=1}(0)|D_i = 0] - E[Y_{i,t=0}(0)|D_i = 0]
     $$
     The trends in the outcome variable for the treated and control groups should be similar in the absence of treatment.
  2. **No-Anticipation Assumption**:
     $$
     Y_{it=0}(1) = Y_{it=0}(0)
     $$
     The potential outcomes for both groups are the same before the treatment.
  3. **Stable Unit Treatment Value Assumption (SUTVA)**:
     $$
     Y_{it} = Y_{it}(1) * [D_i = 1] + Y_{it}(0) * [D_i = 0]
     $$
     The potential outcomes of a unit do not depend on the treatment status of other units.

### 2×2 DID Parameter Estimation
- **Regression Model**:
  $$
  Y_i = \beta_0 + \beta_1 \text{After}_i + \beta_2 \text{Treat}_i + \beta_3 (\text{Treat}_i \cdot \text{After}_i) + u_i
  $$
  - **$Y$**: Outcome variable.
  - **$After$**: Indicator for post-treatment period (1) or pre-treatment period (0).
  - **$Treat$**: Indicator for treated group (1) or control group (0).
  - **$\beta_3$**: Captures the causal effect.

- **Interpretation**:
  - **Difference after the treatment**:
    $$
    E[Y|\text{Treat} = 1, \text{After} = 1] - E[Y|\text{Treat} = 0, \text{After} = 1] = \beta_2 + \beta_3
    $$
  - **Difference before the treatment**:
    $$
    E[Y|\text{Treat} = 1, \text{After} = 0] - E[Y|\text{Treat} = 0, \text{After} = 0] = \beta_2
    $$
  - **DID Estimate**:
    $$
    \beta_3 = (E[Y|\text{Treat} = 1, \text{After} = 1] - E[Y|\text{Treat} = 0, \text{After} = 1]) - (E[Y|\text{Treat} = 1, \text{After} = 0] - E[Y|\text{Treat} = 0, \text{After} = 0])
    $$

## DID Regression: Two-Way Fixed Effects
- **Model**:
  $$
  Y_{it} = \alpha + \mu_i + \lambda_t + \tau D_{it} + \beta X_{it} + \epsilon_{it}
  $$
  - **$\mu_i$**: Individual fixed effects.
  - **$\lambda_t$**: Time fixed effects.
  - **$\tau$**: Treatment effect.
  - **$X_{it}$**: Covariates.
  - **$\epsilon_{it}$**: Error term.

- **Strong Exogeneity Assumption**:
  - The error term is independent of the treatment variable, covariates, individual fixed effects, and time fixed effects.
  - Conditional exogeneity of the treatment variable: The treatment variable can be correlated with covariates, individual fixed effects, and time fixed effects, but not with the error term.

- **Uncertainty Estimation**:
  - Use clustered standard errors (Bertrand et al., 2004).
  - When the number of clusters is small, use clustered bootstrap (Cameron et al., 2008).

## Selection Bias
- **Problem**: Directly comparing the treated and control groups after the policy often introduces selection bias.
  $$
  E[Y_{i,t=1}|D_i=1] - E[Y_{i,t=1}|D_i=0] = ATT + \text{Selection Bias}
  $$
- **Solution**:
  - Use weighting methods (e.g., entropy balancing) to balance the control group with the treated group.
  - The target variables for weighting include pre-treatment covariates and pre-treatment outcome variables.

## Application Cases

### Truex (2014): Entrepreneur Joining NPC and Firm Performance
- **Research Background**:
  - Treatment variable: Entrepreneur joining the National People's Congress (NPC).
  - Outcome variables: Return on assets, profit margin.
  - Data: 987 listed companies from 2007 to 2010, of which 48 had leaders elected as NPC deputies in 2008.
- **Result**:
  - Joining the NPC increased return on assets by 1.5 percentage points and profit margin by 3-4 percentage points.
  - The author argues that this is due to the reputation boost from the NPC membership.

### Bertrand, Schoar, and Thesmar (2007): French Banking Deregulation
- **Research Background**:
  - Studied the impact of French banking deregulation on firms and industry structure.
- **Result**:
  - Deregulation promoted a "creative destruction" process, improving resource allocation efficiency.

### Bleakley (2010): Malaria Eradication and Labor Productivity
- **Research Background**:
  - Treatment variable: Malaria eradication campaigns.
  - Outcome variable: Labor productivity.
- **Result**:
  - Malaria eradication significantly increased labor productivity in previously malaria-endemic areas.

## Variations of DID and Strong Exogeneity

- **Dynamic Treatment Effects**:
  - Use event study methods to handle dynamic effects.
- **Continuous Treatment Variables**:
  - Discretize continuous variables into multiple binary treatment variables for testing.
- **Generalized DID**:
  - Treatment effects are moderated by certain variables, requiring multiple interaction terms for testing.
