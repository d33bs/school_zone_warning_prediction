# School Zone Warning Prediction

## Goal

Predict school zone road warning signage using location, map, and street-level data. Created as part of a volunteer AI challenge: _Omdena + iRAP: Preventing Road Crashes and Saving Lives_ ([https://omdena.com/projects/ai-road-safety/](https://omdena.com/projects/ai-road-safety/))

## Background 

The International Road Assessment Programme (iRAP) is a registered charity established to help tackle the devastating social and economic cost of road crashes. The charity’s vision is for a world free of high-risk roads. In this project, 50 technology changemakers are building AI based solutions to map the crash risk on roads. Together we can save thousands of lives every year.

My role in this project as a Lead Machine Learning Engineer has involved contributions towards data pipelines, image recognition models, and collaborative team guidance. Using iRAP's road score attributes as a basis, one specific focus area included the work found within this repo towards a pipeline which finds school road locations, gathers street-level  images using those road locations, and assesses the probability of school-zone warning signage existence from those images.

iRAP uses various attributes with specific data codes to determine a 5-star rating for segments of road. Segments with fewer stars are more dangerous and often results in greater human injury. The work in this repo is intended to help automate the coding of one 5-star attribute that deals with the presence of a school zone and school zone warning signage or lights. For more details, see the following page for a reference of the coding specification (found under "iRAP Coding Manual") with the label "School Zone Warning": [https://www.irap.org/specifications/](https://www.irap.org/specifications/)

## Organization

- __./analysis__ <br> Includes analysis-style notebooks used to gather details, find the shape of data, perform tests with existing libraries, etc.
- __./pipeline__ <br> Includes notebooks intended to be used in automated workflow sequence in Prefect while still retaining notebook-form via Papermill implementation. "pipeline_schoolroads.ipynb" includes the workflow itself, while the other notebooks represent tasks found within that workflow. 

## Technologies

Technology used in the pipeline includes (but is not limited to) the following:

### Prefect
The Prefect Python library is "An open-source workflow management system." (https://www.prefect.io/core). In the context of Prefect, we are able to create "tasks" (may be understood to be Python functions) that are coordinated in a "flow". A flow which consists of these coordinated tasks is also considered a directed acyclic graph (DAG) (https://en.wikipedia.org/wiki/Directed_acyclic_graph).

Prefect provides the capability to run individual flows as well as a host platform by which many flows may be coordinated and viewed through a web dashboard. Tasks and flows are distinguished as "Prefect Core" (https://docs.prefect.io/core/) whereas platform components are organized under the label "Prefect Orchestration" (https://docs.prefect.io/orchestration/).

The pipeline included in this repo uses Jupyter notebooks executed with parameters via Papermill as Prefect tasks in a coordinated flow. Using notebooks in this manner allows for flexible development or experimentation as well as a production-ready workflow to deliver results at scale. The intent is to allow for less clunky or manual process translation from data analysis to data engineering.

### Papermill
"Papermill is a tool for parameterizing and executing Jupyter Notebooks." (https://papermill.readthedocs.io/en/latest/index.html). Using Papermill we are able to use notebooks as dynamic functions or programs in and of themselves. This helps data-orientated development (which often may take place in a notebook) remain flexible to development or experimentation while also enabling automation efforts via pipelining tools. Parameters may be added (and are not required) for existing notebooks in order to gain flexibility in their execution (https://papermill.readthedocs.io/en/latest/usage-parameterize.html).
        