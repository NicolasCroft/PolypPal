# GitHub Repository Structure

This file describes the recommended folder structure for the PolypPal GitHub repository.

## Directory Tree

```
polyppal/
├── README.md                    # Main documentation (already created)
├── LICENSE                      # MIT License (already created)
├── CONTRIBUTING.md              # Contribution guidelines (already created)
├── QUICKSTART.md               # Quick start guide (already created)
├── IMAGES_GUIDE.md             # Guide for creating screenshots (already created)
├── requirements.txt            # Python dependencies (already created)
├── .gitignore                  # Git ignore rules (already created)
├── config_example.yaml         # Example configuration file (already created)
│
├── polyp_pal.py                # Main application (your current file)
├── polyp_pal_logo.png          # Application logo (your current file)
│
├── docs/                       # Documentation and images
│   ├── images/                 # Screenshots for README
│   │   ├── interface_overview.png
│   │   ├── main_interface.png
│   │   ├── measurement_demo.png
│   │   └── annotated_output.png
│   │
│   └── tutorials/              # Optional: detailed tutorials
│       ├── coral_tutorial.md
│       ├── bacteria_tutorial.md
│       └── general_tutorial.md
│
├── examples/                   # Optional: example data
│   ├── example_config.yaml
│   ├── sample_metadata.xlsx
│   └── README.md               # Describes example data
│
└── tests/                      # Optional: unit tests
    ├── test_image_registration.py
    ├── test_measurements.py
    └── test_data/
```

## What to Include

### Essential Files (Must Have)
- ✅ `README.md` - Main documentation
- ✅ `LICENSE` - MIT License
- ✅ `requirements.txt` - Dependencies
- ✅ `.gitignore` - Ignore rules
- ✅ `polyp_pal.py` - Main script
- ✅ `polyp_pal_logo.png` - Logo image
- ✅ `config_example.yaml` - Example configuration

### Important Files (Should Have)
- ✅ `CONTRIBUTING.md` - How to contribute
- ✅ `QUICKSTART.md` - Quick start guide
- `docs/images/` - Screenshots for README
- `CHANGELOG.md` - Version history (create when you have releases)

### Optional Files (Nice to Have)
- `examples/` - Sample data for users to test with
- `tests/` - Unit tests for developers
- `docs/tutorials/` - Application-specific tutorials
- `.github/workflows/` - CI/CD workflows
- `setup.py` - For pip installation

## Next Steps

1. **Create docs/images/ directory** and add screenshots
   - See IMAGES_GUIDE.md for what screenshots to take

2. **Add a CHANGELOG.md** when you create your first release:
   ```markdown
   # Changelog
   
   ## [1.0.0] - 2025-01-XX
   ### Added
   - Initial release
   - Two-timepoint measurement capability
   - Automatic image registration
   - Manual rotation adjustment
   - Excel export
   - Manual and metadata modes
   ```

3. **Consider adding examples/** directory with:
   - Sample configuration file
   - Sample metadata Excel file
   - README explaining the examples
   - Optional: small sample images (if not too large)

4. **If adding tests**, use pytest:
   ```
   tests/
   ├── test_registration.py
   ├── test_measurement.py
   └── conftest.py
   ```

## GitHub-Specific Files

### Create GitHub Issues Templates
Create `.github/ISSUE_TEMPLATE/`:

**bug_report.md**:
```markdown
---
name: Bug report
about: Report a bug in PolypPal
---

**Describe the bug**
A clear description of what the bug is.

**To Reproduce**
Steps to reproduce:
1. ...
2. ...

**Expected behavior**
What you expected to happen.

**Screenshots**
If applicable, add screenshots.

**Environment:**
- OS: [e.g., Windows 10, macOS 12, Ubuntu 20.04]
- Python version: [e.g., 3.9.7]
- PolypPal version: [e.g., 1.0.0]
```

**feature_request.md**:
```markdown
---
name: Feature request
about: Suggest a feature for PolypPal
---

**Feature Description**
Clear description of the feature.

**Use Case**
Why is this feature useful?

**Proposed Solution**
How might this work?
```

### Create Pull Request Template
Create `.github/pull_request_template.md`:
```markdown
## Description
Brief description of changes.

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Performance improvement

## Testing
- [ ] Tested with sample data
- [ ] Verified measurements are accurate
- [ ] Checked both manual and metadata modes

## Screenshots
If applicable.
```

## Recommended GitHub Settings

1. **Topics/Tags**: Add these to help discovery
   - `image-analysis`
   - `measurement-tool`
   - `python`
   - `opencv`
   - `marine-biology`
   - `research-tool`
   - `time-series`
   - `coral-reef`

2. **Description**: 
   "Interactive tool for measuring object growth between two timepoints. Originally developed for coral polyp studies, adaptable to any two-timepoint measurement application."

3. **Website**: Link to documentation or your lab website

4. **Enable**: 
   - Issues
   - Projects (optional)
   - Wiki (optional, for extended docs)

## File Sizes

Keep repository lean:
- Code files: Any size OK
- Images (docs): < 500KB each
- Logo: < 100KB
- Example data: < 10MB total or use Git LFS

If you have large example datasets, consider:
- Linking to external storage (Zenodo, figshare)
- Using Git LFS
- Providing download scripts
