# Homework 3

- **Due Date:** Tuesday, Feb 10 at 11:59 pm.
- **Link to Assignment:** https://classroom.github.com/a/FQKccYH-

## Overview

```{tip} Keep it simple — this is just a first step!
The goal of this homework is **not** to finish your final project. It is simply to help you **get oriented** with your datasets and project infrastructure. You only need to demonstrate that you can pull *something* from each required data source and produce *any* simple exploratory plot for each. The charts do not need to be polished or directly related to the paper's analysis — any plot that shows the data was successfully retrieved is sufficient. There will be plenty of time to refine your work later.
```

Project assignments will be emailed on Wednesday, January 28. You and your partner will be assigned one project from the [list of potential final projects](./FinalProject/potential_final_projects.md). In this homework, you will set up the repository for your final project using the cookiecutter chartbook template, pull data from each of your data sources, create a simple exploratory chart for each to verify you can access and work with the data, and publish your chartbook site via GitHub Pages.

See the [Final Project Instructions and Rubric](./FinalProject/final_project_rubric.md) for full details on how the final project will be graded. This homework gets you started on the infrastructure.

## Part 0 (not graded): Review Resources

Before starting, please review the following:

- [Project Structure: "Chartbook" Template](./Week3/project_structure.md) — Explains the cookiecutter chartbook template and how to use cruft.
- [Final Project Instructions and Rubric](./FinalProject/final_project_rubric.md) — Grading criteria for the final project.
- [Potential Final Projects](./FinalProject/potential_final_projects.md) — The list of assigned projects and their data sources.

## Part 1 (graded): Set Up Your Final Project Repository

### Step 1: Create the Repository

One team member should create a **public** GitHub repository under their own GitHub user account. The repository must be named using the following convention:

```
pXX_lastnames_year
```

where:
- `XX` is the zero-padded project number from the [potential final projects list](./FinalProject/potential_final_projects.md)
- `lastnames` is the authors' last names from the paper (lowercase, separated by underscores, hyphens preserved within hyphenated names)
- `year` is the publication year of the paper

**Examples:**
- Project 1 (Kelly and Pruitt, 2013): `p01_kelly_pruitt_2013`
- Project 5 (Lopez-Lira and Tang, 2023): `p05_lopez-lira_tang_2023`
- Project 8 (Jiang, Matvos, Piskorski, and Seru, 2024): `p08_jiang_et_al_2024`

If the paper has more than three authors, you may use `et_al` in place of the remaining author names.

After creating the repository, add your partner as a **collaborator** (Settings > Collaborators > Add people). Both team members should contribute commits to the repository. The other student can optionally fork the repo so that it shows up on both students' GitHub profiles.

### Step 2: Scaffold with the Cookiecutter Chartbook Template

