# Vessel-Diameter-Tools
Matlab tools for measuring blood vessel diameter

### In this repository:

##### getVesselWidths.mlapp: Matlab app for calculating vessel widths over time from multichannel .tif files
To run this app, clone this repository and double click the app, or enter `getVesselWidths` in the Matlab command window. 

After the app opens, click `Load Image File` to select a .tif file with blood vessels visible. When prompted, enter the number of color channels present in the .tif file, and the channel where blood vessels are most visible (i.e. the vessel channel). 

Next, click `Add Vessel` to manually draw 4-point boxes around the vessel segments of interest, one at a time. Each vessel box must be drawn with the 1st 2 points drawing a line along one side of the vessel segment, and the final 2 points drawing a line in the opposite direction along the other side of the vessel. After the 4 points have been drawn, double-click the 1st point to finish drawing the box.

After all vessel segment boxes have been drawn, click `Get Vessel Widths` to estimate the vessel width in each vessel segment, for every frame in the vessel channel of the .tif file. This is calculated automatically by collapsing the vessel segment into a single line (i.e. an average of all pixel lines crossing the vessel in that segment), fitting a 2-term gaussian function to that line crossing the vessel, and calculating the FWHM of the gaussian fit. This process is performed for every vessel segment and every frame individually.

Upon completion, this app will output 3 files:
1. A .mat file containing all vessel boxes drawn, an `MxN` matrix containing the calculated vessel widths for the `M` vessel segments in all `N` vessel frames, and an `MxN` matrix containing the `R^2`
2. A .svg file showing an image projection of the vessel channel, with all vessel boxes overlayed in unique colors
3. A .svg file showing the vessel widths for every vessel segment over time (frame #), color coded to match the boxes in file 2
