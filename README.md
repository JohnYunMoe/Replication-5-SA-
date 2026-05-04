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

**Task 1 — Data Inspection**
- Inspect all files in the replication package and document what each file contains and how it contributes to the study.
- Identify which files originate from the AIDev dataset and which were created by the paper's authors.
- Randomly select 3 pull requests from `python_fix_prs.csv`, open their GitHub pages, and verify whether each is a genuine bug-fix PR with a correct recorded author.

**Task 2 — Full Paper Replication**
- Rerun all provided scripts to replicate the results for RQ1 (issue frequency and density across agents) and RQ2 (severity profiles and most violated rules).
- Reproduce Table 2, Table 3, Table 4, and Figure 1 from the paper.
- Commit all intermediate outputs (CSV and JSON files) generated during the replication pipeline to this repository.

### 2. Repository Structure

Document your repository structure clearly. Organize your repository using the following standard structure:

```
README                    # Documentation for your repository
datasets/                 # Subset of data you used (if any). If you used the whole dataset, include instructions on how to download it
replication_scripts/      # Scripts used in your replication:
                          #   - If you used scripts as-is: document which scripts you ran
                          #   - If you modified scripts: include the modified scripts
                          #   - If you created new scripts: include all new scripts
outputs/                  # Your generated results only
logs/                     # Console output, errors, screenshots
notes/                    # Optional if you have any notes you took during reproduction (E.g., where you noted discrepencies etc)
```

**For each folder and file, provide a brief description of what it contains.**

### 3. Setup Instructions

- **Prerequisites**: Required software, tools, and versions
  - OS requirements
  - Programming language versions (Python, R, etc.)
  - Required packages/libraries and versions
  - Any other dependencies
- **Installation Steps**: Step-by-step instructions to set up the environment
  - How to install dependencies
  - How to configure paths or settings
  - Any environment variables needed

### 4. GenAI Usage

**GenAI Usage**: Briefly document any use of generative AI tools (e.g., ChatGPT, GitHub Copilot, Cursor) during the replication process. Include:

  - Which tools were used
  - How they were used (e.g., understanding scripts, exploring datasets, understanding data fields, debugging)
  - Brief description of the assistance provided


## Grading Criteria for README

Your README will be evaluated based on the following aspects (Total: 40 points):

### 1. Completeness (10 points)
- [ ] All required sections are present
- [ ] Each section contains sufficient detail
- [ ] Repository structure is fully documented
- [ ] All files and folders are explained
- [ ] GenAI usage is documented (if any AI tools were used)

### 2. Clarity and Organization (5 points)
- [ ] Information is well-organized and easy to follow
- [ ] Instructions are clear and unambiguous
- [ ] Professional writing and formatting
- [ ] Proper use of markdown formatting (headers, code blocks, lists)

### 3. Setup and Reproducibility (10 points)
- [ ] Setup instructions are complete and accurate, i.e., we were able to rerun the scripts following your instructions and obtain the results you reported


## Best Practices

1. **Be Specific**: Include exact versions, paths, and commands rather than vague descriptions
2. **Keep It Updated**: Ensure the README reflects the current state of your repository
3. **Test Your Instructions**: Have someone else (or yourself in a fresh environment) follow the setup instructions
4. **Document AI Usage**: If you used any GenAI tools, be transparent about how they were used (e.g., understanding scripts, exploring datasets, understanding data fields)


## Acknowledgement

This guideline was developed with the assistance of [Cursor](https://www.cursor.com/), an AI-powered code editor. This tool was used to:

- Draft and refine this documentation iteratively
