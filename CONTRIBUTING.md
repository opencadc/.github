# Contributing to OpenCADC

OpenCADC is the GitHub Organization used by the Canadian Astronomy Data Centre (CADC) and the Canadian Advanced Network for Astronomical Research (CANFAR).

We welcome contributions at OpenCADC!  If you have a fork or clone of any of the software maintained here in the OpenCADC GitHub repository, please consider contributing any changes you make back to the origin repository here at OpenCADC.  This benefits all involved.  We will be sure to respond in a timely manner to any issues or pull requests created.

## Creating Issues

Create issues when you discover any sort of problem with OpenCADC software or want to propose a new feature. Ensure the bug was not already reported by searching on GH Issues first. Only if you're unable to find an open issue addressing the problem, open a new one. Be sure to include a title and clear description, as much detail as possible, and a code sample or an executable test case demonstrating the unexpected behavior.

Use the same mechanism for new proposed features providing a rationale for it. It is a good idea to wait for feedback debating the merits of the feature before starting to implement it.

If you end up working on a solution for the issue, it should be referenced in the associated Pull Request.

## Guidelines for Pull Requests

In OpenCADC, the publicly released code lives in the main (or master) branch of the GitHub repository.  Therefore, contributions (modifications, additions) to OpenCADC software must be done through Pull Requests (PR).  While the pull request is open, OpenCADC maintainers will correspond with you through the PR.  Generally, before the PR is merged to the main branch, repositories will require:
* A code review with approval
* Code style conventions to be met
* Automated tests to pass

### Java Development Guidelines

TODO
* checkstyle
* CI

### Python Development Guidelines
Related Python projects are grouped in repos, each repo containing a number of application projects: `cadctools`, `caom2tools`, `vostools`. A project of general interest might be published on `PyPI` (The Python Project Index).
The OpenCADC Python software is expected to be available and work with all the official active versions of Python (see https://devguide.python.org/versions/.)

#### Directory Structure
A project, let's say `myapp` has the following structure:
`myapp` root directory with the following files:
* `setup.py` - script used by `pip` command to run install the application
* `setup.cfg` - configuration file for `pip`. It contains the dependencies and the version of the application.
* `README.md` - description of the project
* `LICENCE` - the license file
* `tox.ini` - `tox` configuration file

Subdirectories:
* `myapp/myapp` - contains the Python source code and the unit test code. The directory can contain multiple subdirectories. Each directory might have a `tests` directory for the unit tests corresponding to the directory. `tests` directories might have `data` subdirectories containing the test data used in unit tests.

#### Tools
Required Python packages:
- `pytest` - used to run the unit tests
- `flake8` - used to check the conformance with the coding styles. The CADC coding styles are very similar to the default `flake8` styles.
- `tox` - used to set up virtual environments with different configurations and execute tests
- `virtualenv` - (optional) to create a custom virtual environment
- `coverage` - (optional) the coverage Python package is used to measure the code coverage achieved through the unit tests

The code should follow the standard [PEP8 Style Guide for Python Code](https://peps.python.org/pep-0008/). In particular, this includes using only 4 spaces for indentation, and never tabs.

#### Testing
To run all the available configuration:
```commandline
tox
```

To check the available `tox` targets:
```commandline
tox list
```

To run a `tox` target:
```commandline
tox -e py311
```

`tox` targets are created in the `.tox` subdirectory. To activate a specific virtual environment:
```commandline
source .tox/py310/bin/activate
```

Once the virtual environment has been activated, use `pip` to install required software. For ex:
```commandline
pip install -e ".[test]"
```
to install the test environment.

To run the unit tests from a virtual environment:
```commandline
pytest <package_name>
```

#### Continuous Integration/ Continuous Development (CI/CD)
In order for a contribution (PR) to be merged into the project branch, it needs to be reviewed and accepted by at least one of the package maintainers and pass the CI/CD pre-conditions. These are implemented as GH Actions and check the following:
- project `egg` builds successfully
- unit tests are successfully executed in all the supported configurations (Python versions)
- no code style errors are present
- test code coverage does not decrease

CADC staff can also run integration tests. These are not always accessible to external collaborators because they require internal Authentication/Authorization (A&A).

Once a patch has been merged into the default branch it can, depending on the urgency and its content, be published to `PyPI` immediately as an updated version or it can be bundled with other minor changes to be released later. This is at the discretion of the package maintainers.


### Web Browser Application Development Guidelines

TODO

## Image (Container) Repositories

### CADC and CANFAR System Images and Helm Charts

For CADC and CANFAR services, the artefact that is delivered for deployment is a container.  The latest releases of these containers, as well as their accompanying Helm charts (when applicable), are available at the CADC Harbor Image Registry, here:  https://images.opencadc.org.

### Science Platform User/Science Images

Images created by the user community and made available to the CANFAR Science Platform are available at https://images.canfar.net

## Links
* [CADC](https://www.cadc-ccda.hia-iha.nrc-cnrc.gc.ca)
* [OpenCADC Code of Conduct](CODE_OF_CONDUCT.md)
* [OpenCADC License](LICENSE)
* [CANFAR](https://www.canfar.net)
* [CANFAR User Documentation](https://www.opencadc.org/science-containers/)
