# gmid_skywater130nm

# Setup Ubuntu 24.04 LTS

Used this method to install: https://philipwig.com/tutorials/installing-skywater/#method-1-python-script-install
Changes from the steps provided:
Install Anaconda3/miniconda
make sure to activate the conda environment, use conda activate skywater
update the tool versions: python setup/skywater.py update -y
Failing install of ngspice -> change setup/scripts/ngspice/install.sh. Change libfftw3-3 to libfftw3-bin.
To find package, use apt search fftw3
add build-essential to install.sh to solve g++ command not found issue.
To solve skywater failing install, check err.txt and run the conda commands to accept terms of service.
Edit setup/scripts/skywater/install.sh -> comment out git SC HD and SC HVL -> this is logic library
Comment out make timing -> only for asic flow
All tools will be installed in ~/tools/
Edit setup/scripts/open_pdks/install.sh -> disable other variants of skywater pdk, only install variant A and disable GF180
If variants is set to ALL (A and B), install will exit unexpectedly.
Edit setup/scripts/open_pdks/install.sh. Remove tha paths "$1/skywater-pdk/" in the enable options in configure. this will force open_pdk to download fresh copy of skywater PDK.
This means we can skip step in cloning skywater pdk in previous step????
PDK is installed here: /usr/local/share/pdk/
Another great resource for installation of tools for skywater: https://github.com/HRITAM-MITRA/Installation-of-open-source-analog-design-tools-with-sky130-PDK
http://opencircuitdesign.com/open_pdks/

# AICEX
Too complicated for my use case. Uses docker and downloads its own models from skywater. I want something that can use what I already have..

# gmid (medwatt) python
after clone, install requirements numpy, scipy, matplotlib using pip.
cd to gmid git clone, "pip install ." to install package into python environment.
Devices: https://skywater-pdk.readthedocs.io/en/main/rules/device-details.html
