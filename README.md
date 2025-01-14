# mesonpy (meson-python) [![PyPI version](https://badge.fury.io/py/meson-python.svg)](https://pypi.org/project/meson-python/)

[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/FFY00/mesonpy/main.svg)](https://results.pre-commit.ci/latest/github/FFY00/mesonpy/main)
[![checks](https://github.com/FFY00/mesonpy/actions/workflows/checks.yml/badge.svg)](https://github.com/FFY00/mesonpy/actions/workflows/checks.yml)
[![tests](https://github.com/FFY00/mesonpy/actions/workflows/tests.yml/badge.svg)](https://github.com/FFY00/mesonpy/actions/workflows/tests.yml)
[![codecov](https://codecov.io/gh/FFY00/mesonpy/branch/main/graph/badge.svg?token=xcb2u2YvVk)](https://codecov.io/gh/FFY00/mesonpy)
[![Documentation Status](https://readthedocs.org/projects/meson-python/badge/?version=latest)](https://meson-python.readthedocs.io/en/latest/?badge=latest)

Python build backend ([PEP 517](https://www.python.org/dev/peps/pep-0517/)) for Meson projects.

See the [documentation](https://meson-python.readthedocs.io/en/stable/) for more details.

### Status

- Pure Python modules :+1:
- Native modules
  - Don't link against anything :+1:
  - Link aginst external libraries :+1:
  - Link aginst libraries from the Meson project :+1:
  - Detect the ABI :+1:
- Scripts (executables in Meson)
  - Don't link aginst anything :+1:
  - Link against external libraries :+1:
  - Link against libraries from the Meson project :hammer:

#### Platform Support

- Linux :+1:
- Windows :soon:
- MacOS :soon:
- Other UNIX-like :warning:
  - Most platforms should work, but currently that is not tested or guaranteed