Use [cruft](https://cruft.github.io/cruft/) to scaffold your project from the [cookiecutter chartbook template](https://github.com/backofficedev/cookiecutter_chartbook):

```bash
pip install cruft
cruft create https://github.com/backofficedev/cookiecutter_chartbook
```

Answer the prompts with your project's details. Copy the generated files into your repository (or run the command directly inside your cloned repo directory). Commit and push.

For more details on the template and cruft, see [Project Structure: "Chartbook" Template](./Week3/project_structure.md).

### Step 3: Set Up Data Pull Scripts

For **each distinct data source** your assigned project requires (e.g., CRSP, Compustat, FRED, Bloomberg, OptionMetrics, etc.), create a `src/pull_*.py` script that programmatically downloads the data. Refer to the "Data sources" listed for your assigned project in the [potential final projects list](./FinalProject/potential_final_projects.md).

Requirements:
- Follow the naming convention: `pull_CRSP_stock.py`, `pull_compustat.py`, `pull_fred.py`, etc.
- Each pull script should save its output to the `_data/` directory as a `.parquet` file.
- If a data source requires credentials (e.g., WRDS), use a `.env` file and document the required environment variables in `.env.example`.
- Add each pull script as a task in your `dodo.py` file.

### Step 4: Create Exploratory Charts

The purpose of this step is simply to demonstrate that you were able to successfully pull and work with each dataset. For **each distinct data source**, create at least one simple exploratory chart that:
- Loads the pulled data from `_data/`
- Creates any simple visualization — a time series plot, a histogram, a scatter plot, or anything else that shows the data was retrieved successfully
- Saves the chart as an interactive HTML file in `_output/` (using [Plotly](https://plotly.com/python/) or a similar library)

Don't overthink this — any plot that helps you get oriented with the data is fine. You will have time to create more polished charts later.

You may create charts in a `src/generate_chart.py` file or in separate scripts. Add chart generation as a task in `dodo.py`.

### Step 5: Register Dataframes and Charts in `chartbook.toml`

For **each distinct data source**, add entries in your `chartbook.toml`:

1. One `[dataframes.<name>]` entry describing the dataset — include metadata such as `data_sources`, `data_providers`, `how_is_pulled`, and `path_to_parquet_data`.

2. One `[charts.<name>]` entry describing the exploratory chart — include `chart_name`, `short_description_chart`, `dataframe_id`, and `path_to_html_chart`.

Refer to the `chartbook.toml` in the template or the course examples for the required fields and format.

### Step 6: Build and Publish the Chartbook Site

1. Run the full pipeline:
   ```bash
   doit
   ```

2. Build the chartbook site:
   ```bash
   chartbook build -f
   ```
   This generates the `docs/` folder containing a static website.

3. Commit and push the `docs/` folder to your `main` branch.

4. Enable GitHub Pages on your repository:
   - Go to your repo's **Settings > Pages**
   - Under "Source", select **Deploy from a branch**
   - Select the `main` branch and the `/docs` folder
   - Click **Save**

5. Verify your site is live at:
   ```
   https://<username>.github.io/pXX_lastnames_year/
   ```

## Part 2 (graded): Schedule a Consultation

Schedule a consultation meeting with the instructor using the following link:

- **Booking link:** [https://finm-32900.youcanbook.me/](https://finm-32900.youcanbook.me/)

You must **schedule** the meeting before the homework deadline. You do not need to have attended the meeting before the deadline — only the booking needs to be completed.

**Purpose of the consultation:** You and your partner should come to the meeting prepared with:
- A plan for how you will complete the final project
- A division of responsibilities between team members (who is primarily responsible for which tasks)
- Any questions or concerns about feasibility (e.g., data access issues, unclear requirements)

I will use this meeting to verify that the work is being divided appropriately, provide guidance on the project, and help modify requirements if something turns out not to be feasible (e.g., you do not have access to the necessary data).

Ideally, you should have your exploratory plots (from Part 1) completed before the meeting so we can discuss your initial findings. However, if you need extra help getting situated with the data, that is fine — we can work through it together in the consultation.

## Part 3 (graded): Set Flags in the HW3 GitHub Classroom Repo

Accept the GitHub Classroom assignment using the link at the top of this page. In the HW3 repo, edit `src/final_project_flags.py` to set all of the following:

1. `I_HAVE_CREATED_MY_FINAL_PROJECT_REPO = True`
2. `URL_TO_MY_FINAL_PROJECT_REPO = "https://github.com/<username>/pXX_lastnames_year"`
3. `I_HAVE_CREATED_A_CHARTBOOK_SITE_ON_GITHUB_PAGES = True`
4. `URL_TO_MY_CHARTBOOK_SITE = "https://<username>.github.io/pXX_lastnames_year/"`
5. `I_HAVE_REGISTERED_DATAFRAMES_IN_CHARTBOOK_TOML = True`
6. `I_HAVE_REGISTERED_CHARTS_IN_CHARTBOOK_TOML = True`
7. `I_HAVE_SCHEDULED_A_CONSULTATION = True`

The autograder will run `pytest` against `src/test_final_project_flags.py` to verify that all flags are set and all URLs are non-empty.

## Reminder

Do not make any changes to the unit test files. If an edit is made, you will be required to edit the history of your commits to remove any trace of the edits to these files.
