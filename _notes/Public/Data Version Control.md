---
title : Data Version Control
notetype : feed
date : 14-03-2022
---

### Data Versioning

[Version control is an important component when working with Machine Learning](https://censius.ai/blogs/version-control-importance). It also [increase the speed of development and reduce mistakes](https://lakefs.io/data-versioning/)

- Increase the speed of development
	- Reproduciblity
	- Data Sharing
	- Change Comparison
- Reduce errors
	- [Data Provenance](https://ardc.edu.au/resources/working-with-data/data-provenance/) - How the data derived
	- Revert to the correct version, when you accidentally change something
	- Debugging

### Tools

There several ways to implement data versioning ranging from full duplication, to space-efficience approaches, to more advance tools ([# Best 7 Data Version Control Tools - Neptune Blog](https://neptune.ai/blog/best-data-version-control-tools), [# Comparing Data Version Control Tools - DagsHub](https://dagshub.com/blog/data-version-control-tools/), [# Top 14 Data Versioning Tools - StartupStash](https://startupstash.com/data-versioning-tools/))

##### Example data tools comparison from DagsHub

![Example data tools comparison from DagsHub](https://dagshub.com/blog/content/images/size/w1000/2020/11/Screen-Shot-2020-11-01-at-20.03.51.png)

One of them is [DVC](https://dvc.org/) which is open-source, lightweight, storage-agnostic, and Git-compatible.


---

## DVC

### What is DVC?
As mention in [their website](https://dvc.org/). DVC is an open-source version control system for Machine Learning Projects which is Git-compatible, Storage agnostic, Lightweight, and [others](https://dvc.org/features).

### When to use DVC?

Refer to [DVC Use Cases](https://dvc.org/doc/use-cases)


### How?

Refer to [DVC Documentation](https://dvc.org/doc/start) which is very clear and easy to follow.

Personally, I'll split the How section into 3 main parts.

- **Data Version Control** - Including the concepts when dealing with data, versioning data with DVC, sharing data across person, or projects, and Data Registries
- **Machine Learning Pipeline** - Connect ML steps with `dvc stage`, reproduce pipeline with dvc repro, compare versioning with `dvc params, or dvc metrics`, and visualize (plot) the time-series data with `dvc plots`
- **Experimentation** - with DVC 2.0, we can easily track experiments, compare, checkout, apply, and also sharing experiments using `dvc exp`

#### 1. Data Version Control

#### Commands
- [`dvc init`](https://dvc.org/doc/command-reference/init)
- [`dvc add`](https://dvc.org/doc/command-reference/add) 
- [`dvc remove`](https://dvc.org/doc/command-reference/remove)
- [`dvc commit`](https://dvc.org/doc/command-reference/commit)
- [`dvc checkout`](https://dvc.org/doc/command-reference/checkout)
- [`dvc diff`](https://dvc.org/doc/command-reference/diff)
- [`dvc remote`](https://dvc.org/doc/command-reference/remote)
- [`dvc fetch`](https://dvc.org/doc/command-reference/fetch)
- [`dvc push`](https://dvc.org/doc/command-reference/push)
- [`dvc pull`](https://dvc.org/doc/command-reference/pull)
- [`dvc status`](https://dvc.org/doc/command-reference/status)
- [`dvc list`](https://dvc.org/doc/command-reference/list)
- [`dvc get`](https://dvc.org/doc/command-reference/get)
- [`dvc get-url`](https://dvc.org/doc/command-reference/get-url)
- [`dvc import`](https://dvc.org/doc/command-reference/import)
- [`dvc import-url`](https://dvc.org/doc/command-reference/import-url)
- [`dvc update`](https://dvc.org/doc/command-reference/update)


##### Reference or Related
- [Get Started with Data and Model Versioning](https://dvc.org/doc/start/data-and-model-versioning)
- [Get Started with Data and Model Access](https://dvc.org/doc/start/data-and-model-access)
- [Set up a Google Drive DVC Remote](https://dvc.org/doc/user-guide/setup-google-drive-remote)
- [External Dependencies](https://dvc.org/doc/user-guide/external-dependencies)
- [`.dvc` Files](https://dvc.org/doc/user-guide/project-structure/dvc-files)
- [`.dvcignore` Files](https://dvc.org/doc/user-guide/project-structure/dvcignore-files)


#### 2. Machine Learning Pipeline

##### Commands
- [`dvc run`](https://dvc.org/doc/command-reference/run)
- [`dvc stage`](https://dvc.org/doc/command-reference/stage)
- [`dvc dag`](https://dvc.org/doc/command-reference/dag)
- [`dvc repro`](https://dvc.org/doc/command-reference/repro)
- [`dvc destroy`](https://dvc.org/doc/command-reference/destroy)
- [`dvc metrics`](https://dvc.org/doc/command-reference/metrics)
- [`dvc params`](https://dvc.org/doc/command-reference/params)
- [`dvc plots`](https://dvc.org/doc/command-reference/plots)



##### Reference or Related

- [Get Started with Data Pipelines](https://dvc.org/doc/start/data-pipelines)
- [Get Started with Metrics, Parameters, and Plots](https://dvc.org/doc/start/metrics-parameters-plots)
- [Pipeline Files (`dvc.yaml`)](https://dvc.org/doc/user-guide/project-structure/pipelines-files)
- [How to Add Dependencie or Outputs](https://dvc.org/doc/user-guide/how-to/add-deps-or-outs-to-a-stage)


#### 3. Experimentation

##### Commands
- [`dvc exp`](https://dvc.org/doc/command-reference/exp)

##### Reference or Related

- [Get Started with Experiment](https://dvc.org/doc/start/experiments)
- [Experiment Management](https://dvc.org/doc/user-guide/experiment-management)
- [Machine Learning Experiment Tracking](https://dvc.org/doc/use-cases/experiment-tracking)


---

### Interesting Resources
- [Data Versioning and Reproducible ML with DVC and MLflow](https://www.youtube.com/watch?v=W2DvpCYw22o&ab_channel=Databricks) shares how to use both tools to gether, so we can track data using DVC and track experiment using MLflow
- [Reproducible Machine Learning & Experiment Tracking Pipeline with Python and DVC](https://www.youtube.com/watch?v=6_kK6wRtzhk&ab_channel=VenelinValkov) shares a step by step on how to use DVC pipeline by using Kaggle dataset (Note starting around [28:20](https://youtu.be/6_kK6wRtzhk?t=1700))
- [Experience report: Data Version Control (DVC) for Machine Learning Projects](https://medium.com/gocardless-tech/experience-report-data-version-control-dvc-for-machine-learning-projects-29c09b195e) shares pros and cons when using DVC with their workflow. Interestingly, they also create their own tools (e.g.,  paired with `pre-commit`), and also use DVC to versioning entire Jupyter Notebook.