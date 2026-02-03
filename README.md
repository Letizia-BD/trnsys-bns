# Goethermal boreholes in parallel with updated configuration
This repository contains a TRNSYS component for simulating geothermal borehole fields connected in parallel and installed in two separate phases. The boreholes may have different lengths and can be positioned at arbitrary locations within the field. 

The component is implemented in Python as a [Type 3157](https://trnsys.de/static/77828438acd0697c30be234f0f248eff/Calling-Python-from-TRNSYS-with-CFFI.pdf). It relies on the [BoreholeNetoworksSimulator](https://github.com/marcbasquensmunoz/BoreholeNetworksSimulator.jl) library for modeling thermal interactions within the borefield. 

To use this component, you must have the following installed:

- TRNSYS 18
- Python 3.10
- Julia 1.11.5

**Input interface**

An Excel interface (`GeoInput.xlsx`) allows users to easily modify borehole properties, ground parameters, and circulating fluid characteristics.

This makes it straightforward to set up and customize your geothermal simulation without modifying the Python code directly.

The simulation time step and total simulation duration are configured as usual in TRNSYS by adjusting the settings in the `.tpf` file.

## Detailed installation
Details about how to configure **Python 3.10** and the **TRNSYS Add-On** are available in the user guide: https://trnsys.de/static/77828438acd0697c30be234f0f248eff/Calling-Python-from-TRNSYS-with-CFFI.pdf

Below is a simplified step-by-step guide.

### 1. Add the TRNSYS Add-On to TRNSYS 18 
1. Go to the [TRNSYS Add-Ons page](https://trnsys.de/en/addons-en) and search for **"Calling Python CFFI Type 3157"**


>These instructions and component are tested on version **v0.6.0 (2022-05-06)** of the add-on.

2. Download the Zip archive containing all the necessary files:
3. Extract the contents of the ZIP archive into your **TRNSYS installation directory**. Default location:

        C:\TRNSYS18

### 2. Install python 3.10
> ⚠️ To follow these instructions you need Python 3.10 exactly. It is ok to have other Python versions installed at the same time.
1. Download the **latest 64-bit Python 3.10** release from [python.org](https://www.python.org)  
2. During the installation, make sure to check the box: 

        Add Python to PATH

If you succesfully installed Python 3.10 and could check the box "Add Python to Path" continue to the section "Install the main Python dependencies". Otherwise, if for some reason the **Add Python to PATH** box did not appear during the installation, add Python to Path manually by doing the following:

I. Find where Python is installed. Possible common locations: 

        C:\Users\<YourUser>\AppData\Local\Programs\Python\Python310\
        C:\Program Files\Python310\
II. Open **Edit Environment Variables** from the Windows Start menu.

III. Add two new Paths (make sure that you use the correct paths, the two paths below are just examples):
        C:\Users\<YourUser>\AppData\Local\Programs\Python\Python310\ and
        C:\Users\<YourUser>\AppData\Local\Programs\Python\Python310\Scripts

### 3. Install the main Python dependencies
1. Open the **Command Prompt** (search "Command Prompt" in Windows)
2. Type the following commands **one at a time**, pressing Enter after each:

        py -3.10 -m pip install numpy 
        py -3.10 -m pip install cffi

If you succesfull installed numpy and cffi continue to section "Download the model from GitHub". Otherwise, **if the two previous commands did not work**, install the numpy and cffi libraries from Python:
I. Open Python 3.10
II. Run the following commands inside Python, pressing enter after each line:

        import sys
        import subprocess
        subprocess.check_call([sys.executable, "-m", "pip", "install", "numpy"])
        subprocess.check_call([sys.executable, "-m", "pip", "install", "cffi"])

### 3. Install Julia

1. Download the **Julia 1.11.5** release from [julialang.org]([https://www.python.org](https://julialang.org/downloads/oldreleases/))
   ⚠️  OBS: if you donwload a different version this module may not work! 
3. During the installation, make sure to check the box: 

        Add Julia to PATH

### 4. Install the Julia package BoreholeNetwoksSimulator

   Start Julia and type the following commands **one at a time**, pressing Enter after each:

       using Pkg;
       pkg"registry add https://github.com/marcbasquensmunoz/geothermal_registry";
       Pkg.add("BoreholeNetworksSimulator")

### 5. Download the model from GitHub
Through your **Command Prompt**, navigate to the folder containing the examples installed together with the CallingPython-Cffi Add-On. Default location:

        C:\TRNSYS18\TRNLib\CallingPython-Cffi\Examples


1. To navigate to the folder through the Command Prompt write:

        cd <your actual location>
        
2. Clone this GitHub repository into that folder, still in the Command Prompt run:

        git clone https://github.com/Letizia-BD/trnsys-bns.git

If you have succesfully cloned the repository a new folder has been created inside "C:\TRNSYS18\TRNLib\CallingPython-Cffi\Examples" (or your equivalent location). You can proceed to section "Install the specific Python dependencies for this model".

If you instead got the error: 

        'git' is not recognized as an internal or external command operable program or batch 

you have to install Git:

I. Download and install the latest Git version from [git-scm.com](https://git-scm.com/install/windows)

II. Make sure **Add Git to PATH** is checked during installation.

III. Restart your computer and try the clone command again.

### 5. Install the specific Python dependencies for this model
In the **Command Prompt**, run these commands **one at a time**, pressing Enter after each:

            py -3.10 -m pip install openpyxl==3.1.5
            py -3.10 -m pip install scipy==1.15.3
            py -3.10 -m pip install pandas==2.2.3
            py -3.10 -m pip install juliacall==0.9.25

>✅ After completing these steps, your environment is ready to run the trnsys-bns Model.




