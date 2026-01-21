# Quick Start Guide - PolypPal in 5 Minutes

Get up and running with PolypPal in just a few steps!

## Prerequisites
- Python 3.8 or higher
- Two sets of images (timepoint 1 and timepoint 2)

## Installation (1 minute)

```bash
git clone https://github.com/yourusername/polyppal.git
cd polyppal
pip install -r requirements.txt
```

## Setup (2 minutes)

1. **Organize your images** in two folders:
   ```
   project/
   ├── timepoint1/
   │   ├── sample_001.jpg
   │   └── sample_002.jpg
   └── timepoint2/
       ├── sample_001.jpg
       └── sample_002.jpg
   ```

2. **Copy and edit config file**:
   ```bash
   cp config_example.yaml my_config.yaml
   # Edit my_config.yaml with your paths
   ```

3. **Minimum config**:
   ```yaml
   dir1: "/path/to/timepoint1"
   dir2: "/path/to/timepoint2"
   output_excel: "/path/to/output.xlsx"
   annotated_dir: "/path/to/annotated"
   metadata_excel: null  # or path to metadata file
   ```

## Run (2 minutes)

```bash
python polyp_pal.py my_config.yaml
```

## Measure

1. **Calibrate scale**: Click 1 cm apart on ruler (both images)
2. **Measure object**: Click 2 perpendicular diameters (both images)
3. **Mark status**: Click on object if present, or click status button
4. **Repeat**: Tool auto-advances to next object
5. **Done**: Close window - data auto-saved to Excel

## Keyboard Shortcuts

- `q` / `e` - Rotate image 2 (if misaligned)
- `+` / `-` - Zoom in/out
- `u` - Undo
- Arrow keys - Pan

## Output

Check your output directory:
- **Excel file** with all measurements
- **Annotated images** folder with visual comparisons

## Next Steps

- See [README.md](README.md) for full documentation
- Customize status labels in config for your application
- Try manual mode (no metadata) for flexible measurement

## Troubleshooting

**Images not aligned?** Press `q` or `e` to rotate image 2

**Need more objects than expected?** Just keep measuring - tool allows it

**Want to resume later?** Progress auto-saved, just restart with same config

---

**Questions?** Open an issue on GitHub or see full README.md
