# photomicrograph-scalebar
Add a scale bar to photomicrographs

### Purpose

The purpose of this script is to automate and standardize the task of adding a scale bar to photomicrographs.  

### Usage notes

The program relies on the _PIL_ library, so that needs to be installed.  

In its current form, the script uses TrueType fonts in the Linux filesystem for adding text to the photos, so does not out-of-the-box support Windows file paths.  This will be added in the future, but in the meantime, the code can be customized by the end user to reflect his own filesystem font path.

The program is set up to be run from in the directory where the photos located.  So, navigate to that directory before running the script.  If no photos are found, the script will notify the user.

Only a limited number of photo types are currently included, but this can easily be modifed by adding to the _imagetypes_ variable and is only limited by what is supported by PIL.
