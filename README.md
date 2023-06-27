# Utilities and Implementations for Glue Jobs
Here we host code and artifacts for AWS Glue Jobs. The main idea is that Glue Jobs allow to include [python wheels](https://pythonwheels.com/) as external libraries. In this repository we host all external libraries needed for the implementation of glue jobs on the datalake.

# Add Your Own Library
All python projects are built with [pdm](https://pdm.fming.dev/latest/) which is a python dependency manager. (in principle any dependency manager compatible with ~pyproject.toml~ should work, such as [poetry](https://python-poetry.org/). In the ~template~ folder you can find a project template easily customizable to your needs.
