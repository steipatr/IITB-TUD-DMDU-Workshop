# Exploratory Modelling and Analysis of System Dynamics Models for Policy Analysis

This workshop explores how System Dynamics models can support policy analysis under deep uncertainty. We use models to examine alternative futures, identify vulnerabilities of candidate policies, and compare strategies across a wide range of uncertain conditions.

The workshop combines introductions to Decision Making under Deep Uncertainty (DMDU) and Exploratory Modelling and Analysis (EMA) with hands-on exercises. Participants apply computational techniques to System Dynamics models and interpret the results to develop decision-relevant insights.

## Learning objectives

By the end of the workshop, participants should be able to:

1. **Frame a policy problem under deep uncertainty** using the XLRM framework, distinguishing external uncertainties, policy levers, model relationships and performance measures.
2. **Design and conduct an exploratory simulation experiment** with a provided System Dynamics model, and use visualisations to characterise the resulting range of model behaviour.
3. **Evaluate candidate policies across uncertain conditions**, using performance criteria, robustness measures and trade-offs to support a reasoned policy comparison.
4. **Apply and interpret global sensitivity analysis** using a suitably designed simulation dataset, explaining how the results depend on the selected output measure and treatment of input uncertainty.
5. **Apply and interpret scenario discovery** to identify combinations of uncertain conditions associated with policy success or failure, and assess the quality and limitations of the resulting descriptions.
6. **Explain how Many-Objective Robust Decision Making (MORDM) and Dynamic Adaptive Policy Pathways (DAPP) extend the core workflow**, and identify when these approaches could be useful for a policy problem.

The practical sessions develop participants' ability to analyse provided models and datasets and interpret the results. The advanced session introduces MORDM and DAPP through examples and discussion; independent implementation of these approaches is beyond the scope of the workshop.

## Teaching team

| Instructor | Institution | Email |
|---|---|---|
| Om Prakash Damani | Indian Institute of Technology Bombay | [damani@cse.iitb.ac.in](mailto:damani@cse.iitb.ac.in) |
| Jayendran Venkateswaran | Indian Institute of Technology Bombay | [jayendran@iitb.ac.in](mailto:jayendran@iitb.ac.in) |
| Patrick Steinmann | Delft University of Technology | [p.steinmann@tudelft.nl](mailto:p.steinmann@tudelft.nl) |
| Coen van den Elshout | Delft University of Technology | [C.S.vandenElshout@tudelft.nl](mailto:C.S.vandenElshout@tudelft.nl) |

## Format and preparation

The workshop runs over **two days, from 09:30 to 17:30 each day**, with three two-hour teaching blocks per day. This provides **12 hours of scheduled sessions**, plus two 30-minute breaks and a one-hour lunch each day. The middle block is split across lunch. Approximately **12 hours of individual reading and preparation** complement the workshop.

Sessions combine conceptual introductions, demonstrations, practical exercises and discussion. Prepared simulation datasets are supplied for computationally demanding analyses, including global sensitivity analysis and scenario discovery, so participants can focus on applying the methods and interpreting their results.

A working knowledge of System Dynamics and basic familiarity with Python will help you get the most out of the exercises.

Before the workshop:

1. Begin with Maier et al. (2016) and Bankes (1993), then consult the starting-point readings for the practical sessions. The reading list is a reference collection; you are not expected to read every item in full before attending.
2. Choose a notebook environment and download or open the workshop material. Use Google Colab if you prefer to avoid a local Python installation.
3. Check that you can open a notebook and import the required packages in your chosen environment before the first session.
4. If you would like to discuss your own model, bring a brief description of its policy question, uncertainties, candidate policies and outputs. Bring model files and supporting data only if they can be shared with your working group. If you intend to run the model through PySD, check its compatibility in advance.

## Getting started

### Choose a notebook environment

The exercises use Jupyter notebooks (`.ipynb` files). **JupyterLab is one option, not a requirement.** You can use any compatible notebook environment, including **PyCharm**, **Visual Studio Code**, or **Google Colab**.

