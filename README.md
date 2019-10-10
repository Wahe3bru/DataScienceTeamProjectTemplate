# DataScienceTeamProjectTemplate
a cookiecutter project structure template
This template is used to standarise the project structure of the data science team to ensure reproducibility, consistency and a systematic workflow that could assist newer team members get up and running as soon as possible.
This structure was designed with a smaller team in mind working on small to medium size projects. The template is a guide to a consistant structure that is only minimally modified to mold to unique projects.

### Getting started
##### _requirements:_
- cookiecutter
- LSA_DS_project_template

__install cookiecutter__

`pip install cookiecutter`

__get template__

either copy LSA_DS_project_template.zip file to local pc or copy path to template
- template location: <shared folder>
- github path: https://github.com/Wahe3bru/DSprojectTemplate.git 

__installation__

open terminal / command prompt <br>
change to your projects directory, then run cookiecutter followed by the path to template.

```bash
$ cd work/projects
$ cookiecutter path/to/LSA_DS_project_template.zip
# or using github url
$ cookiecutter https://github.com/Wahe3bru/DSprojectTemplate.git 
```

### Initializing project template
You will have to answer a few prompted questions.<br> Some will have acceptable defaults (press `enter` to keep the default) but most will be answered by you about the project.

##### Questions to be answered:
__project_name__: default="test_project", <br>
__directory_name__: will default to the project name provided,  <br>
__project_code__: default="LSA-DS-{project_name}",  <br>
__description__: "Enter a short description of the project.",  <br>
__project_lead__: default="Waheeb Agherdien",  <br>
__lead_email__: default="Waheeb.Agherdien@gmail.com"  <br>
<br>

##### Project structure
```bash
├───data
│   ├───00-raw
│   ├───01-interim
│   └───02-processed
├───docs
│   ├───admin
│   │   └───Contact_info.docx
│   ├───project_documentation
│   │   └───Team-DoL.docx
│   ├───reference_material
│   │   └───Data-dictionary.txt
│   └───reports
│   │   └───initial_findings.ppt
├───notebooks
│   ├───01-WA-EDA.ipynb
│   ├───02-TC-EDA.ipynb
│   └───03-WA-process_features.ipynb
└───src
│   ├───01-TC-get_data.py
│   └───02-WA-process_data.ipynb
└───Readme.md
```
