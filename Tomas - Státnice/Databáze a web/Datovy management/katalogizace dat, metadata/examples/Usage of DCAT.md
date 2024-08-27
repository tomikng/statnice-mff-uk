---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT
### Example: Data Catalog with DCAT

```turtle
@prefix dcat: <http://www.w3.org/ns/dcat#> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .

# Define the data catalog
<https://example.org/catalog> a dcat:Catalog ;
    dct:title "Example Data Catalog" ;
    dct:description "A catalog of datasets related to environmental monitoring." ;
    dct:publisher <https://example.org/organization> ;
    dct:issued "2024-01-01"^^xsd:date ;
    dct:language "en" ;
    dcat:dataset <https://example.org/dataset/weather-data>,
                 <https://example.org/dataset/air-quality-data> ;
    dcat:service <https://example.org/service/weather-api> .

# Define a dataset within the catalog
<https://example.org/dataset/weather-data> a dcat:Dataset ;
    dct:title "Weather Data" ;
    dct:description "A dataset containing weather observations from various stations." ;
    dct:keyword "weather", "temperature", "humidity" ;
    dct:theme <http://example.org/themes/environment> ;
    dct:issued "2023-12-01"^^xsd:date ;
    dct:modified "2024-01-10"^^xsd:date ;
    dcat:distribution <https://example.org/dataset/weather-data/csv>,
                      <https://example.org/dataset/weather-data/api> .

# Define the distribution (CSV file)
<https://example.org/dataset/weather-data/csv> a dcat:Distribution ;
    dct:format "text/csv" ;
    dcat:accessURL <https://example.org/files/weather-data.csv> ;
    dct:title "Weather Data CSV File" .

# Define the distribution (API access)
<https://example.org/dataset/weather-data/api> a dcat:Distribution ;
    dct:format "application/json" ;
    dcat:accessURL <https://api.example.org/weather-data> ;
    dct:title "Weather Data API Access" .

# Define the Data Service providing API access
<https://example.org/service/weather-api> a dcat:DataService ;
    dct:title "Weather Data API Service" ;
    dct:description "An API service providing real-time access to weather data." ;
    dct:license <https://example.org/license> ;
    dcat:endpointURL <https://api.example.org/v1/weather> ;
    dcat:servesDataset <https://example.org/dataset/weather-data> ;
    dcat:endpointDescription <https://example.org/docs/weather-api> ;
    dcat:contactPoint <https://example.org/contact> .

# Define another dataset within the catalog
<https://example.org/dataset/air-quality-data> a dcat:Dataset ;
    dct:title "Air Quality Data" ;
    dct:description "A dataset containing air quality measurements from various cities." ;
    dct:keyword "air quality", "pollution", "environment" ;
    dct:theme <http://example.org/themes/environment> ;
    dct:issued "2023-11-15"^^xsd:date ;
    dct:modified "2024-01-05"^^xsd:date ;
    dcat:distribution <https://example.org/dataset/air-quality-data/json> .

# Define the distribution (JSON file)
<https://example.org/dataset/air-quality-data/json> a dcat:Distribution ;
    dct:format "application/json" ;
    dcat:accessURL <https://example.org/files/air-quality-data.json> ;
    dct:title "Air Quality Data JSON File" .

```

### Explanation of the Example

- **Catalog (`dcat:Catalog`)**: The catalog itself is represented with a title, description, publisher, issue date, and language. It contains references to datasets.
- **Datasets (`dcat:Dataset`)**: Each dataset in the catalog is described with attributes like title, description, keywords, themes, issue date, and modification date. The dataset is linked to one or more distributions.
- **Distributions (`dcat:Distribution`)**: Each distribution represents a specific accessible format of the dataset, such as a CSV file or an API endpoint. Each distribution has its own format and access URL.

### How It’s Used

- **Findability**: By using DCAT, this catalog and its datasets can be indexed in search engines and data portals, making it easier to find relevant data.
- **Interoperability**: Since DCAT is a standard vocabulary, other systems can easily understand and integrate this catalog’s metadata.
- **Reusability**: With clear metadata descriptions and accessible formats, the datasets are more likely to be reused in different contexts or by different users.

This example illustrates how DCAT can be applied to create a machine-readable and interoperable data catalog that supports the FAIR principles.