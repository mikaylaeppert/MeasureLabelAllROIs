# MeasureLabelAllROIs

An ImageJ macro for automated measurement and counting of all ROIs (Regions of Interest) in the ROI Manager.

## Description

This macro streamlines the process of analyzing multiple regions within microscopy images by automatically measuring all ROIs and providing a total count. It's particularly useful for batch analysis workflows in scientific imaging.

## Features

- **Automated Measurement**: Measures area, mean intensity, and centroid coordinates for all ROIs
- **Batch Processing**: Processes all ROIs in the ROI Manager simultaneously
- **Precision Control**: Results displayed with 3 decimal place precision
- **Count Display**: Shows total number of analyzed ROIs in the log
- **Visual Feedback**: Displays all ROIs during analysis

## Requirements

- ImageJ or Fiji
- Image file(s) loaded in ImageJ
- ROIs added to the ROI Manager

## Usage

1. Open your image(s) in ImageJ
2. Add regions of interest to the ROI Manager
3. Run the macro: `Plugins > Macros > Run...` and select the script
4. Results will appear in the Results table
5. Total ROI count will be displayed in the Log window

## Output

- **Results Table**: Area, mean intensity, and centroid coordinates for each ROI
- **Log Window**: Total number of processed ROIs

## Notes

- Channel selection is determined by ROI configuration
- Works with any image format supported by ImageJ
- Measurements are performed with redirect disabled

## License

This project is open source and available under standard terms.

## FIJI Macro Script

    // MeasureLabelAllROIs
    // This macro will run “measure” on all ROIs in the ROI manager for open image files. ROI defines which
    // channel is used. It will then count the total number of ROIs and label as “objects”. 

    roiManager("Show All");
    roiManager("Select All");

    // Measure all ROIs
    run("Set Measurements...", "area mean centroid redirect=None decimal=3");
    roiManager("Measure");

    // Count ROIs
    n = roiManager("count");
    print("Total number of ROIs: " + n);
