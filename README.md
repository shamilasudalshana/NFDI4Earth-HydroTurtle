# 🐢 NFDI4Earth-HydroTurtle

**HydroTurtle** is a flexible Python tool that converts hydrological data (e.g., CSV or Shapefiles) into semantic RDF triples in **Turtle (`.ttl`) format**, following standard ontologies like SOSA/SSN, QUDT, and others.

Built as part of the [NFDI4Earth](https://www.nfdi4earth.de/) initiative, HydroTurtle supports both:
- ✅ **Command-line conversion** for batch processing
- ✅ **Streamlit-based interface** for easy use by non-programmers

---

## 🚀 Features

- Convert CSV and shapefile data into structured RDF triples
- Time-aware observations with configurable formats
- Handles both simple and complex nested triple mappings
- Automatically writes `.ttl` files with correct prefixes
- Streamlit UI for uploading, previewing, and exporting
- Modular Python library structure (easily extendable)

---

## 📦 Installation

```bash
git clone https://github.com/shamilasudalshana/NFDI4Earth-HydroTurtle.git
cd NFDI4Earth-HydroTurtle
pip install -r requirements.txt