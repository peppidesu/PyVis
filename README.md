# PyVis

PyVis is a 2D graphics API that mimics the Processing API.

## Installation

1. Download the repository as a .zip file.
2. Copy and paste __all__ files into your project folder
3. Make sure you've got all of the required pip packages:
    * pygame
    * colorama

## How to use

### Main script setup

First of all, you need to import the `pyvis.py` file:

```Python
    import pyvis
```

Note: since all functions for drawing are part of the pyvis namespace, you might
want to use `import pyvis as pv` instead.

After that, you can initialize PyVis by calling the 'init()' method:

```Python
    pyvis.init()
```

The nice thing about PyVis is that the update loop is already setup for you.
The only thing you need to do is add your functions to the update loop by adding them
to a _function pool_.

_Function pools_ are lists of functions that get called
at a certain point in the kernel loop. For example, the _"draw"-pool_ gets called
every frame, whilst the _"setup"-pool_ only gets called at the start of the program.

You can add functions to a function pool as follows:

```Python
@pyvis.kernel.pool("draw", 1)
def yourFunction():
    # Do something

```

The number after the name of the draw pool indicates the priority of that function in the pool.
Functions with a higher priority will be executed before others.

To start the kernel loop, add this line at the end of your main script:

```Python
pyvis.kernel.run()
```

Your final script should look like this:

```Python
import pyvis as pv

pv.init()

@pv.kernel.pool("setup",1)
def onSetup():
    # do something

@pv.kernel.pool("draw",1)
def onDraw():
    # do something

pv.kernel.run()
```

All functionality is included in the example, and you can use it as a reference to create your
own application.

## PyVis 0.1.5a

### Changelog

- Further improvements in kernel loop
- Added splash screen
- Expanded functionality in fps monitoring.
- Improved and added log messages.
- Command line colors! :D

## PyVis 0.1.3a

### Changelog

- Improved kernel loop performance
- Fullscreen now works properly

---
