---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě přednášek od Klimka

### **Step-by-Step Mapping with Annotations**

```csv
id,title,author,published_date,price
1,The Catcher in the Rye,J.D. Salinger,1951-07-16,8.99
2,To Kill a Mockingbird,Harper Lee,1960-07-11,7.99
3,1984,George Orwell,1949-06-08,6.99
```

### **Step 1: Define JSON-LD Metadata with Mappings**

Here, we define the metadata, specifying how each column in the CSV is mapped to RDF properties.

```json
{
  "@context": "http://www.w3.org/ns/csvw",
  "url": "books.csv",
  "tableSchema": {
    "columns": [
      {
        "name": "id",
        "titles": "id",
        "datatype": "integer",
        "propertyUrl": "http://example.org/schema/id",
        "valueUrl": "http://example.org/books/{id}"
      },
      {
        "name": "title",
        "titles": "title",
        "datatype": "string",
        "propertyUrl": "http://schema.org/name"
      },
      {
        "name": "author",
        "titles": "author",
        "datatype": "string",
        "propertyUrl": "http://schema.org/author"
      },
      {
        "name": "published_date",
        "titles": "published_date",
        "datatype": "date",
        "propertyUrl": "http://schema.org/datePublished"
      },
      {
        "name": "price",
        "titles": "price",
        "datatype": "decimal",
        "propertyUrl": "http://schema.org/price"
      }
    ],
    "primaryKey": "id"
  },
  "rdfs:label": "Books",
  "rdfs:comment": "A list of books and their details",
  "dc:creator": "Tomas"
}
```

#### **Annotations Explained:**

1. **@context**: Defines the context for interpreting the metadata according to the CSVW standard.
2. **url**: The location of the CSV file to be mapped.
3. **tableSchema**: Describes the structure of the table, including the columns.

   **Within `columns`:**
   
   - **name**: Internal name for the column (matches the CSV header).
   - **titles**: The actual title as it appears in the CSV file.
   - **datatype**: Defines the data type of the column values (e.g., `integer`, `string`, `date`, `decimal`).
   - **propertyUrl**: Specifies the RDF property to which the CSV column is mapped. This URL represents the predicate in the RDF triple.
   - **valueUrl** (for `id`): Constructs a URI for each book, using the `id` value from the CSV. This URL will be used as the subject in the RDF triple.

4. **primaryKey**: Identifies the column that acts as the unique identifier for each row, ensuring each RDF subject is unique.

### **Step 2: Transformation into RDF**

With the metadata defined, the transformation process maps each row in the CSV to RDF triples. Let's see how this looks for the first row:

```turtle
@prefix ex: <http://example.org/books/> .
@prefix schema: <http://schema.org/> .

ex:1 a schema:Book ;
  schema:name "The Catcher in the Rye" ;
  schema:author "J.D. Salinger" ;
  schema:datePublished "1951-07-16"^^xsd:date ;
  schema:price "8.99"^^xsd:decimal .
```

#### **Breaking Down the RDF Output:**

1. **Subject**: `ex:1` (constructed using the `valueUrl` from the `id` column). It uniquely identifies the book using its `id`.

2. **Predicates and Objects**:
   - `schema:name` maps to the `title` column and provides the book's title.
   - `schema:author` maps to the `author` column and specifies the author.
   - `schema:datePublished` maps to the `published_date` column and provides the publication date.
   - `schema:price` maps to the `price` column and specifies the book's price.

### **Key Points to Highlight:**

- **propertyUrl**: This annotation is crucial as it directly maps CSV columns to RDF predicates. Each column in your CSV corresponds to a specific RDF property, ensuring that your CSV data can be accurately represented in RDF format.
- **valueUrl**: Used primarily for identifiers, this allows you to create unique URIs for your RDF subjects using the values in your CSV, ensuring that each resource is distinctly addressable on the web.

### **Summary**

The process of mapping CSV columns to RDF involves defining a detailed metadata file that specifies how each piece of data in the CSV is to be interpreted and transformed into RDF triples. The `propertyUrl` and `valueUrl` are key annotations in the metadata that determine how the CSV data is converted into RDF, enabling semantic interoperability and ensuring that the data is machine-readable and linked on the web.