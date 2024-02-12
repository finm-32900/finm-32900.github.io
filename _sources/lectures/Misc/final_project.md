# Final Project

In this project, you'll replicate tables, figures, or data series from a well known finance paper using the principals of reproducible analytical pipelines (RAPs) learned in this class. Your replication must be automated from end-to-end, formatted using the [project template](https://github.com/jmbejara/blank_project) I have provided, which is based upon the [Cookiecutter Data Science](https://drivendata.github.io/cookiecutter-data-science/) template.

## Receiving Your Assigned Project

  - You will be assigned a project from the list found [here.](./potential_final_projects.md) 
  - Your preference will be taken into account when assigning the projects. You can rank your preferred projects by using the following Google Form: https://forms.gle/EKkPQSX6uWipZhdx5 . Please, only submit one response per group. Your group must have 4 people in it. Some exceptions may be made for groups of 5.
  - You will meet with me at the beginning of the project as well as at the end (a consultation). The first meeting is to establish the goals for the project. The final meeting is to present your results. When you submit the link, you will also have a chance to schedule your consultation and final presentation dates. The link the page to book these meetings is in the Canvas announcement.
  - In this first consultation meeting, you should come prepared with a list of tasks that each team member will be primarily responsible for. Team members can and should share tasks (e.g., two people can be responsible for the LaTeX writeup whereas everyone should be involved in figuring out how to understand and clean the data). Write this list of tasks in the README.md of the GitHub repo.

## Final Project Grading Rubric

The following questions or assertions will be made of your code when you present it at the end of the quarter. Each question will be subjectively prorated on the degree of completion. For example, if you replicate 50% of the numbers from a table, you'll get 50% of the available points. Some adjustments may be made by discretion based on the difficulty of the task.
For each assertion in the following, I enumerate the points each is worth in **bold** and there are a total of 182 points available in total.


- **4/4** You must generate a single LaTeX document that briefly describes the nature of the replication project and contains all the tables and charts that your code produces. You should give a high level overview of how the replication project went. Where did you find success, where were the challenges? Also, explain the data sources that you used? The LaTeX document should not contain code snippets, but only give the tables and charts and a high level discussion of the project.
- **4/4** Provide at least one jupyter notebook that gives an brief tour of the cleaned data and some of the analysis that is performed in the code. You can think of this as giving the reader a tour of the code that you have written. You can provide code snippets in this notebook. It should look somethin like one the HW guides that we used, e.g. [Wage Growth During the Recession](../../output/_01_wage_growth_during_the_recession.ipynb)
- **20/20** Replicate the series, tables, and/or figures listed for your assigned project. Choose a reasonable tolerance and construct unit tests to ensure that your numbers match the paper's within this tolerance.
- **20/20** Now, reproduce the series, tables, and/or figures with updated numbers. That is, replicating the numbers from the paper require performing the calculations over the same time period as that of the paper. In this task, you'll recalculate the series, tables, and/or figures using numbers up until the present (or at least the most recently available numbers).
- **20/20** Outside of the tables, figures, or derived series that you are to replicate, have you also provided a table of your own summary statistics AND charts that gives you and the reader of sufficient understanding of the underlying data. These tables and/or figures must be typeset on LaTeX and you must provide captions on the Tables and Figure that properly describe them and motivate them. That is, you must tell me in the caption what I should learn or take away from each table and figure. You are to choose how many figures and or tables is sufficient for your case, but it will usually be one of each.
- **4/4** Does the paper generate a tidy data set of the data being used before then using the data for analysis? Specifically, there must be a separate file or set of files whose only purpose is to clean the data and put it into a "tidy" format. The analysis of the data should be kept in separate files.
- **4/4** Are the statistics in all tables in the LaTeX document automatically generated from the code?
- **4/4** Is the project automated from end-to-end, using PyDoit?
- **4/4** Does the repository use unit tests to ensure that code is working properly? Are these unit tests well motivated?
- **4/4** Does the project use the template from https://github.com/jmbejara/blank_project ?
- **4/4** Does each unit test have a purpose? Are there unnecessary or repetitive unit tests?
- **4/4** Is the GitHub repository and the Git history free of any copyrighted material (e.g., the raw data should not be in the repo).
- **4/4** Is the GitHub repository and the Git history free of any secrets, such as API keys?
- **4/4** Does the project use a `.env` file as well as reasonable defaults in the `config.py` file to manage the configuration of the project (e.g., the data directory, the API keys, but also the `START_DATE` and `END_DATE` of the time period of analysis of the project.) Is the format of the required `.env` file described in an example `env.example` file?
- **4/4** The project must not contain a trace of `.env` (it should not be in the Git commit history).
- **4/4** Does the project contain a `requirements.txt` file that described the required packages to run the project's code?
- **4/4** Is the GitHub repository and the Git history free of any secrets, such as API keys?
- **4/4** Has each group member made commits to the Git repo?
- **4/4** Has each member of your group made and merged a GitHub pull request?
- **4/4** Does each Python file have a "docstring" at the top that describes what the file does?
- **4/4** Does each Python function have a reasonably descriptive name and, when appropriate, a function docstring? (No need to overboard, but the code should be reasonably clean.)
- **50/50** Did I individually accomplish the tasks that were assigned to me by the group and did I contribute a substantial part of the code to the project as evidenced by the commit history?

 
 