| Environment | Suitable if you… | Setup |
|---|---|---|
| Google Colab | Are unfamiliar with Python environments, are unsure what to choose, or want to avoid installing Python locally | Run notebooks in your browser; install workshop packages and load the required files in the Colab runtime |
| JupyterLab | Want a dedicated notebook interface running on your computer | Create a local Python environment and install the dependencies |
| PyCharm or Visual Studio Code | Already use an IDE with notebook support | Open the workshop folder and select the Python environment containing the workshop dependencies as the notebook interpreter/kernel |

**If you are unsure, Google Colab offers a low-hurdle starting point.** See Option B below. If you already work comfortably in another notebook environment, you can continue using it.

### Option A — Run locally

#### 1. Download the material

On this repository's GitHub page, select **Code → Download ZIP** and extract the archive. Open a terminal in the extracted repository folder.

Alternatively, clone the repository using Git if you already use it.

#### 2. Create a Python environment

Use Python 3.12 for the workshop environment. Use a separate environment to avoid conflicts with other projects.

**Windows — Command Prompt:**

```bat
py -3.12 -m venv .venv
.venv\Scripts\activate.bat
```

**macOS / Linux:**

```bash
python3.12 -m venv .venv
source .venv/bin/activate
```

#### 3. Install the dependencies

With the environment activated, run:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

The core packages are:

| Package | Purpose |
|---|---|
| `ema-workbench` | Experimental design, exploratory modelling and policy analysis |
| `SALib` | Global sensitivity analysis |
| `matplotlib` | Plotting |
| `numpy` | Numerical computation |
| `pandas` | Working with tabular data |
| `pysd` | Running supported System Dynamics models in Python |

Check the installation:

```bash
python -c "import ema_workbench, SALib, matplotlib, numpy, pandas, pysd; print('Core packages imported successfully')"
```

This checks package imports; it does not verify that a particular model or exercise runs successfully.

#### 4. Open the notebooks

**JupyterLab:** install JupyterLab and its Python kernel, then launch it:

```bash
python -m pip install jupyterlab ipykernel
python -m jupyterlab
```

Open the relevant exercise notebook in the browser and run its cells in order. Keep the terminal running while using JupyterLab.

**PyCharm or Visual Studio Code:** open the extracted repository folder in your IDE, open the relevant `.ipynb` file, and select the workshop environment as the notebook interpreter/kernel. Install `ipykernel` in that environment if needed. You do not need to launch the JupyterLab interface to work in your IDE.

