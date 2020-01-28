# VRE Sample Tool

A simple example tool that is ready to run a workflow

## Requirements
- Python 3.6.9+
- Python3-dev and Python3-venv
- Docker: https://docs.docker.com/get-docker/
- Python Modules:
  - pylint
  - pytest
  - mg-tool-api: https://github.com/Multiscale-Genomics/mg-tool-api.git
  - cwltool: https://github.com/common-workflow-language/cwltool.git

## Installation

Directly from GitHub:

```
cd ${HOME}/user

git clone https://github.com/inab/vre_sample_tool.git

cd vre_sample_tool
```

Create the Python environment

```
python3 -m venv ${HOME}/user/vre_sample_tool/venv
source venv/bin/activate
pip install -r requirements.txt
```

## Configure

Add your ${USER} in `/tests/basic/config.json`:

```json 
"arguments": [
  {
      "name": "execution",
      "value": "/home/${USER}/vre_sample_tool/tests/basic/run000"
  }
],
"output_files": [
  {
      "name": "bam_file",
      "required": true,
      "allow_multiple": false,
      "file": {
          "file_path": "/home/${USER}/vre_sample_tool/tests/basic/run000/A.bam"
      }
   }
]
```
and `/tests/basic/in_metadata.json`:

```json 
{
    "_id": "unique_file_id_5e14abe0a37012.29503907",
    "file_path": "/home/${USER}/vre_sample_tool/tests/basic/NA12878.bam"
},
{
    "_id": "unique_file_id_5e14abe0a37012.29503908",
    "file_path": "/home/${USER}/vre_sample_tool/tests/basic/hg38.fa"
{
``` 
and `/test/basic/input_basic_example.yml`:

```yaml 
  input_reads: 
    class: File
    location: /home/{USER}/vre_sample_tool/tests/basic/NA12878.bam
  biospecimen_name: "hg38"
  output_basename: "mytest"
  indexed_reference_fasta:
    class: File 
    location: /home/{USER}/vre_sample_tool/tests/basic/hg38.fa
```
