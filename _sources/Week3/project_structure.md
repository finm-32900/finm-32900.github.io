# Project Structure: "Chartbook" Template

I would like to defer much of this discussion to the discussion presented by [Cookie Cutter Data Science](https://drivendata.github.io/cookiecutter-data-science/).

The key take-aways from the Cookie Cutter Data Science project structure discussion are these:

- Other people will thank you
- You will thank you
- Data is immutable (pull fresh when you can)
- Analysis is a DAG (build system)
- "Build from the environment up" (Use a virtual environment and start sparse)
- Keep secrets out of version control. Use `.env` files.


## What is Cookiecutter?

[Cookiecutter](https://cookiecutter.readthedocs.io/) is a command-line tool that creates projects from project templates. Instead of manually creating folder structures, configuration files, and boilerplate code each time you start a new project, Cookiecutter automates this process. You point it at a template repository, answer a few prompts about your project (name, author, etc.), and it generates a fully scaffolded project ready to use.

The limitation of Cookiecutter is that it's a one-time operation: once you've created your project, there's no built-in way to incorporate updates if the template improves over time.


## What is Cruft?

[Cruft](https://cruft.github.io/cruft/) extends Cookiecutter by adding ongoing template synchronization. It is fully compatible with existing Cookiecutter templates but adds the ability to:

- **Check** if your project is up-to-date with the template (`cruft check`)
- **Update** your project when the template changes (`cruft update`)
- **View differences** between your project and the template (`cruft diff`)

This means when the course template is updated with improvements or bug fixes, you can pull those changes into your existing project rather than starting over or manually copying changes.


## Course Template

For this course, use the following Cookiecutter template with Cruft:

**Template:** [https://github.com/backofficedev/cookiecutter_chartbook](https://github.com/backofficedev/cookiecutter_chartbook)

To create a new project:
```bash
pip install cruft
cruft create https://github.com/backofficedev/cookiecutter_chartbook
```

See the template's README for detailed usage instructions and the structure it provides.


## Historical Reference

For historical reference, older versions of project templates I've used are available here:

- [https://github.com/jmbejara/blank_project/](https://github.com/jmbejara/blank_project/)
- [https://github.com/jmbejara/blank_project_simple/](https://github.com/jmbejara/blank_project_simple/)

These are now deprecated in favor of the Cookiecutter template above, which provides better maintainability through Cruft's template synchronization features.
