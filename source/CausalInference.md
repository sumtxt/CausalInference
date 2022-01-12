---
name: CausalInference
topic: Causal Inference
maintainer: Imke Mayer, Pan Zhao and Julie Josse
email: mayer.imke@gmail.com
version: 2022-01-05
---



Causal inference can be seen as a subfield of statistical analysis. It
is used in various fields such as econometrics, epidemiology,
educational sciences, etc. With causal inference one addresses questions
about effects of a treatment, intervention or policy on some target over
a given sample or population. Under certain model assumptions, causal
inferences can be carried out by fitting simple regression models or
combining several regression models in a specific way as will be
sketched out later. For observational data, additional untestable
assumptions have to be made to (non-parametrically) identify causal
effects.

There do not exist basic R functions to do causal analyses straight
away, but many methods - more or less complex - are implemented in
different packages on CRAN, which we structure into main topics:

-   [Methods for experimental data](#rct)
-   [Average treatment effect estimation and other univariate treatment
    effect estimates](#ate)
-   [Heterogeneous treatment effect estimation](#hte)
-   [Policy learning and dynamic treatment regimes](#policy)
-   [Do-calculus and causal discovery](#dag)
-   [Specific types of data](#data)
-   [Specific application fields](#applications)

If you think that we missed some important packages in this list, please
contact the maintainers.

[**Methods for randomized controlled trial (RCT) and other experimental
data**]{#rct}

-   *Construction of experimental designs* is implemented in
    `r pkg("blocksdesign")` (blocks for general factorial
    treatment designs), `r pkg("BCHM")` (Bayesian cluster
    hierarchical model design for multiple subgroup basket trials),
    `r pkg("Boptbd")` (Bayesian optimal block designs under
    linear mixed effects model), `r pkg("seqDesign")`
    (sequential design of randomized two-stage treatment efficacy trials
    with time-to-event endpoints). Many other tools and packages exist
    for designing experiments and clinical trials, we refer to the
    `r view("ExperimentalDesign")` and
    `r view("ClinicalTrials")` CRAN Task Views.
-   *Tests based on pairwise comparisons* are provided in
    `r pkg("BuyseTest")`.
-   *Regression models* where the causal estimand is defined as a
    coefficient of a regression model are implemented in the packages
    `r pkg("allestimates")`.
-   *Evaluation of RCTs* is provided in `r pkg("experiment")`
    (various statistical methods), `r pkg("eefAnalytics")`
    (Frequentist and Bayesian multilevel models),
    `r pkg("ipcwswitch")` (IPW adapted to treatment switch in
    an RCT), `r pkg("idem")` (with death and missingness).
-   *Posterior analysis tools* are implemented in
    `r pkg("beanz")` (Bayesian HTE models),
    `r pkg("cjoint")` (conjoint analysis for survey
    experiments).
-   Design and analysis of *two-stage preference trials* is implemented
    in `r pkg("preference")`.
-   `r pkg("interferenceCI")` implements treatment effect
    estimation methods for two-stage randomized experiments with
    interference and binary outcome.
-   In case of *non-compliance*, `r pkg("rpsftm")` uses
    g-estimation to estimate the causal effect of a treatment in a
    two-armed randomised control trial where non-compliance exists and
    is measured, under an assumption of an accelerated failure time
    model and no unmeasured confounders.
-   A time series causal inference model for RCT under *spillover
    effect* is implemented in `r pkg("SPORTSCausal")`.
-   Design and analysis of clinical non-inferiority or superiority
    trials with active and placebo control is implemented in
    `r pkg("ThreeArmedTrials")`.

[**Average treatment effect estimation and other univariate treatment
effect estimates**]{#ate}

-   *Regression models* where the causal estimand is a regression
    parameter are implemented in `r pkg("estimatr")`,
    `r pkg("CausalGAM")` (using generalized additive models),
    `r pkg("sampleSelection")` (two-step and maximum
    likelihood estimation of Heckman-type sample selection models),
    `r pkg("BCEE")` (Bayesian causal effect estimation for
    binary or continuous treatment and outcomes),
    `r pkg("borrowr")` (Bayesian PATE estimation for multiple
    exchangeable data sources), `r pkg("causaldrf")` (average
    causal dose response functions), `r pkg("hdm")` (efficient
    estimators with uniformly valid confidence intervals, it assumes
    approximately sparse models for high-dimensional settings).
-   *G-formula* and other *conditional outcome regression* based methods
    are supported in the packages `r pkg("gfoRmula")` (also
    for time-varying treatment and confounding),
    `r pkg("EffectLiteR")` (based on structural equation
    modeling), `r pkg("endoSwitch")` (maximum likelihood
    estimation of endogenous switching regression models), and
    `r pkg("riskRegression", priority = "core")` (for survival
    outcomes with or without competing risks).
-   *Matching* methods are implemented in
    `r pkg("Matching", priority = "core")` (multivariate and
    propensity score matching, and finding optimal balance based on a
    genetic search algorithm),
    `r pkg("MatchIt", priority = "core")` (selecting matched
    samples of the original treated and control groups with similar
    covariate distributions), `r pkg("MatchThem")`
    (pre-processing techniques of matching and weighting multiply
    imputed datasets), `r pkg("optmatch")` (distance based
    bipartite matching using the RELAX-IV minimum cost flow solver),
    `r pkg("CMatching")` (for cluster data),
    `r pkg("FLAME")` (almost-matching-exactly via learned
    weighted Hamming distance).
-   *Inverse propensity weighting* (IPW, also known as inverse
    probability of treatment weighting, IPTW) methods are implemented in
    `r pkg("ipw")`, `r pkg("causalweight")`,
    `r pkg("estimatr")`, `r pkg("riskRegression")`
    (for survival outcomes), `r pkg("clusteredinterference")`
    and `r pkg("inferference")` (the latter two both making
    interference assumptions), `r pkg("hrIPW")` (under a Cox
    proportional hazards model), `r pkg("ipwCoxCSV")`
    (corrected sandwich variance estimation for the IPW Cox model),
    `r pkg("ipwErrorY")` (correction methods for the IPW
    estimation with measurement error in outcomes).
    `r pkg("autoCovariateSelection")` offers automated
    covariate selection for high-dimensional propensity scores.
    `r pkg("pstest")` provides specification tests for
    parametric propensity score models. In case of *ordinal or
    multinomial treatment,* `r pkg("GPSCDF")` allows to
    estimate generalized propensity score cumulative distribution
    functions.
-   Other *balancing score weighting* methods for balancing covariate
    distributions are available in `r pkg("CBPS")` (for binary
    and multivalued treatments, optionally in longitudinal settings).
    `r pkg("PSweight")` supports propensity score weighting
    analysis (including overlap weights) of observational studies and
    randomized trials (available for multivalued treatment).
    `r pkg("twang")` provides a set of functions for
    propensity score estimation and weighting (including time-varying
    and multivalued treatment), nonresponse weighting, and diagnosis of
    the weights (of nonequivalent groups).
    `r pkg("twangContinuous")` provides functions for
    propensity score estimation and weighting for continuous treatments.
-   *Doubly robust methods* are implemented in
    `r pkg("grf", priority = "core")` (function
    `average_treatment_effect` for the AIPW estimator using generalized
    random forest), in `r pkg("AIPW")` (allowing for
    user-defined stacked machine learning predictive models), in
    `r pkg("causalweight")`, in
    `r pkg("riskRegression")` (function `ate` implements a
    parametric doubly robust estimator for survival outcomes), and in
    `r pkg("DoubleML")` (function `DoubleMLIRM`).
-   *Targeted learning* (also known as targeted maximum likelihood
    estimation or targeted minimum loss-based estimation) methods are
    available in `r pkg("drtmle")`,
    `r pkg("tmle", priority = "core")`, and
    `r pkg("ltmle")` (for longitudinal data).
-   *Difference in differences* methods are implemented in
    `r pkg("DRDID")` (doubly robust estimators with two
    choices for nuisance function estimation),
    `r pkg("bacondecomp")` (using the Goodman-Bacon
    decomposition to allow for variation in treatment timing),
    `r pkg("did")` (for cases with more than two periods and
    with variation in treatment timing), and in
    `r pkg("qte")`.
-   *Quantile treatment effects* can be estimated using the
    `r pkg("qte")`, `r pkg("Counterfactual")` and
    `r pkg("grf")` packages.
-   *Odds ratio* estimation and power calculation for the *Trend in
    Trend* model is implemented in `r pkg("TrendInTrend")`.
-   *Synthetic control* methods are implemented in
    `r pkg("Synth")` (using a group method for comparative
    case studies), `r pkg("microsynth")` (for micro- and
    meso-level data), and `r pkg("gsynth")` (extension to
    multiple treated units and variable treatment periods.
-   *Instrumental variable* methods are implemented in
    `r pkg("ivmodel")`, `r pkg("ivpack")` (including
    power analysis, sensitivity analysis, and diagnostics),
    `r pkg("bpbounds")` (nonparametric bounds on ATE),
    `r pkg("grf")`, `r pkg("estimatr")`, and
    `r pkg("DoubleML")` (function `DoubleMLIIVM`).
    `r pkg("ivmte")` provides a choice-theoretic
    interpretation to IV models using *Marginal Treatment Effects* to
    extrapolate from the compliers to estimate treatment effects for
    other subpopulations; and estimation using local IVs is implemented
    in `r pkg("localIV")`. `r pkg("LARF")` uses
    Local Average Response Functions for IV estimation of treatment
    effects with binary endogenous treatment and instrument.
    `r pkg("icsw")` implements inverse compliance score
    weighting for estimating average treatment effects with an
    instrumental variable.
-   *Mediation analysis* can be performed with `r pkg("cfma")`
    (functional mediation analysis), `r pkg("cit")`
    (likelihood-based tests), `r pkg("MultisiteMediation")`
    (multisite trials), `r pkg("DirectEffects")` (controlled
    direct effect when fixing a potential mediator to a specific value)
    and `r pkg("causalweight")`.
    `r pkg("mediation")` and `r pkg("cfdecomp")`
    implement identification, inference and
    `r pkg("mediation")` additionally also provides
    sensitivity analysis for causal mediation effects. Linear mediation
    analysis for complex surveys using balanced repeated replication is
    implemented in `r pkg("MedSurvey")`.
    `r pkg("paths")` uses an imputation approach to estimate
    path-specific causal effects along with a set of bias formulas for
    conducting sensitivity analysis. `r pkg("regmedint")`
    implements regression-based analysis with a treatment-mediator
    interaction term. `r pkg("gma")` performs Granger
    mediation analysis for time series.
-   Under *interference,* causal effect estimation can be achieved using
    `r pkg("inferference")` by inverse-probability weighted
    (IPW) estimators, `r pkg("netchain")` on collective
    outcomes by chain graph models approximating the projection of the
    full longitudinal data onto the observed data, and
    `r pkg("interferenceCI")` provides some exact confidence
    intervals for treatment effects on a binary outcome in two-stage
    randomized experiments with interference.
-   Diagnostics and visualization for *Multiplicative Interaction
    Models* are implemented in `r pkg("interflex")`.
-   `r pkg("InvariantCausalPrediction")` provides confidence
    intervals for causal effects, using data collected in different
    experimental or environmental conditions (with hidden variables),
    extensions to nonlinear models are implemented in
    `r pkg("nonlinearICP")`.
-   *Regression discontinuity design* (RDD) methods are implemented in
    `r pkg("rddensity")` (density discontinuity testing (also
    known as manipulation testing)), `r pkg("rdlocrand")`
    (inference under local randomization), `r pkg("rdmulti")`
    (analysis with multiple cutoffs or scores); tools to perform power,
    sample size and minimum detectable effects (MDE) calculations are
    available in `r pkg("rdpower")`, robust confidence
    interval construction and bandwidth selection are implemented in
    `r pkg("rdrobust")`, `r pkg("RATest")` provides
    a collection of randomization tests, including a permutation test
    for the continuity assumption of the baseline covariates in the
    sharp RDD.
-   Regularized calibrated estimation of the average treatment effects
    (ATE) and local average treatment effects (LATE) is implemented in
    `r pkg("RCAL")`.
-   `r pkg("WhatIf")` offers easy-to-apply methods to evaluate
    counterfactuals that do not require sensitivity testing over
    specified classes of models.

In addition, `r pkg("causalsens")`,
`r pkg("hettx")`, `r pkg("dstat")` and
`r pkg("EValue")` provide functions for *sensitivity analyses*
(for unmeasured confounding, selection bias, measurement error),
`r pkg("ui")` implements functions to derive uncertainty
intervals and conduct sensitivity analysis for missing data and
unobserved confounding. `r pkg("BalanceCheck")` provides tests
to assess balancing of the treatment groups after matching,
`r pkg("cobalt", priority = "core")` generates balance tables
and plots before and after covariate balancing, and
`r pkg("confoundr")` implements covariate-balance diagnostics
for time-varying confounding.

[**Heterogeneous treatment effect estimation**]{#hte}

Some of the above mentioned packages can also be used for heterogeneous
treatment effect (HTE) estimation.

-   *Bayesian approaches* for individual causal effect estimation are
    available in several packages including
    `r pkg("bartCause")` (based on Bayesian Additive
    Regression Trees) and `r pkg("bcf")` (Bayesian Causal
    Forest).
-   *Efficacious treatment or population subset selection* exploiting
    treatment effect heterogeneity is implemented in
    `r pkg("FindIt")` and `r pkg("grf")`. This
    latter package supports missing covariate values using the Missing
    Incorporated in Attributes approach. Additionally the package
    `r pkg("subdetect")` provides a test for the existence of
    a subgroup with enhanced treatment effect.
-   Other approaches for personalized causal predictions are provided by
    `r pkg("EffectTreat")` (exploiting correlation-based
    expressions), and for randomized data by
    `r pkg("evalITR")` (it additionally allows for defining
    budget constraints) and by `r pkg("SortedEffects")`
    (estimation and inference methods for sorted causal effects and
    classification analysis).
-   `r pkg("stepp")` provides diagnostic plots to explore
    *treatment-covariate interactions* for survival or generalized
    linear models, applicable for continuous, binomial and count data
    arising from two or more treatment arms of a clinical trial.

[**Policy learning and dynamic treatment regimes**]{#policy}

-   Estimation of an optimal dynamic treatment regime (DTR) is
    implemented in `r pkg("iqLearn")` and
    `r pkg("DynTxRegime")` (using interactive Q-learning),
    `r pkg("listdtr")` (using list-based rules),
    `r pkg("qLearn")` (Q-learning for two stage sequentially
    randomized trials). `r pkg("quantoptr")` implements
    estimation methods for optimal treatment regimes under marginal
    quantile, marginal mean, and mean absolute difference.
    `r pkg("DTRreg")` proposes different methods such as
    G-estimation, dynamic weighted OLS and Q-learning, as well as
    several variance estimation approaches, it can handle survival
    outcomes and continuous treatment variables.
    `r pkg("QTOCen")` provides methods for estimation of mean-
    and quantile-optimal treatment regimes from censored data.
-   `r pkg("ITRLearn")` implements maximin-projection learning
    for recommending a meaningful and reliable individualized treatment
    regime, and also Q-learning and A-learning for estimating the
    group-wise contrast function. `r pkg("ITRSelect")`
    implements sequential advantage selection and penalized A-learning
    for selecting important variables in optimal individualized
    (dynamic) treatment regime in both single-stage or multi-stage
    studies. `r pkg("OTRselect")` implements a penalized
    regression method that can simultaneously estimate the optimal
    treatment strategy and identify important variables for either
    censored or uncensored continuous response.
-   `r pkg("smartsizer")` provides a set of tools for
    determining the necessary sample size in order to identify the
    optimal DTR in a *sequential, multiple assignment, randomized trial
    (SMART)* , `r pkg("DTRlearn2")` implements estimators for
    general K-stage DTRs from SMARTs with Q-learning and several
    outcome-weighted learning methods.
-   `r pkg("lpdensity")` implements a density (and
    derivatives) estimator based on local polynomial regressions for
    counterfactual analysis, program evaluation, and policy
    recommendations.
-   Estimation of treatment decision rules from a randomized clinical
    trial using Single-Index Models with Multiple-Links is implemented
    in `r pkg("simml")`, Single-Index Models with a
    Surface-Link for optimizing individualized dose rules from an
    observational study is implemented in `r pkg("simsl")`.

[**Do-calculus and causal discovery**]{#dag}

-   *Identifiability* is addressed by `r pkg("causaleffect")`
    and `r pkg("dosearch")` providing algorithms to decide
    whether a causal effect is identifiable (non-parametric
    identifiability) and by `r pkg("CausalQueries")` that
    calculates arbitrary estimands for a given causal model.
    `r pkg("causaloptim")` provides tight bounds for a user
    defined DAG, query and constraints using a symbolic linear
    optimizer.
-   `r pkg("pcalg", priority = "core")` provides a set of
    functions for *causal structure learning*: (PC, for observational
    data without hidden variables, FCI and RFCI, for observational data
    with hidden variables, and GIES, for a mix of observational and
    interventional data without hidden variables), and for *causal
    inference using graphical models* (the IDA algorithm, the Generalized
    Backdoor Criterion - GBC, the Generalized Adjustment Criterion - GAC). 
    Incorporating background knowledge is also possible.
-   *Estimation of causal effects* is possible in
    `r pkg("CIEE")` using estimating equations derived from a
    DAG and in `r pkg("InvariantCausalPrediction")` using
    adjustment sets derived from conditional independence tests that
    leverage causal invariances across environments.
-   *Causal networks estimation* is implemented in
    `r pkg("CompareCausalNetworks")`.
-   `r pkg("generalCorr")` computes generalized correlations,
    partial correlations and *plausible causal paths*.
-   Constrained maximum likelihood estimation of a DAG with intervention
    or observation data is implemented in `r pkg("intdag")`
    for linear Gaussian SEM.

In addition, `r pkg("dagitty", priority = "core")` provides
methods to define different types of graphical models (cpdags, pdag,
ect.) and to identify adjustment sets (a web-based graphical
environment is also available: [DAGitty](http://dagitty.net)).

[**Specific types of data**]{#data}

-   *Longitudinal data / time series and censored data*: Causal effect
    estimation for time series is implemented in
    `r pkg("CausalImpact")` (using a Bayesian approach),
    `r pkg("confoundr")` (covariate-balance diagnostics), and
    `r pkg("CausalMBSTS")` (for multivariate responses).
-   Other packages, such as `r pkg("PanelMatch")` implements a
    set of matching methods to time-series cross-sectional data, are
    dedicated to time series but also contain some (often basic) methods
    to handle missing data (see also `r view("MissingData")`).
-   *GWAS and SNPs*: `r pkg("CKAT")` implements kernel based
    methods to jointly test genetic main effect and gene-treatment
    interaction effects for a set of SNPs. `r pkg("epiGWAS")`
    provides functions to perform robust epistasis detection in GWAS.
-   *Example data sets* to run frequent example problems from causal
    inference textbooks are accessible through the
    `r pkg("causaldata")` package.
-   Weighted, two-mode, and longitudinal networks analysis is
    implemented in `r pkg("tnet")`

[**Specific application fields**]{#applications}

-   Behavior change sciences use specialized analyses and visualization
    tools implemented in `r pkg("behaviorchange")`.
-   Evaluation of biomarkers and estimation of treatment-biomarker
    effects can be done using tools from `r pkg("bhm")` (for
    biomarker-treatment effects).
-   Qualitative Comparative Analysis type methods are implemented in
    `r pkg("cna")`.
-   *Mendelian randomization methods* used to examine causal effects
    related to certain genes are implemented in
    `r pkg("MendelianRandomization")`,
    `r pkg("mr.raps")` (two-sample Mendelian randomization
    with summary statistics by using Robust Adjusted Profile Score),
    `r pkg("MRPC")` (PC algorithm with the principle of
    Mendelian Randomization).
-   Causal inference approaches in genetic systems exploit quantitative
    trait loci (QTL) genotypes to infer causal relationships among
    phenotypes: functions to simultaneously infer causal graphs and
    genetic architecture (acyclic and cyclic) are implemented in
    `r pkg("qtlnet")`.
-   `r pkg("tools4uplift")` uplift modeling aims at predicting
    the causal effect of an action such as a marketing campaign on a
    particular individual.
-   *Coincidence analysis* through configurational comparative methods
    is provided by `r pkg("cna")`.



### Links
-   [DAGitty: draw and analyze causal diagrams](http://dagitty.net)