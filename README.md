# CellProfiler γ-H2AX Foci Detection Pipeline

Pipeline developed in CellProfiler for the analysis of H2AX immunofluorescence images in A549 cells.
It separates DAPI and H2AX channels, identifies nuclei and γ-H2AX foci, filters objects by size, shape and intensity, and exports measurements for downstream analysis.

## What it does

- Imports images from a structured folder hierarchy.
- Extracts metadata for time post-radiation and treatment condition.
- Splits the blue and green channels into grayscale images.
- Detects nuclei using object size and circularity constraints.
- Detects γ-H2AX foci using size, circularity and intensity thresholds.
- Filters foci inside nuclei to exclude artifacts.
- Exports quantitative measurements to a spreadsheet/CSV format.

## Folder structure

```text
Inmuno_A549_Duber_IR_H2AX_7425/
├── Placa_control/
│   ├── Control/
│   │   ├── 1.tif
│   │   ├── 2.tif
│   │   └── ...
│   └── Dubermatinib/
├── Placa_30min_post_IR_10_Gy/
│   ├── Control/
│   └── Dubermatinib/
└── Placa_4h_post_IR_10_Gy/
    ├── Control/
    └── Dubermatinib/

## Main modules

- Images
- Metadata
- NamesAndTypes
- Groups
- ColorToGray
- IdentifyPrimaryObjects
- MeasureObjectSizeShape
- FilterObjects
- MeasureObjectIntensity
- ExportToSpreadsheet

## How to use

1. Place your TIFF images in the expected folder hierarchy.
2. Open the `.cppipe` file in CellProfiler.
3. Check that the metadata rules match your folder names.
4. Verify the object size and intensity thresholds for your images.
5. Run the pipeline.
6. Export the results and analyze them in Excel, Python, or R.

## Technical specifications

**Designed for:**
- **Magnification:** 40X
- **Microscope:** Zeiss Apotome epifluorescence microscope
- **Cell line:** A549
- **Channels:** DAPI (nuclei, blue), γ-H2AX (green)

## Notes

- Diameter thresholds (nuclei: 50-100px, foci: 1-20px) and intensity threshold (0.06) optimized for 40X Zeiss Apotome images.
- If you change microscope magnification, exposure, or image quality, you may need to re-tune the pipeline.
- The metadata extraction step is optional, but it makes downstream tabulation easier.

## Output

The pipeline produces measurements for nuclei and γ-H2AX foci, including object counts, object properties, and metadata-linked results that can be used for statistical analysis.

## Author

Juan Jesús Martínez Gómez

## License

Licensed under the MIT License.
