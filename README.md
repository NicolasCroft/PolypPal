# PolypPal - Interactive Two-Timepoint Measurement Tool

**Measure object growth and changes between two timepoints with precision and ease**

PolypPal is a powerful Python-based visual measurement tool for tracking size changes in objects across two timepoints. While originally developed for marine biology research (coral polyp recruit studies), **it's designed to work with any application requiring two-timepoint diameter measurements**.

![PolypPal Interface](interface_overview.png)

## Use Cases

Was used to measure coral recruits in this study, which is not yet published: [example_study.pdf](https://github.com/NicolasCroft/PolypPal/blob/main/Example_Study.pdf)

PolypPal excels at comparing objects between two images taken at different times:

- **Marine Biology**: Coral polyp recruitment, growth rates, mortality tracking
- **Microbiology**: Bacterial colony growth, inhibition zones
- **Botany**: Seedling growth, leaf spot disease progression
- **Cell Biology**: Cell culture confluence, spheroid growth
- **Material Science**: Crystal growth, corrosion progression
- **Medical Imaging**: Lesion size tracking, wound healing
- **Any application** where you need to measure circular/elliptical objects at two timepoints!

## Key Features

### Interactive & Visual
- **Point-and-click measurements**: No complex image processing knowledge needed
- **Real-time visual feedback**: See measurements as you make them
- **Dots persist through operations**: All measurements stay visible
- **Color-coded tracking**: Each object gets a unique color for easy identification

### Intelligent Image Handling
- **Automatic image registration**: Detects and aligns objects automatically
- **Manual rotation control**: Fine-tune alignment with keyboard (q/e keys, 22.5° increments)
- **Coordinate transformation**: Measurements automatically adjust when you rotate images
- **Zoom and pan**: Navigate large images easily (+/- keys, arrows)

### Flexible Workflow
- **With or without metadata**: Works in manual mode (no expected counts) or metadata-driven mode
- **Customizable status labels**: Adapt "Dead/Chimera" to your application (e.g., "Contaminated/Merged")
- **Resume capability**: Pick up exactly where you left off
- **Progress tracking**: JSON-based state management

### Professional Output
- **Excel export**: All measurements with timestamps and status
- **Annotated images**: Visual comparison with measurements marked
- **Configurable via YAML**: No code changes needed for different experiments

## Requirements

- Python 3.8 or higher
- Works on Windows, macOS, and Linux

**Dependencies:**
```
numpy
opencv-python
matplotlib
pandas
scikit-image
scipy
pyyaml
pillow
openpyxl
```

## Quick Start

### 1. Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/polyppal.git
cd polyppal

# Install dependencies
pip install -r requirements.txt
```

### 2. Prepare Your Images

Organize your images in two directories:
```
/my_project/
  ├── timepoint1/
  │   ├── sample_001.jpg
  │   ├── sample_002.jpg
  │   └── ...
  └── timepoint2/
      ├── sample_001.jpg
      ├── sample_002.jpg
      └── ...
```

**Image naming**: Images from both timepoints should have matching identifiers (e.g., same number or ID).

### 3. Create Configuration File

Create `config.yaml`:

```yaml
# Image directories
dir1: "/path/to/timepoint1"
dir2: "/path/to/timepoint2"

# Output files
output_excel: "/path/to/measurements.xlsx"
annotated_dir: "/path/to/annotated_images"

# Optional: Metadata file with expected counts
# Omit this line or set to null for manual mode
metadata_excel: null

# Optional: Customize button labels for your application
button_labels:
  status_1: "Dead"        # Or: "Contaminated", "Apoptotic", "Wilted", etc.
  status_2: "Chimera"     # Or: "Merged", "Senescent", "Diseased", etc.
```

### 4. Run PolypPal

```bash
python polyp_pal.py config.yaml
```

## How to Use

### Basic Workflow

1. **Launch**: Images load automatically, aligned using automatic detection
2. **Calibrate scale**: Click two points 1 cm apart on the ruler (if present)
3. **Measure diameters**: 
   - Click 2 points for first diameter
   - Click 2 points for perpendicular diameter
4. **Mark status** (Timepoint 2):
   - Click on object if alive/present
   - Click status button if dead/absent
5. **Repeat**: Tool automatically moves to next object
6. **Close window**: When done, saves all data and annotated images

### Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `q` / `e` | Rotate image 2 left/right (22.5°) |
| `+` / `-` | Zoom in/out |
| Arrow keys | Pan the view |
| `r` | Reset view |
| `u` | Undo last action |
| `h` | Show help |

### Two Modes of Operation

#### Manual Mode (No Metadata)
- Set `metadata_excel: null` in config
- Measure as many objects as you want
- Close window when done
- Perfect for exploratory work

#### Metadata Mode
- Provide Excel file with expected object counts
- Shows progress (e.g., "3/5 objects measured")
- Can exceed expected counts if needed
- Calculates yield/survival rates

## Output Files

### Excel Spreadsheet
Columns include:
- Sample ID
- Object number
- Diameter 1 & 2 (timepoint 1)
- Diameter 1 & 2 (timepoint 2)
- Area calculations
- Status (Alive/Dead/Other)
- Timestamp
- Comment

### Annotated Images
Side-by-side comparison images with:
- Color-coded measurements for each object
- Status indicators
- Scale information
- Saved as high-resolution PNG files

## Customization Examples

### For Bacterial Colonies
```yaml
button_labels:
  status_1: "Contaminated"
  status_2: "Merged"
```

### For Cell Cultures
```yaml
button_labels:
  status_1: "Apoptotic"
  status_2: "Senescent"
```

### For Plant Studies
```yaml
button_labels:
  status_1: "Wilted"
  status_2: "Diseased"
```


## Metadata File Format (Optional)

If using metadata mode, create an Excel file with these columns:

| sample_id | original_recruits | yield_calc | recruits |
|-----------|-------------------|------------|----------|
| 1         | 10                | 0.80       | 8        |
| 2         | 12                | 0.75       | 9        |

- `sample_id`: Unique identifier matching image filenames
- `original_recruits`: Expected count at timepoint 1
- `yield_calc`: Expected survival rate (0-1)
- `recruits`: Expected count at timepoint 2

## Troubleshooting

**Images don't align properly?**
- Use `q` and `e` keys to manually rotate image 2
- Measurements automatically adjust when you rotate

**Dots disappear after rotating?**
- This is intentional - measurements from different rotations are hidden to avoid confusion
- Rotate back to see them, or they're still in the Excel file

**Tool crashes when starting new object?**
- Ensure you have the latest version
- Check that all dependencies are installed

**Can't see the logo?**
- Ensure `polyp_pal_logo.png` is in the same directory as `polyp_pal.py`
- Tool works fine without it!

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

Originally developed for coral recruitment studies in marine biology research. Special thanks to the marine ecology community for feedback and testing.

## Contact

Questions? Issues? Feature requests?
- Open an issue on GitHub
- Email: nickcroft07@gmail.com

---

