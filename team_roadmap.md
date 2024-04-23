# (DRAFT) About team and roadmap
---

# About the team
The current team started in summer of 2022 (with #1232) and constitutes the
projects 3rd generation of maintainers.
Consisting of three members with diverse backgrounds (@aryoda, @buhtz, @emtiu),
the team benefits from the assistance of the former maintainer, @Germar,
who contributes from behind the scenes.

All team members are engaged in every aspect of the project, including code
analysis, documentation, solving issues, and the implementation of new
features. This work is carried out voluntarily during their limited spare time.

# Strategy Outline
The following tries to give a broad overview of the tasks or steps to
enhance _Back In Time_ as a software and as a project. The schedule is
not fixed, nor is the order of priority.

- [Analyzing code and behavior](#analyzing-code-and-behavior)
- [Code quality & unit tests]([#code-quality--unit-tests](#code-quality--unit-tests))
- [Issues](#issues)
- [Replace encryption library EncFS or remove it](#replace-encryption-library-encfs-or-remove-it)
- [Project infrastructure](#project-infrastructure)
- [Graphical User Interface (GUI): Redesign and Refactoring](#graphical-user-interface-gui-redesign-and-refactoring)
- [Terminal User Interface](#terminal-user-interface)

## Analyzing code and behavior
As none of the current team members were involved in the original
development of _Back In Time_, there is a lack of deep understanding of
certain aspects of the codebase and its functionality. Part
of the work done in this project involves conducting research on the code,
its features, infrastructure, and documenting the findings.

## Code quality & unit tests
One challenge resembles a chicken-and-egg problem: the code structure
lacks sufficient isolation, making it difficult, if not nearly impossible in some cases,
to write valuable unit tests. Heavy refactoring of the code is necessary,
but this carries a high risk of introducing new bugs. To mitigate this risk,
unit tests are essential to catch any potential bugs or unintended changes
in the behavior of _Back In Time_. Thus, the circle is closed.

Considering the three major types of tests (unit, integration, system), the
current test suite primarily consists of system tests. While these system
tests are valuable, their purpose differs from that of unit tests. The
codebase has very low coverage of real unit tests (in the meaning of behavioral
focused _Classical_ test school).

The codebase does not adhere to [PEP8](https://peps.python.org/pep-0008/),
which serves as the minimum Python
coding style. Utilizing linters in their default configuration is currently
not feasible. One of our objectives is to align with PEP8 standards and
meet the requirements of code linters.

## Issues
All existing issues have been triaged by the current team.
[Labels](https://github.com/bit-team/backintime/labels) are assigned
to indicate priority, along with
a [milestone](https://github.com/bit-team/backintime/milestones)
indicating which planned release
will address the issue. Some of these issues persists for a long time and
involve multiple complex problems. They can be challenging to diagnose due
to various factors. Enhancing test coverage and code quality is one
aspect aimed at finding and implementing solutions for these issues.

## Replace encryption library EncFS or remove it
Currently, _Back In Time_ uses [EncFS](https://github.com/vgough/encfs) for
encrypting backups, but it has known security vulnerabilities
(see issue #1549). This requires replacing it, with
[GoCryptFS](https://github.com/rfjakob/gocryptfs) as a potential candidate.
However, lack of resources hinders this effort.
If no volunteers step forward, the encryption feature will be removed,
prioritizing user security and team maintenance efforts.

## Project infrastructure
At present, _Back In Time_ utilizes a build system that relies on `make`. However,
this approach has several shortcomings and does not adhere to modern standards
in Python packaging ([PEP 621](https://peps.python.org/pep-0621),
[PEP 517](https://peps.python.org/pep-0517),
[src layout](https://packaging.python.org/en/latest/tutorials/packaging-projects),
[pyproject.toml](https://setuptools.pypa.io/en/latest/userguide/pyproject_config.html)).
The team intends to migrate to these contemporary standards to streamline
the maintenance of _Back In Time_ (#1575).

## Graphical User Interface (GUI): Redesign and Refactoring
Over the years, the GUI has become increasingly complex. It requires a visual
redesign as well as code refactoring. Additionally, it lacks tests.

## Terminal User Interface
Various people use _Back In Time_ via the terminal, for example, through an SSH
shell on a headless server. There is an idea of creating a terminal user
interface (TUI) or to enhance the existing command-line interface (CLI).
See #254. The proposal of having a web frontend was rejected (#209). Of course
separate projects offering a web fronted will be supported of course.
