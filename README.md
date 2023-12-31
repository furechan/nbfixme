# Utility to fix basic notebook validation errors

This project offers a command line tool to fix jupyter notebook files that have some type of validation errors.
These errors may happen when editing a notebook in non standard jupyter clients like PyCharm or other editors
and they can stop the notebook from being properly processed or displayed in github for example.

Currently the script only deals with one type of error that appears as
`NotebookValidationError: 'execution_count' is a required property`.
This error usually happens when a notebook is saved and its last cell has not been executed.
As a fix the script will add a key `execution_count` with a value of `null` to the cell data
if the key is not already present.

By default the script will change the files in place when there is a fix, but you can specify an OUTDIR
parameter if you prefer to save output files in a different directory.

## Usage

```console
Usage: nbfixme [OPTIONS] [PATH]...

  Utility to fix basic notebook validation errors

  PATH is the path to a notebook file or a
  directory containing *.ipynb files.

  By default the script will change the files in
  place when there is a fix, but you can specify
  an OUTDIR parameter if you prefer to save output
  files in a different directory.

Options:
  -o, --outdir OUTDIR  Save output in directory.
  -c, --check-only     Only check for errors.
  -r, --recurse        Recurse to sub directories.
```

## Example

```console
❯ nbfixme extras -o output
extras/notebook-valid.ipynb ok
extras/notebook-broken.ipynb error
extras/notebook-tofix.ipynb fixed
```

## Installation

You can install the latest version of this module with `pip` or `pipx`

```console
pip install git+ssh://git@github.com/furechan/nbfixme.git
```

## Related Resources
-[The Jupyter Notebook Format](https://nbformat.readthedocs.io/en/latest/)
