## **Microbiome Data Visualization Dashboard**

## **Overview**
This project provides a dashboard that visualizes microbiome data using a Bubble Chart and a Bar Chart. 
The data represents bacterial cultures found in various samples, and the dashboard allows users to select a sample and view relevant information.

The dashboard consists of two charts:
- **Bubble Chart**: Displays bacteria cultures per sample with interactive markers.
- **Bar Chart**: Shows the top 10 bacteria cultures in a horizontal bar chart format.

Additionally, a **metadata panel** displays detailed information about the selected sample.

---


### **Libraries Used**
- **D3.js**: A JavaScript library for manipulating documents based on data. It is used for DOM manipulation, handling the dropdown, and building metadata and charts.
- **Plotly.js**: A graphing library used to generate interactive charts like the Bubble Chart and Bar Chart.
- **JavaScript (ES6)**: The code uses ES6 syntax, including arrow functions, promises, and template literals.

### **Files**
- **index.html**: The main HTML file that contains the layout and calls the necessary scripts.
- **app.js**: The main JavaScript file containing the code to build the charts and metadata panel.
- **samples.json**: The external JSON file containing the microbiome data. This data includes the bacterial cultures and metadata associated with different samples.

---

## **How It Works**

### **Data Source**
The dashboard uses a JSON file hosted at the URL:

```plaintext
https://static.bc-edx.com/data/dl-1-2/m14/lms/starter/samples.json
```

This file contains:
- **Samples**: A list of sample identifiers and associated data, including:
  - `otu_ids`: IDs of operational taxonomic units (OTUs).
  - `otu_labels`: Labels describing the OTUs.
  - `sample_values`: The number of bacteria for each OTU.
- **Metadata**: Information about each sample, such as age, ethnicity, gender, and location.

### **Main Functions**

#### **1. `init()`**
This function is executed when the page is loaded. It does the following:
- Fetches the list of sample names from the data.
- Populates a dropdown menu with these sample names.
- Calls the `buildCharts()` and `buildMetadata()` functions for the first sample in the list to display initial charts and metadata.

#### **2. `buildMetadata(sample)`**
This function populates the metadata panel with details about a selected sample. It does the following:
- Fetches the `metadata` from the JSON file.
- Filters the metadata based on the selected sample.
- Clears any previous metadata and appends new key-value pairs in the panel.

#### **3. `buildCharts(sample)`**
This function builds the Bubble Chart and Bar Chart based on the selected sample:
- **Bubble Chart**: Displays OTU IDs on the x-axis, sample values on the y-axis, and uses OTU labels as hover text. The size and color of the bubbles depend on the sample values and OTU IDs.
- **Bar Chart**: Displays the top 10 OTUs by sample values in a horizontal bar chart format. The chart uses OTU IDs as the y-axis and sample values as the x-axis.

#### **4. `optionChanged(newSample)`**
This function is triggered when a new sample is selected from the dropdown. It rebuilds both the charts and metadata panel for the new sample.

---
## **Code Explanation**

### **Data Fetching**
- The data is fetched using **`d3.json()`** which fetches data asynchronously from a URL.
- The JSON structure contains two main parts: **`metadata`** and **`samples`**.
  
### **D3.js for DOM Manipulation**
- **`d3.select()`** is used to select DOM elements (e.g., the dropdown menu, metadata panel, and chart containers).
- **`.append()`** adds new elements to the DOM, such as `<h6>` tags for displaying metadata or `<option>` tags for the dropdown.
- **`.html("")`** is used to clear any existing content in a DOM element before adding new content.

### **Plotly.js for Charting**
- **`Plotly.newPlot()`** is used to render the Bubble Chart and Bar Chart.
- **Bubble Chart** uses a `markers` mode and custom `size` and `color` properties to visually represent bacteria samples.
- **Bar Chart** uses a horizontal bar chart with a reversed data order to display the top 10 OTUs.

### **Interaction with the Dropdown**
- When the user selects a new sample, the **`optionChanged()`** function is triggered, which rebuilds the charts and metadata with the newly selected sample.



