# Goethermal boreholes in parallel with updated configuration
This repository contains a TRNSYS component for simulating geothermal borehole fields connected in parallel and installed in two separate phases. The boreholes may have different lengths and can be positioned at arbitrary locations within the field. 

The component is implemented in Python as a [Type 3157](https://trnsys.de/static/77828438acd0697c30be234f0f248eff/Calling-Python-from-TRNSYS-with-CFFI.pdf). It relies on the [BoreholeNetoworksSimulator](https://github.com/marcbasquensmunoz/BoreholeNetworksSimulator.jl) library for modeling thermal interactions within the borefield. 

To use this component, you must have the following installed:

- TRNSYS 18
- Python 3.10

The simulation time step and total simulation duration are configured in the usual way for TRNSYS simulations — by adjusting the settings in the .tpf file.

An Excel interface, provided in the file "GeoInput.xlsx", allows users to easily modify borehole properties, ground parameters, and circulation fluid characteristics.



