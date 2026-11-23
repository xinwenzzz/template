# Project structure and grading
The project should be submitted as a GitHub repository. The repository should be organized so that another person can understand the problem, reproduce the simulations, and explore the results without additional instructions.


## README.md (6 points)
The README is the entry point to the project. It should give a reader a clear overview of the problem, the approach, and the repository, and guide them to the tutorials.

The README is graded on the following criteria:

- **Title and group information (1p).** A clear and descriptive title, the names of all group members, and their affiliation.
- **Introduction and approach (1p).** A description of the problem being studied, why it is interesting, and the overall approach taken in the project, in a few sentences. The details belong in the tutorials.
- **Repository overview and usage (1p).** A short description of the main files and modules, and instructions for installing the required packages and running the tutorials and tests.
- **Links to tutorials (1p).** Links to all tutorials, each with a short description of what it demonstrates, listed in the order they are meant to be read.
- **References (1p).** A complete list of the references used in the project, including 3–5 peer-reviewed references per group member that are relevant to the models and methods studied. References for data and reused code are listed in addition to these. Each reference includes the authors, title, year, journal or publisher (with volume and pages, where applicable), and a DOI or link, in a consistent format, for example:

    > Vicsek, T., Czirók, A., Ben-Jacob, E., Cohen, I., & Shochet, O. (1995). Novel Type of Phase Transition in a System of Self-Driven Particles. *Physical Review Letters*, 75(6), 1226–1229.  https://doi.org/10.1103/PhysRevLett.75.1226

    Each reference in the list should be cited where it is used, in the README, the tutorials, or the source code.
- **Contributions (1p).** A description of each group member's contributions to the project, including the lead author of each tutorial.


## Tutorials (21 points)
The `tutorials/` folder contains .ipynb notebooks that run without any changes. All file paths in the notebooks are relative (e.g., `results/simulation.csv`), not absolute (e.g., `C:/Users/...`), so that the notebooks also run on other computers. A tutorial that does not run cannot be graded and will receive 0 points. The notebooks should be submitted already executed, with all outputs visible.

All packages used in the project must be installable with `pip` and listed, with their versions, in a `requirements.txt` file in the root of the repository (e.g., `numpy==2.5.4`).

As a guideline, each tutorial should run from top to bottom in under 10 minutes on a standard laptop. If longer simulations are needed, save their results in a `results/` folder inside the tutorial folder and load them in the notebook. Include a variable at the top of the notebook (e.g., `RUN_SIMULATIONS = False`) that lets the reader choose between loading the saved results and rerunning the full simulations.

Each group member writes one tutorial as its lead author, so the number of tutorials equals the group size (one to three). The lead author is stated at the top of the tutorial and in the Contributions section of the README. Group members may help each other, but the lead author is responsible for the content and quality of their tutorial and receives the points for it, while the other parts of the repository are graded for the group as a whole. Each tutorial is graded on the following criteria:

- **Question and conclusions (2p).** The introduction states the question the tutorial addresses and why it is interesting. The tutorial ends with a short summary of its conclusions that answers this question.
- **Structure and conciseness (2p).** The sections follow a logical order, and each one contributes to answering the question. There is no unnecessary repetition, code, or printed output. Longer is not better.
- **Model and methods (4p).** The model, simulation method, and analysis are explained in Markdown cells where they are introduced. All parameters (with values and units) and modeling assumptions are stated. The main parts of the code are explained, so that the reader can follow what is done and why, with inline comments where the code needs further clarification. Sources for models, methods, and data are cited where they are used.
- **Depth of analysis (6p).** The tutorial includes at least three of the following, each giving up to 2p:
    - A systematic parameter study (e.g., a parameter sweep or phase diagram)
    - Statistics over multiple independent runs, with uncertainties shown
    - Validation against an analytical result, a known limit, or the literature
    - A comparison between two models, methods, or algorithms
- **Results and interpretation (6p).** Figures are clear, with labeled axes, units, and legends where needed. Each result is interpreted in the text: what it shows, and how it relates to the question. The tutorial includes at least one visualization of the simulation itself (e.g., an animation or a few snapshots of a short run), with a brief explanation of what to observe. Of the 6p, 3p are awarded for figures and visualization, and 3p for interpretation of the results.
- **Reproducibility (1p).** Random number generators are seeded where applicable, so that rerunning the notebook reproduces the outputs shown, also when the full simulations are rerun (e.g., with `RUN_SIMULATIONS = True`).


