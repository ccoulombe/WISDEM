# WISDEM&reg;

[![Build Status](https://travis-ci.com/WISDEM/WISDEM.svg?branch=develop)](https://travis-ci.com/WISDEM/WISDEM)
[![Coverage Status](https://coveralls.io/repos/github/WISDEM/WISDEM/badge.svg?branch=develop)](https://coveralls.io/github/WISDEM/WISDEM?branch=develop)
[![Documentation Status](https://readthedocs.org/projects/wisdem/badge/?version=latest)](https://wisdem.readthedocs.io/en/latest/?badge=latest)


The Wind-Plant Integrated System Design and Engineering Model (WISDEM&reg;) is a set of models for assessing overall wind plant cost of energy (COE).
The models use wind turbine and plant cost and energy production as well as financial models to estimate COE and other wind plant system attributes.
WISDEM&reg; is accessed through Python, is built using [OpenMDAO](https://openmdao.org/), and uses several sub-models that are also implemented within OpenMDAO.
These sub-models can be used independently but they are required to use the overall WISDEM&reg; turbine design capability.
Please install all of the pre-requisites prior to installing WISDEM&reg; by following the directions below.
For additional information about the NWTC effort in systems engineering that supports WISDEM&reg; development, please visit the official [NREL systems engineering for wind energy website](https://www.nrel.gov/wind/systems-engineering.html).

Author: [NREL WISDEM Team](mailto:systems.engineering@nrel.gov) 


## Version

This software is a version 2.0.1.

## Documentation

See local documentation in the `docs`-directory or access the online version at <https://wisdem.readthedocs.io/en/latest/>

## Packages

WISDEM&reg; is a family of modules.  The core modules are:

* _AeroelasticSE_ provides multi-fidelity capability for rotor analysis by calling [OpenFAST](https://github.com/OpenFAST/openfast)
* _CommonSE_ includes several libraries shared among modules
* _DrivetrainSE_ sizes the drivetrain and generator systems (formerly DriveSE and GeneratorSE)
* _FloatingSE_ works with the floating platforms
* _OffshoreBOS_ sizes the balance of systems for offshore plants
* _Plant_FinanceSE_ runs the financial analysis of a wind plant
* _RotorSE_ is a tool for rotor design
* _TowerSE_ is a tool for tower (and monopile) design
* _Turbine_CostsSE_ is a turbine cost model
* _NREL CSM_ is the old cost-and-scaling model
* _WISDEM_ provides the interface between models

The core modules draw upon some utility packages, which are typically compiled code with python wrappers:

* _Airfoil Preppy_ is a tool to handle airfoil polar data
* _CCBlade_ is the BEM module of WISDEM
* _pBEAM_ provides a basic beam model
* _pyFrame3DD_ brings libraries to handle various coordinate transformations
* _pyMAP_ provides a python interface to MAP++, a quasi-static mooring line model
* _pyoptsparse_ provides some additional optimization algorithms to OpenMDAO


## Installation

Installation with [Anaconda](https://www.anaconda.com) is the recommended approach because of the ability to create self-contained environments suitable for testing and analysis.  WISDEM&reg; requires [Anaconda 64-bit](https://www.anaconda.com/distribution/).

The installation instructions below use the environment name, "wisdem-env," but any name is acceptable.

1.  Setup and activate the Anaconda environment from a prompt (Anaconda3 Power Shell on Windows or Terminal.app on Mac)

        conda config --add channels conda-forge
        conda create -y --name wisdem-env python=3.7
        conda activate wisdem-env
    
    Note that to use WISDEM again after installation is complete, you will always need to activate the conda environment first with `conda activate wisdem-env`

2.  Use conda to install the build dependencies, but then install WISDEM from source.  Not the differences between Windows and Mac/Linux build systems

        conda install -y wisdem git jupyter
        conda remove --force wisdem
        conda install compilers     # (Mac / Linux only)
        conda install m2w64-toolchain libpython       # (Windows only)
        git clone https://github.com/WISDEM/WISDEM.git
        cd WISDEM
        git checkout develop
        python setup.py develop


3. OPTIONAL: Install pyOptSparse, a package that provides a handful of additional optimization solvers and has OpenMDAO support:

        git clone https://github.com/evan-gaertner/pyoptsparse.git
        cd pyoptsparse
        python setup.py install
        cd ..


## Run Unit Tests

Each package has its own set of unit tests, some of which are more comprehensive than others.

## Feedback

For software issues please use <https://github.com/WISDEM/WISDEM/issues>.  For functionality and theory related questions and comments please use the NWTC forum for [Systems Engineering Software Questions](https://wind.nrel.gov/forum/wind/viewtopic.php?f=34&t=1002).
