<p style="border:1px; border-style:solid; border-color:black; padding: 1em;">
CS-UH 3260 Software Analytics<br/>
Replication Study Guidelines<br/>
Dr. Sarah Nadi, NYUAD
</p>

# Replication Study: Beyond Bug Fixes — Agent-Generated Pull Request Code Quality

## Overview

### 1. Project Title and Overview

- **Paper Title**: Beyond Bug Fixes: An Empirical Investigation of Post-Merge Code Quality Issues in Agent-Generated Pull Requests
- **Authors**: Shamse Tasnim Cynthia, Al Muttakin, Banani Roy (University of Saskatchewan)
- **Replication Team**: John Yun Moe, Zavier Shaikh
- **Course**: CS-UH 3260 Software Analytics, NYUAD
- **Brief Description**:
  - The original paper analyzes 1,210 merged agent-generated bug-fix pull requests from 206 Python repositories, using SonarQube differential analysis to measure code quality issues newly introduced after merging. It examines issue frequency, density, severity, and rule-level prevalence across five AI coding agents: OpenAI Codex, Copilot, Devin, Cursor, and Claude Code.
  - This replication study reproduces the paper's two research questions using the provided dataset and scripts. Task 1 inspects and documents the replication package files and manually validates a sample of pull requests. Task 2 reruns the full SonarQube analysis pipeline to reproduce all reported tables and figures.

### 2. Scope of Replication

This replication covers two tasks:

**Task 1: Data Inspection**
- Inspect all files in the replication package and document what each file contains and how it contributes to the study.
- Identify which files originate from the AIDev dataset and which were created by the paper's authors.
- Randomly select 3 pull requests from `python_fix_prs.csv`, open their GitHub pages, and verify whether each is a genuine bug-fix PR with a correct recorded author.

**Task 2: Full Paper Replication**
- Rerun all provided scripts to replicate the results for RQ1 (issue frequency and density across agents) and RQ2 (severity profiles and most violated rules).
- Reproduce all the 4 tables and 1 figure from the paper.
- Commit all intermediate outputs (CSV and JSON files) generated during the replication pipeline to this repository.

### 2. Repository Structure

Document your repository structure clearly. Organize your repository using the following standard structure:

```
README                    # Documentation for this repository
replication_scripts/      # Scripts used in replication
    result-analysis.ipynb # Modified to fix some bugs
notes.md                  # Some notes about issues in the reproduction
outputs/                  # Generated results
    Agent_Statistics_Summary.csv                     # Data for Table 2 (Statistical Analysis of Issues by AI Coding Agent)
    Agent_Statistics_Summary.tex                     # Same as above, but in Latex form
    Hierarchical_Issue_Type_Severity_Agent_Table.csv # Data for Table 3 (Distribution of Issues by Type, Severity, and Agent)
    Hierarchical_Issue_Type_Severity_Agent_Table.tex # Same as above, but in Latex form
    issue_density.png                                # Figure 1 (Issue Density Across Agents)
    python_fix_prs.csv                               # PRs that are 
    technical_debt_analysis.png                      # Technical Debt Graphs
    Technical_Debt_Dunn_Test.csv                     # Dunn Test of tech debt
    Technical_Debt_Statistics_by_Agent.csv           # Stats about tech debt by agent
    Technical_Debt_by_Issue_Type_and_Agent.csv       # Breakdown of tech debt by issue type and agent
    Top5_Rules_LaTeX_Table.tex                       # Top 5 SonarQube rules with the most violations
```

### 3. Setup Instructions

- **Prerequisites**:
  - Programming language: Python 3.8+
  - Required packages/libraries and versions: pandas[pyarrow], numpy, matplotlib, seaborn, requests, python-dotenv, scipy, scikit_posthocs, cliffs_delta, fsspec, huggingface_hub
  - Other requirements: Docker or Podman
- **Installation Steps**:
  - Create & activate virtual environment (note, `$` represents your user level prompt)
    ```bash
    $ python3 -m venv .venv
    $ source .venv/bin/activate
    ```
  - Install dependencies
    ```bash
    $ pip install pandas[pyarrow] numpy matplotlib seaborn requests python-dotenv scipy scikit_posthocs cliffs_delta fsspec huggingface_hub
    ```
  - Setup SonarQube.  
    Easiest way is the following. It will automatically download and run it.
    ```bash
    $ docker run --name sonarqube -e SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true -p 9000:9000 sonarqube:community
    ```
    Note that if you stop it, you'll need to use a different command to start it again:
    ```bash
    $ docker start --attach sonarqube
    ```
  - SonarQube setup
    - Get a token by going to My Account (click on your profile icon in the top right) > Security > Generate Token. Then fill in any name and expiry data, but I'd strongly recommend getting a user token instead of a Project Analysis or Global Analysis token, to avoid permission issues.
    - Go to Administration > Global Permissions, and make sure the Create and Execute Analysis permission is checked.
  - Setup your .env file. You can see the .env.template file for what's needed, but it's just your SonarQube and GitHub token (and SonarQube URL if you changed it from the default port of 9000).
  - Then you'll need to copy over some files from the original author's repo
    - Clone it: `git clone https://github.com/cynthia247/MSR-Mining-2026.git`
    - Create a `dataset` folder in this repo, and copy over all the files from the original author's `dataset` folder
    - Also copy over the `SonarAnalysis.ipynb` to the `replication_scripts` folder, and make sure to correct the `REPO_DIR` and `SONAR_TOKEN`  variables (and `SONAR_URL` if changed).
- **Done with the setup!** Now you can run through the notebook files in `replication_scripts`.

### 4. GenAI Usage

**GenAI Usage**: GPT-5 mini (through [Duck.ai](https://duck.ai), a privacy friendly frontend for chatting with AIs) was used to help debug some SonarQube and Latex issues.

## Acknowledgement

The template this README was based on was developed with the assistance of [Cursor](https://www.cursor.com/), an AI-powered code editor, which was used to draft and refine this documentation iteratively.
