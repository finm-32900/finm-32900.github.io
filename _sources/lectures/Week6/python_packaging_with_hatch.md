# Writing and Publishing Your Own Python Packages

**Objectives of This Chapter**

This chapter introduces the process of writing Python packages using a tool called [**Hatch**](https://hatch.pypa.io/), an official, standards-based Python packaging tool maintained by the Python Packaging Authority ([PyPA](https://www.pypa.io/)). We will:

1. Discuss the fundamental components of a Python package.
2. Demonstrate how to use Hatch for package development and management.
3. Together we will walk through the development of an example package, `stockbeta`, designed for quantitative finance applications. We will develop this package together from scratch and learn how to publish it to PyPI.
4. Explore how this knowledge can be applied to real-world scenarios in the financial industry.

## Introduction

### Motivation: Why Write Python Packages?

Financial institutions and companies rely heavily on custom libraries to handle complex calculations, manipulate large datasets, and implement models that are central to their decision-making processes. Python has emerged as a dominant language in the finance industry, and understanding how to package and distribute Python libraries is a critical skill.

Knowing how to write Python packages provides several key benefits:

- **Reusability and Collaboration**: Packaging code allows you to create tools that can be easily reused across projects and shared with colleagues or clients.
- **Version Control and Maintenance**: A properly structured package supports versioning, making it easier to track changes and maintain functionality over time.
- **Career Readiness**: Many roles in quantitative finance, data science, and software engineering value candidates who can create and maintain robust software libraries.
- **Open Source Contributions**: Python packages are the building blocks of the open-source ecosystem. Understanding the packaging process allows you to contribute to or build on existing tools.
- **Scalability**: Developing modular code within a package structure helps scale analytics workflows and integrates with corporate software pipelines.

Let's explore several concrete scenarios where understanding Python packaging is valuable:

1. **Publishing Open-Source Packages**
   - As a student or developer, you can share your tools with the global Python community through PyPI
   - Example: You build a machine learning utility that simplifies data preprocessing, then publish it so others can benefit
   - In your particular case as a student, developing open source packages to contribute, e.g., via PyPI has several benefits: 
     - Demonstrates practical Python skills to potential employers
     - Shows ability to write maintainable, documented code
     - Builds your professional portfolio
     - Provides experience with modern development workflows (CI/CD, documentation, testing)

2. **Corporate Private Package Repositories**
   - Many companies maintain internal package repositories for proprietary code
   - Business cases:
     - Protect intellectual property (e.g., proprietary trading algorithms)
     - Share internal tools across teams without exposing them publicly
     - Ensure code consistency across different projects (e.g., when multiple teams need to access the same database, having a shared package with standardized connection methods ensures everyone follows security protocols and best practices, rather than each team implementing their own potentially inconsistent solutions)
     - Using a share package repository makes it easier to manage dependencies and ensure that all teams are using the same version of a package. For example, it can otherwise be hard to make sure that everyone is using the same version of an internal package, e.g., `yourcompanycustompythonpackage`.
   - Example: A financial firm maintains a private package with
     - Custom risk calculation models
     - Company-specific data processing pipelines
     - Standardized reporting templates
     - Internal API clients

3. **Academic and Research Distribution**
   - Universities and research labs package their algorithms and models
   - Benefits:
     - Makes research reproducible
     - Allows other researchers to build on your work
     - Simplifies collaboration between institutions
   - Example: A research group packages their novel optimization algorithm, allowing others to:
     - Verify their results
     - Apply the algorithm to new problems
     - Cite the work in academic papers
     - See [Open Source Asset Pricing](https://www.openassetpricing.com/) and an associated Python package: https://github.com/mk0417/open-asset-pricing-download



### Evolution of Python Packaging

The Python packaging ecosystem has evolved significantly over the years. The landscape has evolved significantly:

1. **Early Days (pre-2012)**:
   - Pip didn't support binary distributions
   - Scientific packages were difficult to install
   - No standardized solution for non-Python dependencies

2. **Conda Era (2012-present)**:
   - Conda solved the binary distribution problem
   - Provided consistent environments across platforms
   - Became standard in scientific computing

3. **Modern Convergence**:
   - Pip's wheel format (introduced 2012) solved many binary distribution issues
   - Build tools like `cibuildwheel` made it easier to distribute compiled packages
   - Conda remains valuable for:
     - Cross-language dependencies
     - System-level packages
     - Consistent scientific computing environments

Today, the choice between pip and conda often depends on:
- Whether you need non-Python dependencies
- The specific packages you're using
- Your platform requirements
- Performance considerations



#### Historical Context

- **[Distutils](https://docs.python.org/3/library/distutils.html) (2000-2020)**: Python's original built-in packaging tool, included in the standard library. It provided basic functionality for:
  - Building source distributions
  - Installing Python modules
  - Basic compilation of extension modules

  However, it lacked crucial features like dependency management, binary distributions, and version handling. Its minimal feature set and inability to adapt to modern Python packaging needs led to its deprecation in Python 3.10 and removal in Python 3.12.

- **[Setuptools](https://setuptools.pypa.io/) (2004-present)**: Originally created as an enhancement to Distutils, it became the de facto standard for Python packaging. It introduced:

  - The `setup.py` configuration file
  - `easy_install` package installer
  - Dependency management
  - Entry points and console scripts
  - Automatic package discovery

  While still widely used, Setuptools has fallen out of favor due to:
  - Security concerns with executing arbitrary Python code in `setup.py`
  - Complex and sometimes unpredictable configuration (e.g., `setup.py` might behave differently based on installed packages or environment variables, making builds inconsistent across systems)
  - Lack of standardization in build processes (e.g., different packages might use different build backends, custom build steps, or non-standard commands in their `setup.py`, making it harder to understand and maintain build processes across projects)
  - Difficulty in maintaining reproducible builds (e.g., two developers running the same `setup.py` might produce different packages due to differences in their local Python environments or setuptools versions)

- **[pip](https://pip.pypa.io/) (2008-present)**: Replaced `easy_install` as the primary package installer, still dominant today. Introduced:

  - Requirements files for dependency specification (e.g., `requirements.txt`)
  - Better dependency resolution
  - More reliable installation process
  - Support for various package formats and sources (e.g., source distributions, binary distributions, and editable installs)

- **[wheel](https://wheel.readthedocs.io/) format (2012-present)**: Introduced a faster, more reliable binary package format that:

  - Eliminates the need to run `setup.py` during installation
  - Provides consistent installations across platforms
  - Reduces installation time
  - Supports reproducible builds

- **Python Packaging Authority (2011-present)**: Founded as the working group that maintains and evolves the core projects of Python packaging. It:

  - Maintains key tools like pip, wheel, and virtualenv
  - Develops packaging standards through PEPs (Python Enhancement Proposals)
  - Provides official documentation at packaging.python.org
  - Coordinates between different packaging tools and projects
  - Ensures security and reliability of Python's package ecosystem
  - Manages [PyPI](https://pypi.org/) (Python Package Index), the official package repository

#### The Rise of Binary Distribution and Scientific Computing

The landscape evolved significantly to address challenges in distributing scientific Python packages:

1. **Early Challenges (pre-2012)**:
   - Pip struggled with binary distributions (e.g., installing NumPy or SciPy often failed because pip couldn't handle the pre-compiled C extensions, requiring users to have the correct compiler and development headers installed). Thus, scientific packages were difficult to install due to compilation requirements
   - No standardized solution for non-Python dependencies. For example, C libraries like OpenBLAS (used for fast linear algebra), Fortran compilers for scientific packages, or system dependencies like CUDA for GPU computing had to be manually installed by users, making it difficult to ensure consistent installations across different machines.
   - Complex build dependencies and platform-specific configurations

2. **Solutions and Progress (2012-present)**:
   - Introduction of the wheel format solved many binary distribution issues
   - Build tools like `cibuildwheel` simplified compiled package distribution
   - Conda emerged as a comprehensive solution for scientific computing. Conda was created by Continuum Analytics (now Anaconda Inc.) in 2012 to solve the "dependency hell" of scientific Python packages by providing language-agnostic package management, handling both Python and non-Python dependencies like compilers and system libraries in one tool. Most students in the data science field are familiar with Conda, as it is packaged with the Anaconda distribution and it is the standard for scientific computing in Python.
   - Modern build systems improved cross-platform compatibility.

#### Modern Packaging Tools

Several tools now compete in the Python packaging space:

- **[Hatch](https://hatch.pypa.io/)**: An official PyPA tool that provides a modern, comprehensive approach to package management. Benefits include:

  - Single `pyproject.toml` configuration. Note that `pyproject.toml` is the new standard for Python projects, replacing `setup.py` and `setup.cfg`. However, `setup.py` is still widely used and supported.
  - Built-in environment management (e.g., `hatch env create`). Recall that environment management means that Hatch will create a virtual environment with the dependencies installed.
  - Standardized build system (e.g., `hatch build`). 
  - Simplified publishing workflow (e.g., `hatch publish` will build the package and upload it to PyPI).
  - Active maintenance by PyPA

- **[Poetry](https://python-poetry.org/)**: Popular alternative that offers:

  - Dependency resolution
  - Virtual environment management
  - Similar `pyproject.toml` configuration
  - Strong community support

```{note}
Some criticisms of Poetry include:

- "Poetry does several things by default that are bad for libraries - see https://iscinumpy.dev/post/poetry-versions/ for some details." (from [here](https://news.ycombinator.com/item?id=31192499))
- Tensorflow and PyTorch have some issues on Poetry.
```

- **[PDM](https://pdm.fming.dev/)**: Newer tool focusing on:
  - PEP 582 compliance
  - Fast dependency resolution
  - Modern package management

- **[Flit](https://flit.pypa.io/)**: Lightweight tool ideal for:
  - Simple Python packages
  - Quick publishing to PyPI
  - Minimal configuration

- **[uv](https://github.com/astral-sh/uv)**: New tool that is gaining popularity. It is a drop-in replacement for `setuptools` and `wheel`. Benefits include:
  - Extremely fast package installation (10-100x faster than pip)
  - Written in Rust for performance and safety
  - Compatible with existing Python tooling (requirements.txt, pyproject.toml)
  - Smart caching of wheel builds
  - Built-in virtual environment management
  - Deterministic builds with precise dependency resolution
  - Memory efficient, using ~10MB RAM vs pip's ~100MB

```{note}
Many people see `uv` as the future of Python packaging. However, it is still in its early stages, though it is gaining traction and developing fast.
```

#### Cross-platform Package Management

The need for cross-platform package managers arose primarily from challenges in distributing scientific Python packages. In the early days of pip, packages with compiled extensions (like NumPy, SciPy) were difficult to install because they required:
- Specific C/Fortran compilers
- Complex build dependencies
- Platform-specific configurations

This led to the development of more comprehensive solutions:

- **[Conda](https://docs.conda.io/)**: Industry standard for cross-platform package management, particularly in data science. Created by Continuum Analytics (now Anaconda Inc.) in 2012 to solve the "dependency hell" of scientific Python packages. Benefits include:
  - Language-agnostic package management (handles Python, R, C++, etc.)
  - Built-in environment management
  - Binary package distribution
  - Platform-specific dependency resolution
  - Large ecosystem of pre-built scientific packages
  - Strong integration with commercial tools (Anaconda)
  - Ability to install non-Python dependencies (e.g., CUDA, MKL, compilers)

```{note}
Some criticisms of Conda include:
- Slower than pip for Python-only installations
- Can be complex to debug when environment conflicts occur
- Large installation size for the base system
```

- **[Mamba](https://mamba.readthedocs.io/)**: A faster reimplementation of Conda, written in C++. Features include:
  - Parallel downloads and faster dependency solving
  - Drop-in replacement for conda commands
  - Compatible with existing conda packages
  - Much better performance for large environments
  - More reliable solver that can better explain conflicts

- **[Pixi](https://pixi.sh/dev/)**: Modern alternative to Conda, built by Prefix.dev. (Also, see [here.](https://prefix.dev/docs/pixi/overview)) Features include:
  - Rust-based implementation for better performance
  - Compatible with existing Conda packages
  - Simpler configuration via `pixi.toml`
  - Faster environment solving
  - Built-in task running capabilities
  - Lock file for reproducible environments
  - Project-based environment management

```{note}
While Pixi is promising, it's still relatively new (launched 2023) and the ecosystem is evolving. Some users report that certain edge cases aren't yet handled as well as in Conda. Note, however, that the exciting Mojo project's package manager is [built on top of Pixi.](https://docs.modular.com/magic/)
```

## New Patterns in Modern Package Management

### Project-Based Package Management vs Environment-Based Package Management

- **Project-Based Package Management**: This is the approach used by Hatch, Poetry, and PDM. It involves:
  - A single configuration file (`pyproject.toml`) that defines both project metadata and dependencies
  - Dependencies are specified at the project level
  - Virtual environments are created automatically based on project needs
  - Build and development dependencies are clearly separated
  - Lock files ensure reproducible builds across different machines
  - Tools typically manage the entire project lifecycle (building, testing, publishing)

  This approach has gained favor in modern Python development because:
  - It follows the "configuration as code" principle
  - Makes projects more portable and reproducible
  - Reduces the gap between development and deployment
  - Better integrates with modern CI/CD practices
  - Follows similar patterns to other language ecosystems (npm for Node.js, Cargo for Rust)

- **Environment-Based Package Management**: This is the approach used by Conda, Mamba, and Pixi. It involves:
  - Creating isolated environments that can be activated/deactivated
  - Dependencies are managed at the environment level
  - One environment can be used for multiple projects
  - Environments can include non-Python packages
  - Manual environment activation is typically required
  - Configuration often spans multiple files (environment.yml, requirements.txt)

  This approach has historically been popular because:
  - It's more flexible for scientific computing needs
  - Better handles system-level dependencies
  - Works well for exploratory data science
  - Supports multiple programming languages in one environment

#### Pros and Cons

**Project-Based Approach**

Pros:
- Clearer dependency specification
- Better reproducibility
- Integrated tooling (build, test, publish)
- More aligned with modern DevOps practices
- Smaller, more focused environments

Cons:
- Limited to Python packages
- Can be more complex for beginners
- May require additional setup for system dependencies
- Multiple projects = multiple environments

**Environment-Based Approach**

Pros:
- Handles non-Python dependencies well
- More flexible for scientific computing
- Can share environments across projects
- Better for exploratory work
- Easier for beginners

Cons:
- Less reproducible across systems
- Configuration can be scattered
- Heavier weight solutions
- Manual environment management

#### The Shift Towards Project-Based Management

The Python ecosystem has been gradually shifting towards project-based management because:

1. **Modern Development Practices**:
   - Microservices architecture demands more isolated, reproducible projects
   - CI/CD pipelines benefit from deterministic builds
   - Container-based deployment favors project-specific dependencies

2. **Lessons from Other Ecosystems**:
   - Success of npm (Node.js) and Cargo (Rust) showed benefits of project-centric approach
   - Growing emphasis on reproducible builds
   - Need for better dependency resolution

3. **Python Packaging Standards**:
   - PEP 517/518 standardized build system specification
   - `pyproject.toml` provides a single source of truth
   - Better separation of development and runtime dependencies

However, both approaches remain valid, and the choice often depends on specific needs:
- Scientific computing often favors environment-based tools
- Web development typically uses project-based tools
- Data science might use a mix of both approaches


### Package Metadata and Version Management

Modern Python packaging tools handle metadata and versioning differently:

- **Traditional Approach (setup.py)**:
  ```python
  setup(
      name="mypackage",
      version="0.1.0",
      author="Your Name",
      description="Package description"
  )
  ```

- **Modern Approach (pyproject.toml)**:
  ```toml
  [project]
  name = "mypackage"
  version = "0.1.0"
  authors = [{name = "Your Name", email = "your.email@example.com"}]
  description = "Package description"
  ```

Key advantages of the modern approach:
- Declarative configuration (no executable code)
- Standardized format across tools
- Better security (no arbitrary code execution during build)
- Easier to parse and validate
- Single source of truth for package metadata

### Development Dependencies

Modern packaging tools provide better separation of development and runtime dependencies:

```toml
[project]
dependencies = [
    "requests>=2.28.0",
    "pandas>=1.5.0"
]

[project.optional-dependencies]
test = [
    "pytest>=7.0.0",
    "pytest-cov>=4.0.0"
]
dev = [
    "black>=23.0.0",
    "mypy>=1.0.0",
    "ruff>=0.1.0"
]
```

This separation:
- Keeps production installations lean
- Makes development setup reproducible
- Clearly documents tool requirements
- Allows selective installation of extras

## Choosing a Packaging Tool

While this chapter focuses on Hatch, consider these factors when choosing a tool:

- **Project Size**: Smaller projects might benefit from Flit's simplicity.
- **Team Experience**: Some teams may be more familiar with Poetry or Setuptools.
- **Corporate Requirements**: Enterprise environments might have specific tooling needs.
- **Feature Requirements**: Different tools excel at different aspects of package management.

## Example Package: `stockbeta`

The `stockbeta` package (see [PyPI](https://test.pypi.org/project/stockbeta/#description) and [GitHub](https://github.com/finm-32900/stockbeta-example)) is a practical demonstration of how to write a Python library for quantitative finance. This package performs factor-based analysis of stock returns, leveraging the Fama-French Three-Factor Model. It provides tools for:

1. Loading and manipulating factor data (e.g., market returns, size, and value factors).
2. Analyzing the factor exposures of individual stocks using their historical return data.
3. Generating concise reports summarizing the findings.

I chose this example because I wanted to demonstrate how to do the following things when creating a Python package:

- Add a command-line interface (CLI) to the package.
- Add the ability to use the functions in the package as a library or from the command line.
- Ship datasets with the package.


### Getting Started: Using `stockbeta`

To get started, first take a look at the project page on [Testing.PyPI](https://test.pypi.org/project/stockbeta/) and then follow the instructions below.

Install the package from Testing.PyPI:

```console
pip install -i https://test.pypi.org/simple/ stockbeta
```

#### Loading Factor Data

Demonstrate how to load factor data using the library:

```python
import stockbeta

# Load all available daily factor data
factors = stockbeta.load_factors()
```

#### Analyzing Stock Returns

Show how to analyze stock returns using both the CLI and the Python library interface:

**CLI Example**
```console
python -m stockbeta.cli --ticker AAPL --start 2020-01-01 --end 2023-12-31
```

**Library Example**
```python
import stockbeta
import yfinance as yf

# Get stock data
stock_data = yf.download("AAPL", start="2020-01-01", end="2023-12-31")
stock_returns = stock_data["Adj Close"].pct_change().dropna()

# Load factors and calculate exposures
factors = stockbeta.load_factors(start="2020-01-01", end="2023-12-31")
exposures = stockbeta.calculate_factor_exposures(stock_returns, factors)

print(exposures)
```

### Preview of the Development Workflow with Hatch

Now, before we start developing a package from scratch, let's take a look at how to modify the `stockbeta` package. To do this, we'll review the development workflow with Hatch.

1. Cloning the repository:
```console
git clone https://github.com/finm-32900/stockbeta-example.git
cd stockbeta-example
```

2. Activating the Hatch shell environment:
```console
hatch shell
```

3. Running tests and making edits:
```console
hatch test           # Run all tests
hatch test -v       # Run tests with verbose output
hatch test --cover  # Run tests with coverage
```

4. Formatting and linting code:
```console
hatch fmt           # Format code
hatch fmt --check   # Check formatting
```

5. Deploying updates to PyPI:

This following command won't work for you because you haven't set up your PyPI credentials and because you're not on the `stockbeta` team. In any case, I use GitHub Actions to publish the package to TestPyPI.

```console
hatch publish 
```

```{note} Eample
As an example, let's now make our own quick modification to the `stockbeta` package and verify that it works for us.
```

## Developing a Python Package with Hatch

Now that we've seen a short preview of the development workflow with Hatch, let's take a look at the overview of the hatch development workflow. 

### Workflow Overview

1. Overview of Hatch

Hatch is a modern Python packaging tool that simplifies the development, testing, and deployment of Python packages. Its features include:

- **Environment Management**: Automatically creates isolated development environments with dependencies installed.
- **Simplified Configuration**: Uses a single `pyproject.toml` file for project metadata.
- **Command Line Tools**: Provides commands for common tasks such as running tests, checking types, and formatting code.

2. Setting Up the Package

- Directory structure and organization.
- Creating a `pyproject.toml` file.
- Initializing a development environment with Hatch.

3. Adding Functionality

- Writing core modules: example implementation of factor data loading and factor analysis.
- Packaging datasets: including sample data with the package.
- Creating a command-line interface (CLI) for ease of use.

4. Testing and Quality Assurance

- Writing unit tests with `pytest`.
- Running tests with Hatch.
- Configuring type checking and linting.

5. Documenting the Package

- Writing a README file to introduce the package and explain its usage.
- Generating API documentation.

6. Publishing to PyPI

- Steps to register the package on PyPI.
- Uploading the package using Hatch.

### Developing a Python Package from Scratch

TODO

### CLI Development: Click vs. argparse

The `stockbeta` package also demonstrates how to create a command-line interface (CLI) using [Click](https://click.palletsprojects.com/), a modern Python package for creating beautiful command line interfaces. While Python's standard library includes [argparse](https://docs.python.org/3/library/argparse.html) for CLI development, we chose Click for several reasons:

#### Why Click Over argparse?

- **Decorator-Based Interface**: Click uses decorators to define commands and options, resulting in more readable and maintainable code:
  ```python
  # Click example
  @click.command()
  @click.option('--ticker', required=True, help='Stock ticker symbol')
  def analyze(ticker):
      """Analyze a stock's factor exposures."""
      pass

  # Equivalent argparse example
  parser = argparse.ArgumentParser()
  parser.add_argument('--ticker', required=True, help='Stock ticker symbol')
  args = parser.parse_args()
  ```

- **Automatic Help Generation**: Click automatically generates well-formatted help messages and documentation.
- **Nested Command Support**: Easily create complex CLI applications with subcommands (similar to `git commit`, `git push`).
- **Type Conversion**: Automatic type conversion and validation of input parameters.
- **Better Error Messages**: More user-friendly error messages out of the box.

#### Why argparse is Still Relevant

While we chose Click for `stockbeta`, argparse remains important to understand:
- It's part of Python's standard library (no additional dependencies)
- Many existing projects use it
- It's more than adequate for simple CLI needs
- It has been the standard since Python 2.7

#### Modern CLI Development

The trend in Python CLI development has moved towards more sophisticated tools like Click because:
- They reduce boilerplate code
- They encourage better CLI design practices
- They provide better developer experience
- They often result in better user experience

For `stockbeta`, Click allows us to create an intuitive interface that makes it easy for users to:
- Specify date ranges for analysis
- Select specific stocks or factors
- Control output formats
- Access help and documentation

#### Editable Installs

During development, you often want changes to your source code to be immediately reflected without reinstalling the package. Modern tools support this through editable installs:

```console
# Traditional pip approach
pip install -e .

# Hatch approach (automatic in development shell)
hatch shell
```

Benefits of editable installs:
- Immediate reflection of code changes
- No need to reinstall after each modification
- Maintains proper package imports
- Preserves development tool configurations

### Publishing Packages to PyPI

Package distribution is a crucial part of the Python ecosystem. While private package repositories exist for organizations that want to keep their code proprietary, the Python Package Index (PyPI) serves as the primary public repository for Python packages. When you run `pip install some-package`, pip typically fetches that package from PyPI.

#### Understanding PyPI and TestPyPI

PyPI (Python Package Index) is often called the "Cheese Shop" - a reference to a Monty Python sketch. It serves as the official repository for Python packages, hosting over 400,000 projects. However, publishing directly to PyPI without testing can be risky. This is where TestPyPI comes in.

TestPyPI is a separate instance of the Python Package Index that allows developers to practice package distribution without affecting the main PyPI repository. It's particularly valuable for:

1. **Educational Purposes**: Learning the publishing workflow without risk
2. **Testing**: Verifying package metadata, README rendering, and installation
3. **CI/CD Development**: Setting up and testing automated release workflows

For example, to install a package from TestPyPI:

```console
pip install --index-url https://test.pypi.org/simple/ your-package-name
```

#### Automated Releases with GitHub Actions

Modern Python package development often leverages CI/CD pipelines for automated releases. In the `stockbeta` package, we use GitHub Actions to automate the release process to TestPyPI. The workflow is triggered by git tags:

```yaml
strategy:
  matrix:
    python-version: ["3.8", "3.9", "3.10", "3.11", "3.12"]
```

This configuration means:
1. The workflow triggers when we push a tag starting with 'v' (e.g., v0.1.0)
2. It uses Trusted Publishing with PyPI (via the `id-token: write` permission)
3. It builds and publishes the package automatically

#### Version Management and Common Issues

Package versioning is critical in Python distribution. PyPI enforces strict version uniqueness - once a version is published, it can never be reused, even if deleted. This policy prevents supply chain attacks but can cause issues during development.

Common versioning patterns include:
- Release versions: `0.1.0`, `1.0.0`
- Development versions: `0.1.0.dev1`, `0.1.0.dev20231225`
- Post-releases: `0.1.0.post1`
- Release candidates: `0.1.0rc1`

A real-world example we encountered with `stockbeta`:
```python
# Initial release
version = "0.0.1"

# Development builds (automated via GitHub Actions)
version = "0.0.2.dev42"  # where 42 is the build number

# Cannot reuse "0.0.2" if it was ever published, even if deleted
# Must use either:
version = "0.0.3"  # increment version
# or
version = "0.0.2.post1"  # post-release
```

#### Security Considerations

Publishing packages requires careful attention to security:

1. **Trusted Publishing**: Modern PyPI supports keyless authentication using OpenID Connect, eliminating the need for API tokens.

2. **Package Signing**: Tools like `sigstore` (used by PyPI) help verify package authenticity.

3. **Version Immutability**: Once published, package versions cannot be modified or reused, preventing supply chain attacks.

4. **Access Control**: Use organization accounts and role-based access for team projects.

#### Best Practices for Package Publishing

1. **Always Test on TestPyPI First**
   - Verify package metadata
   - Check README rendering
   - Test installation process

2. **Use Semantic Versioning**
   - Major.Minor.Patch (e.g., 1.2.3)
   - Increment appropriately based on changes

3. **Automate Releases**
   - Use CI/CD pipelines (like GitHub Actions)
   - Automate version bumping
   - Include automated tests before publishing

4. **Documentation**
   - Maintain clear installation instructions
   - Document version compatibility
   - Keep a detailed changelog

5. **Distribution Format**
   - Build both source distributions (.tar.gz) and wheels (.whl)
   - Use tools like `hatch` or `build` for consistent builds


### The Importance of Matrix Testing

When developing Python packages, ensuring compatibility across different Python versions and operating systems is crucial. This is where matrix testing comes in - it allows us to test our code against multiple configurations simultaneously.

#### Real-World Example: The Distutils Deprecation

During the development of the `stockbeta` package, we encountered an interesting issue that perfectly illustrates why matrix testing is essential. Here's the error we received when testing against Python 3.12:

```
ModuleNotFoundError: No module named 'distutils'
```

This error occurred because one of our dependencies, `pandas_datareader`, was indirectly using `distutils` through its dependency chain:

```
stockbeta → pandas_datareader → pandas_datareader.compat → distutils
```

The issue wasn't apparent in Python 3.11 and earlier versions because `distutils` was part of the standard library. However, it was removed in Python 3.12 as part of [PEP 632](https://peps.python.org/pep-0632/). Without matrix testing, we might have shipped a package that worked fine for most users but would break for anyone using Python 3.12.

#### How Matrix Testing Helped

Our GitHub Actions workflow was configured to test against multiple Python versions:

```yaml
strategy:
  matrix:
    python-version: ["3.8", "3.9", "3.10", "3.11", "3.12"]
```

This configuration caught the compatibility issue before release. We fixed it by:
1. Adding `setuptools` as a dependency (which provides `distutils`)
2. Later updating to newer versions of dependencies that had removed the `distutils` dependency

#### Lessons Learned

This experience highlights several key points about modern Python package development:

1. **Dependency Management**: Your package might break due to changes in indirect dependencies. Matrix testing helps catch these issues early.

2. **Python Evolution**: The Python language and standard library evolve over time. What works in one version might not work in another.

3. **Forward Compatibility**: Testing against pre-release Python versions (like 3.12 before it was released) helps ensure your package stays compatible with future Python releases.

4. **Automated Testing**: Automated CI/CD pipelines with matrix testing can catch issues that might be missed in local development, where developers typically use only one Python version.

## Conclusion

By the end of this chapter, you will understand the process of creating Python packages using Hatch and see how the `stockbeta` example applies these concepts. Writing Python libraries is a valuable skill that bridges the gap between technical programming and applied finance, enabling you to create tools that are both robust and impactful.
