### Description

This module contains scripts for downloading repositories from GitHub and cleaning duplicated repositories.

### Usage

#### 1. Download list of repositories

You can use the resource [seart-ghs.si.usi.ch]( https://seart-ghs.si.usi.ch/) for this purpose.
The file has to be in the CSV format with the ```name``` column,
containing repositories' names in the following format: ```username/project_name```

#### 2. Clean duplicated repositories (optional stage)

Run the script for cleaning all duplicated repositories with different names:
``` shell script
python3 scripts/data_collection/clean_duplicates.py /path/to/csv_file/results.csv /path/to/cleaned/data/dir
```
You can use the ```--save-metadata``` flag to download the metadata about all projects. 
Metadata includes information about repository's full name, owner, etc.
This script makes requests to GitHub API, so you should add your GitHub Token to environment variables 
(variable name is ```GITHUB_TOKEN```).

#### 3. Load dataset

Run the following command to download the dataset:

``` 
python3 scripts/data_collection/load_dataset.py /path/to/cleaned/data/dir/results.csv /path/to/dataset/dir --allowed-extensions kt
```
The optional argument ```--allowed-extensions``` accepts a list of extensions. 
Only files with these extensions will be saved (without this argument all files will be saved).
