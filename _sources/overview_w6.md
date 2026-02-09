# Week 6: Python Package Development and Social Coding with GitHub

```{toctree}
:maxdepth: 1
Week6/GitHub_pull_requests.md
Week6/python_packaging_with_hatch.md
```

## Learning Outcomes

- Python package development with Hatch and Hatchling
- GitHub-based open source contributions (pull requests) using the [`finm`](https://pypi.org/project/finm/) package
- LSEG Datastream via WRDS (brief overview)
- Databento: API-first market data for futures and exchange data
- Introduction to HW 4: yield curve estimation with Nelson-Siegel-Svensson

## Agenda

- Brief LSEG Datastream and Databento overview (carried over from Week 5)
  - [LSEG Datastream](./Week7/LSEG_datastream.md)
  - [Databento](./Week7/databento.md)
- Tutorial of Issue Tracker in conjunction with GitHub Pull Requests
  - [GitHub Issues and Pull Requests](./Week6/GitHub_pull_requests.md)
  - Introduce the [`finm`](https://pypi.org/project/finm/) package as the course's collaborative open-source package; a low-stakes environment for students to practice submitting PRs.
  - Note: Last year we used [`stockbeta`](https://github.com/finm-32900/stockbeta) as the example. `stockbeta` is published on [TestPyPI](https://test.pypi.org/project/stockbeta/) (but not on the real PyPI), which is useful for illustrating the TestPyPI workflow.
  - A function from the `finm` package will be used in HW 4.
- Introduction to Hatch and Hatchling
  - [Python Packaging with Hatch](./Week6/python_packaging_with_hatch.md)
- HW 4 Discussion: Yield Curve Estimation
  - Overview of the Nelson-Siegel-Svensson model and CRSP Treasury data (deferred from Week 5)
