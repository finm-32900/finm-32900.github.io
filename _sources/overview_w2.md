# Week 2: Env Files and Secrets

```{toctree}
:maxdepth: 1
Week2/WRDS_intro_and_web_queries.md
notebooks/_01_wrds_python_package.ipynb
Week2/env_files.md
Week2/github_pages_preview.md
```


## Announcements

- **No class on Monday, Jan 20** (holiday). A makeup class will be held **Tuesday, Jan 21, 6-9 PM CT on Zoom**. See the Canvas calendar for the Zoom link. The class will be recorded.
- **Final Project Partners**: Start thinking about who you'd like to partner with for the final project. I will post the project options later this week. Projects will be completed in pairs.


## Objectives

- Review [HW 1](./HW1.md):
  - How is HW 1 going? 
  - Check understanding: how did we verify that the replication was successful?
  - Today, let's talk about how to complete it. Students must run `doit` first
  and then fill in the missing code to complete the replication.
  - In the past, the first HW had students manually download the data. Differences
  in the data download steps were a common source of error.
  In today's lecture, we'll learn how to automate the data download step. Previously, this was done for you.
- Given the motivation for automating data downloads and the inspiration to create various financial reports, let's discuss the main platform for data that we'll use in this course: WRDS. We started this last week.
  - [Introduction to WRDS and WRDS Web Queries](./Week2/WRDS_intro_and_web_queries.md)
  - [Demo of the WRDS Python package](./notebooks/_01_wrds_python_package.ipynb)
- Discuss `.env` files and secrets, and how to use them in our workflow. See [Env Files](./Week2/env_files.md)
- Introduce [GitHub Pages and Tearsheets](./Week2/github_pages_preview.md) - publishing analysis results to the web
- Discuss [HW 2](./HW2.md):
  - Part 1: Replicate Fama-French 1993 portfolio analysis
  - Part 2: Create and publish a tearsheet using `quantstats_lumi` and GitHub Pages
