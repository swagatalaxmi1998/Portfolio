# Wildfire Watch Australia

# Overview
This is an interactive dashboard built using Dash and Plotly to visualize historical wildfire data in Australia. Users can select a region and year to view trends in wildfire activity.

## Features
- **Interactive Region Selection**: Choose from 7 Australian regions.
- **Year Selection**: Select a year between 2005 and 2020.
- **Visualizations**:
  - Pie Chart: Monthly average estimated fire area.
  - Bar Chart: Monthly average count of pixels for presumed vegetation fires.

## Technologies Used
- `Python`
- `Dash`
- `Plotly`
- `Pandas`

## Analysis

### Library usage

-	Pandas (pd): Used to load and preprocess the wildfire dataset.
-	Dash (dash): Framework for building the web app.
-	Dash Components (html, dcc):
     - `html`: Used to create HTML elements like headings, divs, etc.
     - `dcc`: Used for interactive components like dropdowns, radio buttons, and graphs.
-	Plotly Express (px): Used to create interactive visualizations like pie charts and bar charts.

### Preprocessing data

-	`pd.to_datetime` used to converte the `Date` column to a `datetime` format.
-	`dt.month_name()` applied to extract the month name (e.g., January, February) from the date.

### Dashboard Layout

- `html.H1` used to add a title to the dashboard.
- `dcc.RadioItems` used to create radio buttons for selecting a region.
- `dcc.Dropdown` adds a dropdown menu for selecting a year.
- `html.Div` structures the layout into sections.
- `id=plot1` and `id=plot2`are placeholders for the graphs that will be generated dynamically

### Callback Function

-	`@app.callback` links the inputs (region and year) to the outputs (graphs).
- `update_graphs` generates the graphs based on the selected region and year.
  -	`region_data` used to filter the data for the selected region.
  -	`y_r_data` filters the data for the selected year.
  - `px.pie` for creating a pie chart for the monthly average estimated fire area.
  -	`px.bar` for showing a bar chart for the monthly average count of pixels for presumed vegetation fires.
  -	`dcc.Graph` embeds the `Plotly` figures into the `Dash` app.
 
### Running the App
`if __name__ == '__main__':
    app.run_server(debug=True)`
    
This code is used to start the `Dash` app on a local server.

## Conclusion

The dashboard enables users to interactively explore the data, making it easy to identify patterns and anomalies. By selecting different regions and years, users can observe how factors like climate, vegetation, and human activity influence wildfire trends over time and make comparison between regions. Further research can be looking closely at the wildfire prone regions and understanding why one regions is more prone to fires than others. Effective measures can be taken for the residential areas around regions with more wildfire frequency. 