## Source code (8 points)
The `src/` folder contains the source code used to implement the simulations and analysis. The tutorials should import their functionality from here. To make `src/` importable, add `import sys; sys.path.append("..")` at the top of each notebook, so that, for example, `from src.model import simulate` works. The code should run without any changes.

The source code is graded on the following criteria:

- **Implementation (4p).** The main models, simulations, and/or algorithms of the project are implemented correctly and completely, and support everything shown in the tutorials.
- **Organization (2p).** The code is organized into meaningful functions, classes, and modules, with a logical structure and without large amounts of duplicated code. Parameters are passed as arguments rather than hard-coded, and no absolute file paths are used.
- **Documentation (1p).** All functions and classes have docstrings briefly describing their purpose, inputs, and outputs. Comments are used where the logic is not obvious from the code itself.
- **Readability (1p).** Functions, classes, and variables have clear and descriptive names, and the code follows the PEP 8 style guide (https://peps.python.org/pep-0008/).


## Testing (4 points)
The `tests/` folder contains tests that check that the source code works as intended. Testing simulations is often less about checking exact outputs and more about checking properties that the results must satisfy, such as conserved quantities, known limiting cases, or agreement with analytical results. These properties can be tested at two levels. Unit tests check individual functions or classes in isolation, while system tests run a complete (small and short) simulation from start to finish and check its results. The same property can often be tested at both levels: for example, a unit test can check that a single elastic collision conserves momentum and kinetic energy, while a system test can check that the total energy stays within a given tolerance over a full run. The tests should include both types.

All tests must run with `pytest` from the root of the repository without any changes, all tests must pass, and together they should run in at most a minute. Tests should have descriptive names, with a short comment where it is not obvious why the expected result is correct.

Testing is graded on the following criteria:

- **Unit tests (2p).** At least one unit test for each of the main functions and classes in `src/`, each checking a meaningful property, and at least 3 unit tests per group member.
- **System tests (2p).** At least one system test per tutorial, which runs a small version of the main simulation used in that tutorial from start to finish and checks meaningful properties of the results.


## Data (optional)
The `data/` folder contains external data used in the simulations or analysis, such as experimental measurements, initial conditions, or network datasets. It is only needed if the project uses such data. Results produced by the tutorials' own simulations belong in the `results/` folder of the tutorials instead.

If data is included, its source should be listed in the References, and its format and contents should be described in the README. Large datasets should not be committed to Git. Instead, provide instructions or scripts for obtaining them.


## Repository structure (2 points)
The repository should follow the template provided for the course, so that the different parts of the project are easy to find.

The repository structure is graded on the following criteria:

- **Template and naming (1p).** The repository follows the structure of the course template, with the README, `requirements.txt`, tutorials, source code, tests, and (optional) data in their designated places. Files and folders have meaningful, consistent names that reflect their contents. Numbering the tutorials in their reading order is recommended.
- **Clean repository (1p).** The repository contains no unnecessary files, such as temporary files or old versions of notebooks and code. A `.gitignore` file can be used to keep such files out of the repository.


## GitHub practices (3 points)
The project should be developed with Git from the start, so that the commit history shows how the work progressed. All group members are expected to contribute substantially to the project, with their own commits, consistent with the Contributions section of the README. The commit history and the Contributions section are used to assess individual contributions, and grades may be adjusted individually.

The project is submitted through GitHub releases: two pre-releases during the project and one final release at the deadline. The dates for all releases can be found on Canvas. The final release is graded.

GitHub practices are graded on the following criteria:

- **Commit messages (1p).** Each commit has a meaningful message describing the change (e.g., "Add parameter sweep for noise strength" rather than "update" or "fix stuff").
- **Regular commits (1p).** Commits are reasonably small and focused, and are made regularly throughout the project rather than committing the whole project in a few large commits at the end.
- **Releases (1p).** The two pre-releases and the final release are created on time from the `main` branch, with the version tags `v1.0.0-alpha`, `v1.0.0-beta`, and `v1.0.0`. The pre-releases are marked as pre-releases on GitHub, and each release has short release notes describing what was added or changed since the previous one.
