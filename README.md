# packse

Python packaging scenarios.

## Installation

Only a local installation is supported at this time:

```bash
poetry install
```
Once installed, the `packse` command-line interface will be available.

Depending on your Poetry configuration, you may need to use `poetry run packse` instead or activate Poetry's 
virtual environment.

## Usage

### Scenarios

A scenario is a JSON description of a dependency tree.

See [`scenarios/example.json`](./scenarios/example.json)

### Building scenarios

A scenario can be used to generate packages and build distributions:

```bash
packse build scenario/example.json
```

The `build/` directory will contain sources for all of the packages in the scenario.
The `dist/` directory will contain built distributions for all of the packages in the scenario.

When a scenario is built, it is given a unique identifier based on a hash of the scenario contents and the project
templates used to generate the packages. Each package in the scenario will include the unique identifier.

### Viewing scenarios

**Not yet implemented**

The dependency tree of a scenario can be previewed using the `view` command:

```
$ packse view scenarios/example.json
example-9e723676
└── a-1.0.0
    └── requires b>=1.0.0
        └── satisfied by b-1.0.0
└── b-1.0.0
```

### Publishing scenarios

Built scenarios can be published to a Python Package Index.

For example, to upload to the test PyPI:

```bash
twine upload -r testpypi dist/<scenario>/*
```

### Testing scenarios

Published scenarios can then be tested with your choice of package manager.

For example, with `pip`:

```bash
pip install -i https://test.pypi.org/simple/ <scenario>-<package>==1.0.0
```

### Writing new scenarios

**Not yet written**