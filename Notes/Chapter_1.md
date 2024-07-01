# Statistical Inference and Causal Identification

## 1. Basic Statistical Concepts

- **Population**: The object of interest $\mathcal{Y} = \{y_1, y_2, y_3, y_4, \dots\}$
- **Parameter**: Parameters that describe certain characteristics or relationships of the population
- **Sample**: A subset of the population obtained through sampling $\{y_1, \dots, y_N\}$
- **Estimator**: A statistical tool or method, a function based on data
- **Estimates**: The numerical values obtained by applying estimators to data, e.g., the average height of 20-year-old men in China $\hat{\mu} = 176 \text{cm}$

## 2. Statistical Inference and Characteristics of Statistics

- **Unbiasedness**: $E(\hat{\mu}) = \mu$
- **Efficiency**: $Var(\hat{\mu})$ minimized
- **Consistency**: As $N \to \infty$, $Var(\hat{\mu}) \to 0$ and $E(\hat{\mu}) \to \mu$
- **Sufficiency**: Estimators should utilize all the information from the data

## 3. Law of Large Numbers and Central Limit Theorem

- **Law of Large Numbers**: The sample mean converges to the population mean
- **Central Limit Theorem**: The distribution of the sample mean approaches a normal distribution

## 4. Bootstrap Method

- Estimates the uncertainty of estimators through resampling, including variance ($Var(\hat{\mu})$), standard error ($S.E(\hat{\mu})$), and confidence interval ($C.I(\hat{\mu})$)
- **Method**: Sample with replacement to obtain an approximate sampling distribution of the estimator

## 5. Statistical Hypothesis and Inference

- **Null Hypothesis** and **Alternative Hypothesis**: For example, $H_0: \mu = 176$ and $H_1: \mu \ne 176$
- **t-test**: Calculate the t-value; if it deviates far from 0, the null hypothesis may be rejected
- **Significance Level ($\alpha$)** and **p-value**: A significance level of 5% means a 5% probability of Type I error
- **Confidence Interval**: The probability that the interval contains the true parameter is $1 - \alpha$

## 6. Types of Data

- **Primary Source** vs. **Secondary Data**
- **Experimental Data** vs. **Observational Data**
- **Continuous Data** vs. **Discrete Data**
- **Cross-sectional Data**, **Time Series Data**, **Panel Data**

## 7. Panel Data

- **Short Panel**: Large N, small T
- **Long Panel**: Small N, large T
- **Large Panel**: Large N, large T
- **Balanced Panel**: The number of observations at each time point is the same
- **Unbalanced Panel**: The number of observations at each time point varies
- Causes of data missing: company bankruptcy, individual death, survey dropout, new individuals joining the survey, etc.

## 8. Causal Identification and the Credibility Revolution

- **Identification**: Mapping empirical information uniquely to the research object based on theoretical assumptions
- **Data Revolution**: Opportunities and challenges brought by big data
- **Identification Revolution**: Emphasizes the judgment of the research object and its identifiability, requiring rigorous research design
- **Design-driven Research**: Emphasizes the importance of research design
- **Causal Relationship**: $g: X \to Y$, $Y = g(X) = \alpha + \tau X$

## 9. Causal Effect and Counterfactual

- **Causal Effect**: The difference in outcomes for the same unit at the same time point with and without treatment
- **Counterfactual**: Only one of the potential outcomes can be observed, the other is counterfactual
- **Estimation Methods**: Compare potential outcomes for different units rather than for the same unit

## 10. Estimating Causal Effects

- **Average Treatment Effect (ATE)**: $\tau_{ATE} = E(Y_i(1) - Y_i(0))$
- **Average Treatment Effect on the Treated (ATT)**: $\tau_{ATT} = E(Y_i(1) - Y_i(0) | D_i = 1)$

## 11. Endogeneity

- **Endogeneity Issues**: Omitted variable bias, reverse causality, selection bias, measurement error, and model misspecification
- **Solutions**:
  - **Randomization/Natural Experiment**
  - **Regression Discontinuity Design (RDD)**
  - **Difference-in-Differences (DID)**, synthetic control, event study
  - **Instrumental Variables (IV)**
  - **Selection on Observables**: Regression, Propensity Score Matching (PSM), matching

## 12. Policy Analysis

- **Policy Analysis**:
  - Identify and estimate the treatment effects of policy interventions
  - Understand the mechanisms producing treatment effects
  - Forecast the impacts of interventions (constructing counterfactual states)

## 13. Literature Review

- **Angrist (1991, AER)**: The impact of Vietnam draft lottery on veterans' earnings, using randomization and natural experiment
- **Angrist & Krueger (1994, JLE)**: The impact of WWII draft on veterans' earnings, using dates of birth as an instrument
- **Angrist & Krueger (1991, QJE)**: The impact of quarter of birth on education and earnings, using compulsory school attendance laws as an instrument
- **Xavier et al. (2011, RFS)**: The impact of unexpected snow on strategic default motivation and debt overhang, using unexpected snow as an instrument
- **Levitt (2000, AER)**: The impact of police hiring on crime rates, using the number of firefighters and municipal workers as an instrument
- **Deng et al. (2021, RFS)**: The impact of housing demand on house prices, using Beijing purchase restrictions as a natural experiment
- **Lalive et al. (2014, RES)**: The impact of the Austrian parental leave system on women's pay, using policy changes as a natural experiment
- **Lee (2008)**: The effect of incumbency in US House elections, using close election results as a regression discontinuity design