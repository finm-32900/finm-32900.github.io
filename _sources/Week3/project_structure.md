# Project Structure

I would like to defer this discussion to the discussion presented by [Cookie Cutter Data Science](https://drivendata.github.io/cookiecutter-data-science/).
The template that I use for my [`blank_project` repository](https://github.com/jmbejara/blank_project) borrows from their template.

The key take-aways from the Cookie Cutter Data Science project structure discussion are these:

- Other people will thank you
- You will thank you
- Data is immutable (pull fresh when you can)
- Analysis is a DAG (build system)
- "Build from the environment up" (Use a virtual environment and start sparse)
- Keep secrets out of version control. Use `.env` files.


