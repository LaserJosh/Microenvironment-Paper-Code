# Microenvironment Paper Code
 MATLAB Code used in Microenvironment Paper
 
 IMPORTANT: Please unzip the download as close to the root directory as possible, due to the filenames in the sample data the 260 character path length limit may be reached if unzipped inside several subfolders. ("Path too long" error will occur)


In each supplied folder are the different scripts written in MATLAB for processing and analysing the data in the following experiments:
In-situ UV-Vis experiments (both photoisomerisation of the monomers and photocycloaddition of the tethered molecules)

These scripts are provided in the hopes that anyone doing a similar project that has access to a MATLAB license will not need to start from scratch. I am still transitioning the code to be more accessible for non-MATLAB users, please feel free to reach out if you would like support.

For each MATLAB script, please run this with the same folder active in MATLAB and it will find the correct data and GUI state save file.
Attached is some sample data which should be enough to see how the script works, however the filesize of the data used in the paper is rather large and not attached. Full datasets of our data are available from the corresponding author upon request.

For the fluorescence and absorbance code:

The hierarchy for saving data begins with a folder in the same folder as the script, with the following form:

SampleID/SampleIDSolventConcentration/SampleIDSolventConcentration\<X\>Matlab.csv

where X is "Absorbance" for the absorbance csv, and is "Emission" for the fluorescence emission csv.

In the Absorbance csv file, the data for wavelength should be in column 3, and the data for absorbance should be in column 4. This is set my files contain baseline data in columns 1 and 2, and can be changed in the code to fit what suits the user.

In the Emission csv file, the data is saved through our instruments with repeating columns of Wavelength and Emission data for each excitation wavelength (eg. column 1 and 2 correspond to 1 emission plot from a single excitation wavelength). Every second column top row contains the information about the excitation wavelength, saved as "SampleIDSolventConcentrationEx\<YYY\>nm\<Z\>

where YYY is the excitation wavelength in nanometres and Z is the repeat sample ID (A, B, C, etc)

As long as you also use this format it will extract and label the correct data for each excitation wavelength and repeat sample ID (or you can customise this as required in the code).

There will be bugs, for example I have not accounted for situations where you are don't have equal numbers of repeats (some samples with 3 runs and some with 2). This is planned for another update.

For the steady-state code:

Data is in the same folder as the script, with the following form:

APCis = csv of action plot data of cis-isomer formation, columns 1-4 are: wavelength, conversion, pos error, negative error

APDimer = csv of action plot data of dimer formation, columns 1-4 are: wavelength, conversion, pos error, negative error

2 csv files then exist for the experimental absorbance of reactant and 1 product

1 csv file exists for the calculated molar absorptivity for the isomer product, if you have experimental absorbance data this can be replaced and the code updated.

Please update the code to your needs to suit your data!

For the in-situ UV-Vis:

The hierarchy for saving data begins with a folder in the same folder as the script, with the following form:

SampleID/SampleIDSolventConcentration/SampleIDSolventConcentration\<Z\>/SampleIDSolventConcentration\<YYY\>nm\<Z\>/SampleIDSolventConcentration\<YYY\>nm\<Z\>\_Absorbance\_\<h\>-\<m\>-\<s\>-\<ms\>.txt

where YYY is the excitation wavelength in nanometres, Z is the repeat sample ID (A, B, C, etc), h is the hour, m is the minute, s is the second, and ms is the millisecond for the timestamp of the data, saved by the instrument.

Here, the code will have to be changed depending on the format at which your instrument can save data. I use the timestamp of the data being aquired in the filename to sort the data, so you will need this in the filename.

If you want to change the format of the file save then just update that section of the code, note that I do it in two places, once to get the time of the first file and then again in a loop to get the time of every file.

Note that each csv file will likely have some preamble, and so the code looks where the data starts, if your csv file is exported differently such that the preamble makes it into the data, this will need a change in the code.

There will be bugs, for example I have not accounted for situations where you are don't have equal numbers of repeats (some samples with 3 runs and some with 2). This is planned for another update.

For the photoisomerisations, you will need to run the experiment at each wavelength until a stead-state absorbance is reached.

For the photocycloaddition, you only really need data with the initial linear conversion at each wavelength, however it's always good to have the full trend to make sure the reaction is clean!
