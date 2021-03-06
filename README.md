# PlanCheck
## Introduction
PlanCheck is a GUI-based tool (written in Python) designed to assist in verifying radiotherapy treatment plans as part of the Physics plan check process. It was developed in the Radiotherapy Department at University Hospital Galway during the National Radiation Oncology Physics Residency Programme. 

The Physics Plan Check process in UHG includes verifying that the treatment plan has been transferred correctly from the planning system to the Oncology Information Management System which delivers the treatment parameters to the linac. This application is designed to help automate this process by parsing the treatment data in DICOM and RTP format from the two systems and verifying that the parameters match. Both conformal and IMRT plans are supported. It was designed to support the data structures produced by the Oncentra Master Plan planning system and the Siemens LANTIS Oncology Information Management System, but could easily be extended to support other systems.

As well as assisting in the plan check process, this project also provided an opportunity to learn python and dip my feet into the world of object-oriented programming. 

## Requirements
- [Python 2](https://www.python.org/)
- [PyDicom](http://pydicom.readthedocs.io/en/stable/index.html), a Python package for handling DICOM files.


## Usage
- Run plancheck.py
- Export treatment plan as dicom file from Oncentra Masterplan planning system.
- Export treatment data as RTP file from Lantis.
- In the PlanCheck GUI, click "Load CRT" or "Load IMRT" in each of the OTP and Lantis plan boxes to load the exported data files.
- Click "Compare Plans" to compare plan parameters.
- Matching and mismatching parameters are shown in the boxes in the Results area.

### Parameters Checked
Plans are constructed from both the Lantis and Oncentra data and then compared parameter by parameter to check for mismatches. The following parameters are compared:
#### Prescription
- Lantis dose per beam matches prescription.
- Oncentra dose per beam matches prescription.
- Oncentra total dose matches prescription.

#### Portal Beam
- Energy
- Dose
- Monitor Units

#### Treatment Beams
- Beam Number
- Energy
- Dose
- Monitor Units
- Gantry Angle
- Collimator Angle
- Couch Angle
- SSD
- Position of Y Jaws
- Positions of each MLC pair

### Example
In the example below, three of the beams were renamed in Lantis and are showing up as mismatched parametes. All other parameters match.
![PlanCheck Screenshot](docs/plancheck_screenshot3.JPG?raw=true "PlanCheck Screenshot")


## Disclaimer
This application is a support tool to aid in plan checking and is not a substitute for plan checking by a trained professional. Responsibility for all aspects of the plan check process rests with the staff member carrying out the checks.