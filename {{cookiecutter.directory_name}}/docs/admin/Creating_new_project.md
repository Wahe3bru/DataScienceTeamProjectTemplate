## Creating a new project

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
$ cookiecutter https://github.com/Wahe3bru/project_template.git
```

### Initializing project template
You will have to answer a few prompted questions.<br> Some will have acceptable defaults (press `enter` to keep the default) but most will be answered by you about the project.

##### Questions to be answered:
__project_name__: default="test_project", <br>
__directory_name__: will default to the project name provided,  <br>
__project_code__: default="LSA-DS-{project_name}",  <br>
__description__: "Enter a short description of the project.",  <br>
__project_lead__: default="Waheeb Agherdien",  <br>
__lead_email__: default="Waheeb.Agherdien@za.Logicalis.com"  <br>
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

__data folder__ <br>
Data is typically not saved in version control but the scripts used to acquire, manipulate and store data are.

_00-raw_: The raw (unmodified) data should be stored here. This data is immutable so that when scripts are run we get the same out come i.e. reproducibility.

_01-interim_: The intermediate phase of data should be  kept here ie copy of raw data being processed - cleaning, feature engineering, combining with other sources.

_02-processed_: The finalized data - data used to train the model is stored here.

__docs__<br>
_admin_: <br>
All administrative documentation data to placed here. This would vary depending on the project but could contain contact details of the various project holders, customer IT liaison, NDA's etc.  

_project_documentation_:<br>

_reference_material_:<br>
All documentation, links and other supporting material that assisted team members throughout the project should be placed here. It can assist later team members get up to speed, or as reminders when the project gets picked months later.

_reports_:<br>
All generated reports, both internal and published, should be placed here sorted by date. The most up-to-date report should always be here.

__notebooks__<br>
All notebooks should be numbered sequentially followed by team members initials and a succinct title eg. `01-WA-EDA.ipynb`, `02-TK-ExploringMissingData.ipynb`


### Workflow
access functions written in .py scripts stored in src folder.
```
In [1]: %load_ext autoreload

In [2]: %autoreload 2

In [3]: from foo import some_function

In [4]: some_function()
Out[4]: 42

In [5]: # open foo.py in an editor and change some_function to return 43

In [6]: some_function()
Out[6]: 43
```

##### Rationale
All EDA would be performed using Jupyter Lab/notebook. Eventually the functions created would be refactored
and stored in `.py` scripts stored in `src` folder for both reusability, be used when put in production, testing and most importantly reproducibility.
So All data wrangling methods would be put in `/src/data.py` and all plotting methods in `/src/visualization.py`. This would enable members to work on different aspects of the project and be assured that the graphs created from methods from the `visualization.py` would be the right format and can be reproduced using the latest data (eg. for a representation).

reproducibility is key. All manual implementation should be documented in the steps taken in both the notebooks and in the project documentation. Project documentation should be generated using a tool like `Sphinx` to minimize overhead and once automated ensures documentation is updated. 
