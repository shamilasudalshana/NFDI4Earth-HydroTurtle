# 🐢 NFDI4Earth-HydroTurtle

**HydroTurtle** is a Python tool for converting hydrological data (like time series and catchment attributes) into RDF triples in [Turtle (`.ttl`)](https://www.w3.org/TR/turtle/) format.

It uses Semantic Web vocabularies such as **SOSA**, **SSN**, and **QUDT** to generate a knowledge graph of hydrological observations.

This tool was built using column mappings from the **[LamaH-CE dataset](https://essd.copernicus.org/articles/13/4529/2021/)**. It can be extended to other datasets through adaptations of the attribute-to-vocabulary mappings.

---

## 🌟 Features

- Convert CSV files (with or without timestamps) into RDF
- Optionally support shapefiles and coordinate transformation (to WGS 84)
- Create complex or nested triples using JSON templates
- Generate `.ttl` files with correct prefixes and syntax
- Command-line tool and Streamlit app included
- Built using modular and reusable Python functions

### 🎬 Demo

Check out the app in action:

[![Watch the demo](https://img.youtube.com/vi/VIDEO_ID/0.jpg)](https://youtu.be/Pv9qUvmHaUU)

## 🧪 Example RDF Output

Given a row:
```csv
ID,YYYY,MM,DD,2m_temp_mean
32,1981,01,19,-7.1
```

HydroTurtle generates:
```turtle
n4e_hyd:observation_1_c_32 rdf:type sosa:Observation ;
	sosa:observedProperty n4e_hyd:AirTemperature2mMean ;
	sosa:hasFeatureOfInterest n4e_hyd:catchment_32 ;
	sosa:madeBySensor n4e_hyd:sensor_32 ;
	sosa:memberOf sosa:observationCollection_32 ;
	sosa:resultTime "1981-01-19T00:00:00Z"^^xsd:dateTime ;
	sosa:hasResult [ 
                    rdf:type  qudt:QuantityValue;
                    qudt:numericValue  "-7.1"^^xsd:decimal;
                    qudt:unit  unit:DEG_C] .
```





## 🧩 Included Files

| File | Description |
|------|-------------|
| `convert_csv_folder.py` | CLI script to convert a folder of CSVs |
| `convert_csv_with_coords.py` | CLI with coordinate transformation |
| `streamlit_app.py` | Streamlit web interface |
| `lamah_mapping.json` | JSON mapping file for LamaH-CE CSV columns |
| `rdf_prefixes.json` | List of RDF prefixes used in the output |

> Note: All files are kept in the root of the project (no subfolders yet).

---

## 📦 Installation

1. Clone the repository:

```bash
git clone https://github.com/shamilasudalshana/NFDI4Earth-HydroTurtle.git
cd NFDI4Earth-HydroTurtle
```


2. (Optional but recommended) Create a virtual environment:

```bash
python -m venv venv
venv\Scripts\activate   # On Windows
# or
source venv/bin/activate   # On macOS/Linux
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```


## 🚀 Usage
### ✅ CLI (Convert Folder of CSVs)

Open `convert_csv_folder.py`, adjust file paths inside, and run:
```bash
python convert_csv_folder.py
```

To include coordinate transformation (e.g., EPSG:3035 → EPSG:4326), use:
```bash
python convert_csv_with_coords.py
```

### 🖥️ Streamlit App
Start the web interface:
```bash
pip install -r requirements.txt
streamlit run streamlit_app.py
```

Then upload your:
 - CSV files
 - lamah_mapping.json
 - rdf_prefixes.json
 - mapping_time.json (defines how to parse date/time from columns)

You can interactively convert and download `.ttl` RDF files.

### 🧠 Configuration Files

File | Purpose
|------|-------------|
`lamah_mapping.json` | Maps dataset columns to RDF triples
`rdf_prefixes.json` | Declares RDF namespace prefixes
`mapping_time.json` | Specifies how to extract time from the CSV


## 🙌 Acknowledgments
Built using the [LamaH-CE Dataset](https://essd.copernicus.org/articles/13/4529/2021/) 

The work was funded by the German Research Foundation through the project [NFDI4Earth](https://www.nfdi4earth.de/) (DFG project no. 460036893).