See the [PyCharm notebook documentation](https://www.jetbrains.com/help/pycharm/jupyter-notebook-support.html) for environment-specific instructions.

### Option B — Run in Google Colab

[Google Colab](https://colab.research.google.com/) lets you run notebooks in your browser without installing Python or an IDE on your computer.

1. Open Colab and sign in with your Google account.
2. Open a workshop notebook from GitHub using Colab's notebook-opening dialogue, or upload a downloaded `.ipynb` file.
3. Save your own copy in Google Drive so you can retain your changes.
4. Upload `requirements.txt` and the model/data files required by the exercise using Colab's Files panel. Preserve the folder structure expected by the notebook. Opening a notebook from GitHub does not automatically download its supporting files.
5. Install the workshop dependencies in a notebook code cell:

   ```python
   %pip install -r /content/requirements.txt
   ```

6. Run the notebook cells in order. If you uploaded supporting files to a different location, adjust the file paths or working directory as needed.

Colab runtimes are temporary: uploaded runtime files and installed packages may need to be restored after a runtime reset. Save notebooks in Drive and download or save results you want to keep. Prepared datasets reduce the computation needed for the heavier exercises. If a notebook requires external desktop modelling software, use the prepared results or a compatible local setup instead.

See the [Colab FAQ](https://research.google.com/colaboratory/faq.html) for details on opening notebooks, files and runtime behaviour.

## Programme

All times are local to the workshop venue. Each block includes time for questions and discussion of the exercises.

### Day 1 — From problem framing to policy evaluation

| Time | Session | Focus |
|---|---|---|
| 09:30–11:30 | **1. Foundations** | Deep uncertainty, exploratory modelling and the XLRM framework. Frame a policy problem and identify uncertainties, levers and performance criteria. |
| 11:30–12:00 | Break | |
| 12:00–13:00 | **2. Open exploration — introduction and briefing** | Experimental design, sampling, model execution and visualisation; demonstration and exercise briefing. |
| 13:00–14:00 | Lunch | |
| 14:00–15:00 | **2. Open exploration — exercise and discussion** | Explore model behaviour across uncertain conditions and interpret the resulting ensemble. |
| 15:00–15:30 | Break | |
| 15:30–17:30 | **3. Policy analysis under uncertainty** | Compare candidate policies using performance thresholds, trade-offs and robustness measures. Discuss the implications for policy choice and review the day's lessons. |

### Day 2 — Explaining outcomes and extending the workflow

| Time | Session | Focus |
|---|---|---|
| 09:30–11:30 | **4. Global sensitivity analysis** | Apply sensitivity analysis to a prepared simulation dataset; interpret influential inputs, interactions and the consequences of analytical choices. |
| 11:30–12:00 | Break | |
| 12:00–13:00 | **5. Scenario discovery — introduction and briefing** | Define outcomes of interest, introduce scenario discovery and PRIM/CART, and discuss behaviour-based scenario discovery; demonstration and exercise briefing. |
| 13:00–14:00 | Lunch | |
| 14:00–15:00 | **5. Scenario discovery — exercise and discussion** | Use a prepared ensemble to identify conditions associated with outcomes of interest and assess the resulting descriptions. |
| 15:00–15:30 | Break | |
| 15:30–17:30 | **6. Advanced approaches and synthesis** | Introductions to MORDM and DAPP, discussion of participants' applications, and Q&A. |

The final block allocates approximately 30 minutes to MORDM, 30 minutes to DAPP, 20 minutes to applying the ideas to participants' problems, and 40 minutes to Q&A and synthesis. Participants consider how they would design an experiment and analysis for their own model or policy problem.

## Key readings by session

Each segment has two readings. **Start here** identifies the recommended entry point for the first five sessions; companion readings provide additional foundations or methodological detail. Both advanced-session papers are optional extensions.

### 1. Foundations

- **Start here — Maier, H. R., et al. (2016).** [An uncertain future, deep uncertainty, scenarios, robustness and adaptation: How do they fit together?](https://doi.org/10.1016/j.envsoft.2016.03.014) *Environmental Modelling & Software, 81*, 154–164.  
  An overview of the relationships between uncertainty, scenarios, robustness and adaptation.

- **Bankes, S. (1993).** [Exploratory Modeling for Policy Analysis.](https://doi.org/10.1287/opre.41.3.435) *Operations Research, 41*(3), 435–449.  
  The foundational argument for using computational experiments to reason about systems under significant uncertainty.

### 2. Open exploration

- **Start here — Kwakkel, J. H., & Pruyt, E. (2013).** [Exploratory Modeling and Analysis, an approach for model-based foresight under deep uncertainty.](https://doi.org/10.1016/j.techfore.2012.10.005) *Technological Forecasting and Social Change, 80*(3), 419–431.  
  Connects exploratory modelling to applications, including System Dynamics.

- **Kwakkel, J. H. (2017).** [The Exploratory Modeling Workbench: An open source toolkit for exploratory modeling, scenario discovery, and (multi-objective) robust decision making.](https://doi.org/10.1016/j.envsoft.2017.06.054) *Environmental Modelling & Software, 96*, 239–250.  
  Introduces the software architecture and analytical workflow. Consult current software documentation alongside the paper for executable examples.

### 3. Policy analysis under uncertainty

- **Start here — Lempert, R. J. (2019).** [Robust Decision Making (RDM).](https://doi.org/10.1007/978-3-030-05252-2_2) In *Decision Making under Deep Uncertainty: From Theory to Practice*, pp. 23–51. Springer.  
  An open-access introduction to stress-testing strategies and using the results within a decision-support process.

- **McPhail, C., et al. (2018).** [Robustness Metrics: How Are They Calculated, When Should They Be Used and Why Do They Give Different Results?](https://doi.org/10.1002/2017EF000649) *Earth's Future, 6*, 169–191.  
  Explains how robustness measures reflect different considerations and why they can produce different policy rankings.

### 4. Global sensitivity analysis

- **Start here — Pianosi, F., et al. (2016).** [Sensitivity analysis of environmental models: A systematic review with practical workflow.](https://doi.org/10.1016/j.envsoft.2016.02.008) *Environmental Modelling & Software, 79*, 214–232.  
  An overview of sensitivity analysis purposes, methods, workflow and consequential analytical choices.

- **Saltelli, A., et al. (2019).** [Why so many published sensitivity analyses are false: A systematic review of sensitivity analysis practices.](https://doi.org/10.1016/j.envsoft.2019.01.012) *Environmental Modelling & Software, 114*, 29–39.  
  A critique of common practices, including inadequate exploration of combinations of uncertain inputs.

### 5. Scenario discovery

- **Start here — Bryant, B. P., & Lempert, R. J. (2010).** [Thinking inside the box: A participatory, computer-assisted approach to scenario discovery.](https://doi.org/10.1016/j.techfore.2009.08.002) *Technological Forecasting and Social Change, 77*(1), 34–49.  
  Introduces scenario discovery as the identification of interpretable combinations of conditions associated with policy vulnerabilities.

- **Steinmann, P., Auping, W. L., & Kwakkel, J. H. (2020).** [Behavior-based scenario discovery using time series clustering.](https://doi.org/10.1016/j.techfore.2020.120052) *Technological Forecasting and Social Change, 156*, 120052.  
  Extends scenario discovery by identifying distinct temporal behaviours before finding their associated input conditions.

### 6. Advanced approaches — MORDM and DAPP

- **Kasprzyk, J. R., Nataraj, S., Reed, P. M., & Lempert, R. J. (2013).** [Many objective robust decision making for complex environmental systems undergoing change.](https://doi.org/10.1016/j.envsoft.2012.12.007) *Environmental Modelling & Software, 42*, 55–71.  
  The original MORDM paper, combining generation of policy alternatives, exploration of trade-offs and robustness assessment.

- **Kwakkel, J. H., Haasnoot, M., & Walker, W. E. (2015).** [Developing dynamic adaptive policy pathways: a computer-assisted approach for developing adaptive strategies for a deeply uncertain world.](https://doi.org/10.1007/s10584-014-1210-4) *Climatic Change, 132*, 373–386.  
  Demonstrates model-based evaluation and optimisation of adaptation pathways.

## Further reading

- **Marchau, V. A. W. J., Walker, W. E., Bloemen, P. J. T. M., & Popper, S. W. (Eds.). (2019).** [*Decision Making under Deep Uncertainty: From Theory to Practice.*](https://doi.org/10.1007/978-3-030-05252-2) Springer.  
  An open-access reference covering DMDU approaches, applications and implementation. Select chapters according to your interests.

- **Auping, W. L., d'Hont, F. M., Kubli, M. D., Slinger, J. H., Steinmann, P., van der Heijde, F. T., van Daalen, C., Pruyt, E., & Thissen, W. A. H. (2024).** [*The Delft Method for System Dynamics.*](https://doi.org/10.59490/tb.97) TU Delft OPEN Publishing.  
  An openly available reference for the System Dynamics modelling cycle, with theory and exercises on model development, evaluation and policy analysis.

- **Halim, R. A., Kwakkel, J. H., & Tavasszy, L. A. (2016).** [A scenario discovery study of the impact of uncertainties in the global container transport system on European ports.](https://doi.org/10.1016/j.futures.2015.09.004) *Futures, 81*, 148–160.  
  An application linking exploratory simulation, scenario discovery and optimisation-based worst-case discovery to the competitive position of European ports. Relevant to open exploration, policy analysis and scenario discovery.

- **Kwakkel, J. H., Auping, W. L., & Pruyt, E. (2013).** [Dynamic scenario discovery under deep uncertainty: The future of copper.](https://doi.org/10.1016/j.techfore.2012.09.012) *Technological Forecasting and Social Change, 80*(4), 789–800.  
  A copper-scarcity application using time series clustering to identify dynamics of interest and scenario discovery to investigate their associated conditions. Relevant to open exploration and scenario discovery.

- **Student, J., Kramer, M. R., & Steinmann, P. (2020).** [Simulating emerging coastal tourism vulnerabilities: an agent-based modelling approach.](https://doi.org/10.1016/j.annals.2020.103034) *Annals of Tourism Research, 85*, 103034.  
  Uses the Coasting agent-based model of Curaçao's coastal tourism to study emerging socio-ecological vulnerabilities through global sensitivity analysis and scenario discovery.

- **Student, J., Kramer, M. R., & Steinmann, P. (2020).** [Coasting: Model description, global sensitivity analysis, and scenario discovery.](https://doi.org/10.1016/j.mex.2020.101145) *MethodsX, 7*, 101145.  
  The methodological companion to the tourism application, with implementation details for sensitivity analysis and scenario discovery.

- **Greeven, S., Kraan, O., Chappin, É. J. L., & Kwakkel, J. H. (2016).** [The Emergence of Climate Change Mitigation Action by Society: An Agent-Based Scenario Discovery Study.](https://doi.org/10.18564/jasss.3134) *Journal of Artificial Societies and Social Simulation, 19*(3), 9.  
  An agent-based application connecting exploratory modelling and scenario discovery to narratives of strong and weak climate mitigation action.

- **Jafino, B. A., & Kwakkel, J. H. (2021).** [A novel concurrent approach for multiclass scenario discovery using Multivariate Regression Trees: Exploring spatial inequality patterns in the Vietnam Mekong Delta under uncertainty.](https://doi.org/10.1016/j.envsoft.2021.105177) *Environmental Modelling & Software, 145*, 105177.  
  Compares a sequential clustering-and-rule-induction approach with simultaneous classification of output patterns and identification of input subspaces using Multivariate Regression Trees. An extension of tree-based scenario discovery, applied to spatial inequality in farm profitability.

- **Reed, P. M., Hadka, D., Herman, J. D., Kasprzyk, J. R., & Kollat, J. B. (2013).** [Evolutionary multiobjective optimization in water resources: The past, present, and future.](https://doi.org/10.1016/j.advwatres.2012.01.005) *Advances in Water Resources, 51*, 438–456.  
  Provides background for the advanced session through a diagnostic assessment of multiobjective evolutionary algorithms and discussion of computational search and trade-offs in water-resource applications.

- **Zatarain Salazar, J., Castelletti, A., & Giuliani, M. (2022).** [Multi-Objective Robust Planning Tools.](https://doi.org/10.1093/acrefore/9780199389414.013.626) *Oxford Research Encyclopedia of Environmental Science*. Oxford University Press.  
  An encyclopedia overview of multiobjective robust planning, uncertainty and alternative analytical frameworks. A companion to the MORDM session for participants seeking a broader methodological perspective.

## Getting help

During the workshop, ask the teaching team if you encounter installation problems or unexpected results. When reporting a technical problem, include your operating system, Python version, the file or notebook involved, and the full error message. Remove personal or confidential information before sharing logs or screenshots.

## Copyright and reuse

Copyright remains with the respective rights holders. Refer to the licence and attribution notices accompanying individual files.

Third-party material is subject to its original terms and is excluded from any general licence applied to the original workshop contributions, unless explicitly stated otherwise. Inclusion in this repository does not grant additional reuse rights. Where no reuse licence is stated, no general permission to redistribute or adapt the material is granted.
