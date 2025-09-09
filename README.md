# PhD Data Analysis Scripts

This repository contains a collection of Python scripts developed during my PhD for specific data analysis tasks. These tools were created for personal use and may not adhere to standard software development practices. They are shared here for historical record and as a reference of the work done.

# Files
Below is a brief description of each of the Python scripts included in this repository.


## 2022_Trace_Inspector_Theshold_Frames_Ger.py
This program features a user interface (UI) designed to inspect and select traces from a .txt file where each column represents a single trace or dataset.

Key Features:

Time Calculation: A field for setting the exposure time or characteristic detector time.

Data Inspection: A slider to inspect all data points within a trace.

Thresholding: A slider to adjust a threshold for separating "on" and "off" events. By default, this is set to the background Gaussian mean plus 10 sigma.

Trace Navigation: An editable field to jump to a specific trace by index.

Trace Selection: "Good Trace" and "Bad Trace" buttons to categorize traces for filtering.

Data Export:

Saves a new .txt file, named FILTERED_[original_name], containing only the selected "good traces."

Indicates the percentage of good traces selected.

Saves two additional .txt files with calculated "On" and "Off" times, provided the "calculate" button was pressed.

Internal Data Structure: The self.selection matrix stores trace data:

Column 1: Trace index.

Column 2: 1 for good traces, -1 for bad traces.

Column 3: The threshold value for the trace.

Columns 4 & 5: Deprecated fields for frame selection.

Column 6: "Step intensity," calculated as the green zone mean minus the red zone mean.

⚠️ Warning: The program will not calculate On and Off times if the exposure time is not set.

🐛 Detected Bugs:

The graph does not load correctly on file selection; moving the slider is required to update it.

The green and red zones are collapsed to one side of the graph.

##N anoDrop_read_data.py

This is a very manual script with no user interface, designed for a quick plot of data from a NanoDrop spectrophotometer. It can also calculate the peak of the spectra. The script uses a Savitzky-Golay filter to remove high-frequency noise and saves the generated plots.

## SMAnalyzer_NP edition 2022.py

This program features a user interface for detecting particles in a movie file and extracting their traces or spot intensities into a .txt file.

For Extracting Traces:

Select a custom Region of Interest (ROI).

Average frames within that ROI to get a sharper image.

"Get ROI mean" displays this averaged image, where particles will be detected.

Parameters: Set the minimum distance between maximums, a detection threshold, and the estimated size of the point spread function (PSF).

"Detect Molecules": Searches for local maximums and draws a box around each. It also calculates a background value from the periphery.

"Export Traces": Saves a .txt file with one column per particle and a reference .png image.

For Spot Intensities (Single Frame):

Go to a specific frame.

Set detection parameters (minimum distance, threshold, PSF size, background pixels).

"Detect Molecules": Identifies spots on the current frame.

Export:

Saves a file with a single column of normalized spot intensities.

Saves a "Morgane" file with two columns for each spot: individual ROI intensity and background intensity.

Saves a reference .png image.

Additional Features:

Manual ROI: Use the "New Small roi" button to manually add ROIs.

Spot Filtering:

Gaussian fit: Fits a 2D Gaussian to each ROI and removes spots where the fitted sigmas differ significantly.

Filter bg: Discards spots with a background intensity above a set threshold.

Histogram: Creates a histogram of detected spots.

"Crazy go" Button: Warning! Not for public use. This button subdivides all frames and applies both Gaussian and background filters multiple times.
## Trace_Inspector_Steps_Ger.py

Old version of the 2022_Trace_Inspector_threshold_Frames_Ger.py
only history can judge me

## .gitattributes

This is a configuration file used by Git to define attributes for pathnames. In this case, it likely helps standardize line endings across different operating systems to prevent issues when collaborating or viewing the files.

# Important Note
These scripts were developed for a specific purpose and environment during the course of a PhD. They may have hard-coded paths, require a specific version of Python or libraries, and may not be robust for general use. They are provided as-is, and users may need to modify them to suit their own data and environment.

# How to Use
Dependencies: You will likely need to install certain Python libraries, for sure as numpy and matplotlib.

Execution: Each script can be run from the command line, or by a interpreter like spider, often by passing a file path as an argument.

python script_name.py [input_file]

# License
This repository is shared for educational and reference purposes. The scripts are not intended for commercial use or distribution.
