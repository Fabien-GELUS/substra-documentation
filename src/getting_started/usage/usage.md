# Usage

![Substra](../../../_static/substra-logo.svg)

CLI and SDK for interacting with Substra platform.

- [Usage](#usage)
  - [Install](#install)
  - [Running the Substra platform locally](#running-the-substra-platform-locally)
  - [Usage](#usage-1)
    - [CLI](#cli)
    - [SDK](#sdk)
  - [Documentation](#documentation)
  - [Examples](#examples)
  - [Compatibility table](#compatibility-table)
    - [Adding entries to the compatibility table](#adding-entries-to-the-compatibility-table)
  - [Contributing](#contributing)
    - [Setup](#setup)
    - [Documentation](#documentation-1)
    - [Deploy](#deploy)

## Install

To install the command line interface and the python sdk, run the following command:

```sh
pip install substra
```

To enable Bash completion, you need to put into your .bashrc:

```sh
eval "$(_SUBSTRA_COMPLETE=source substra)"
```

For zsh users add this to your .zshrc:

```sh
eval "$(_SUBSTRA_COMPLETE=source_zsh substra)"
```

From this point onwards, substra command line interface will have autocompletion enabled.

## Running the Substra platform locally

You can run the Substra platform locally on your machine using one of the two following methods:

- [Using kubernetes and skaffold (recommended)](../installation/local_install_skaffold.md)
- [Using docker-compose](../installation/local_install_docker_compose.md)

## Usage

Credentials are required for using this tool.

### CLI

```sh
substra --help
```

### SDK

```python
import substra

client = substra.Client()
# enjoy...
```

## Documentation

Interacting with the Substra platform:

- [Command line interface](https://github.com/SubstraFoundation/substra/blob/master/references/cli.md#summary)
- [SDK](https://github.com/SubstraFoundation/substra/blob/master/references/sdk.md#substrasdk)

Implementing your assets in python:

- [Objective base class](https://github.com/SubstraFoundation/substra-tools/blob/master/docs/api.md#metrics)
- [Dataset base class](https://github.com/SubstraFoundation/substra-tools/blob/master/docs/api.md#opener)
- [Algo base class](https://github.com/SubstraFoundation/substra-tools/blob/master/docs/api.md#algo)
- [Composite algo base class](https://github.com/SubstraFoundation/substra-tools/blob/master/docs/api.md#compositealgo)
- [Aggregate algo base class](https://github.com/SubstraFoundation/substra-tools/blob/master/docs/api.md#aggregatealgo)

Learning about the Substra platform:

- [Concepts](https://github.com/SubstraFoundation/substra/blob/master/docs/concepts.md#substras-concepts)
- [Machine Learning tasks](https://github.com/SubstraFoundation/substra/blob/master/docs/ml_tasks.md#machine-learning-tasks)
- [Adding a full pipeline](https://github.com/SubstraFoundation/substra/blob/master/docs/full_pipeline_workflow.md#adding-a-full-pipeline)
- [Adding data samples](https://github.com/SubstraFoundation/substra/blob/master/docs/add_data_samples.md#add-data-samples-to-substra)

## Examples

- [Titanic](https://github.com/SubstraFoundation/substra/blob/master/examples/titanic/README.md#titanic)
- [Cross-validation](https://github.com/SubstraFoundation/substra/blob/master/examples/cross_val/README.md#cross-validation)
- [Compute plan](https://github.com/SubstraFoundation/substra/blob/master/examples/compute_plan/README.md#compute-plan)

## Compatibility table

These sets of versions have been tested for compatilibility:

| substra  | substra-chaincode  | substra-backend  | substra-tests  | hlf-k8s | substra-frontend |
|---|---|---|---|---|---|
| [`0.4.0-alpha.3`](https://github.com/SubstraFoundation/substra/releases/tag/0.4.0-alpha.3) | [`0.0.8-alpha.6`](https://github.com/SubstraFoundation/substra-chaincode/releases/tag/0.0.8-alpha.6) | [`0.0.12-alpha.13`](https://github.com/SubstraFoundation/substra-backend/releases/tag/0.0.12-alpha.13) | [`0.2.0-alpha.1`](https://github.com/SubstraFoundation/substra-tests/releases/tag/0.2.0-alpha.1) | [`0.0.11-alpha.1`](https://github.com/SubstraFoundation/hlf-k8s/releases/tag/0.0.11-alpha.1) | |
| [`0.4.0-alpha.4`](https://github.com/SubstraFoundation/substra/releases/tag/0.4.0-alpha.4) | [`0.0.8-alpha.9`](https://github.com/SubstraFoundation/substra-chaincode/releases/tag/0.0.8-alpha.9) | [`0.0.12-alpha.20`](https://github.com/SubstraFoundation/substra-backend/releases/tag/0.0.12-alpha.20) | [`0.2.0-alpha.2`](https://github.com/SubstraFoundation/substra-tests/releases/tag/0.2.0-alpha.2) | [`0.0.11-alpha.1`](https://github.com/SubstraFoundation/hlf-k8s/releases/tag/0.0.11-alpha.1) | |

### Adding entries to the compatibility table

- Please ensure that all the tests from [`substra-tests`](https://github.com/SubstraFoundation/substra-tests/) pass

```sh
cd substra-tests
make test
```

## Contributing

### Setup

To setup the project in development mode, run:

```sh
pip install -e .[test]
```

To run all tests, use the following command:

```sh
python setup.py test
```

### Documentation

To generate the command line interface documentation, run the following command:

```sh
python bin/generate_cli_documentation.py
```

Use the following command to generate the python sdk documentation:

```sh
pydocmd simple substra.sdk+ substra.sdk.Client+ > references/sdk.md
```

Documentation will be available in *docs/* directory.

### Deploy

Deployment to pypi.org should be automatic thanks to Travis but if you need to do it manually, here is what you need to do:

```sh
rm -rf dist/*
python3 setup.py sdist bdist_wheel
twine upload dist/* --verbose
```
