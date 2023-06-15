

<h1><img src="docs/assets/favicon.png" alt="Logo" width="40" height="40" align="left">Rigatoni</h1>


![Build Status](https://github.com/InsightCenterNoodles/Rigatoni/workflows/CI/badge.svg)
![PyPI](https://img.shields.io/pypi/v/Rigatoni)
[![Coverage badge](https://raw.githubusercontent.com/InsightCenterNoodles/Rigatoni/python-coverage-comment-action-data/badge.svg)](https://htmlpreview.github.io/?https://github.com/InsightCenterNoodles/Rigatoni/blob/python-coverage-comment-action-data/htmlcov/index.html)


Python Server Library for NOODLES Protocol

## Description
This server library implements the NOODLES messaging protocol and provides objects for maintaining a scene in state. 
The server uses a websocket connection to send CBOR encoded messages. To customize its implementation, the library 
provides convenient interface methods to assist the user in writing their own methods for the server. The user can
also add custom delegates to add additional functionality to any of the standard components.

## Documentation

For more information and documentation, check out [the documentation](https://insightcenternoodles.github.io/Rigatoni/).

## Installation

Installation is as simple as:

```bash
pip install rigatoni
```

For optional dependencies and support for meshes and geometry object creation, you can install

```bash
pip install rigatoni[geometry]
```

## Simple Example

```python
import rigatoni as rig

class CustomTable(rig.Table):

    extra_info = None

    def handle_clear(self):
        print("Clearing table")

def basic_method(server, context):
    print("Hello World!")

starting_state = [
    rig.StartingComponent(rig.Method, {"name": "basic_method", "arg_doc": []}, basic_method),
]

delegates = {
    rig.Table: CustomTable
}

with rig.Server(50000, starting_state) as server:
    # do stuff
    pass
```

## Hungry for more NOODLES?
For more information and other related repositories check out [this repository](https://github.com/InsightCenterNoodles)
