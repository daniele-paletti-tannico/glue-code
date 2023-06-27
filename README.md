# Utilities and Implementations for Glue Jobs
Here we host code and artifacts for AWS Glue Jobs. The main idea is that Glue Jobs allow to include [python wheels](https://pythonwheels.com/) as external libraries. In this repository we host all external libraries needed for the implementation of glue jobs on the datalake.

# Add Your Own Library
All python projects are built with [pdm](https://pdm.fming.dev/latest/) which eases the python build process (in principle any dependency manager compatible with `pyproject.toml` should work, such as [poetry](https://python-poetry.org/)). 

In the `template_glue3` folder you can find a project template easily customizable to your needs.

How to create your own library:
1. [Install pdm](https://pdm.fming.dev/latest/#installation)
2. Copy the `template_glue3` folder:
   ```bash
   cp template_glue3 <project_name>
   ```
3. Inside the newly created `<project_name>` folder
   ```bash
   cd <project_name>
   ```
   Customize the `pyproject.toml` by changing:
   - project name to <project_name>
   - author name and author email
   - change the name of the project_name folder to <project_name>

   You will also find a `README.md` file which you need to update with relevant information for your library.
   
   The newly renamed <project_name> folder is the root of your source code, the `__init__.py` signals to the build system that such folder
   must be handled as a python module.
   
5. Write your python files
6. Build with pdm:
  ```bash
  pdm build
  ```
  Now you can find your newly built wheel inside the `dist` folder which will be created alongside your `pyproject.toml`.

# Use a Wheel on AWS Glue
First the wheel must be uploaded to S3.

Then:
- **Notebook**: you can use `%additional_python_modules` magic command to add (comma separated) external wheels.
- **Job**: you can set external python library in the job details (in the advanced option).


