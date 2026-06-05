# Overview
This repo holds the code for a tech-spike to experiment using Postman to query U.S. Department of Justice APIs. I wanted to
use Postman for the first time, experiment with new data visualization tools like Orange, and interact with crime data. 

# Tools Used

- [FBI Crime Data API](https://cde.ucr.cjis.gov/LATEST/webapp/#/pages/docApi)
- [Postman](https://learning.postman.com/)
  - [Newman Reporter CSV](https://www.npmjs.com/package/newman-reporter-csv)
  - [Newman CLI](https://learning.postman.com/docs/reference/newman-cli/command-line-integration-with-newman)
- [Orange Data Mining](https://orangedatamining.com/)
- [plotnine](https://plotnine.org/)

# Process

I used the Postman VSCode extension to test calling the FBI's Crime Data API. The Postman collection I built and used is viewable: `FBI.postman_collections.json`. You can re-run the Postman collection using Newman CLI: 

```
newman run FBI.postman_collection.json --env-var "FBI_API_KEY=YOUR_KEY_HERE"
```

Within the extension, I used the 'Send and Download' feature to locally save the response bodies to JSON files in `/data`. I used `pandas` and `plotnine` to do some data parsing and exploratory visualizations in a Python notebook.

Because Orange requires .csv data, I then used the Newman CLI and the `newman-reporter-csv` package to run the Postman collection and save results to a local file (not committed, as it contains authentication information). I used Claude Code to quickly parse those results into a better-formatted `data/crime_monthly.csv`. Then, I experimented with a variety of visualization tools in Orange, a visual programming language.

# Sample Visualizations

The code in `crime_trend_viz.ipynb` generates simple summary visualizations using `plotnine` to mimic the grmamar of graphics in R's `ggplot2`. This exercise was mostly for me to flex my Pandas muscles again, and to see how `plotnine` functions:
![alt text](image-1.png)

For the first time, I used Orange's data visualizations tools to build simple charts detailing trends in crime throughout the past 5 years:
![alt text](<Hate Crime Bar Chart.png>)

While the visualizations are pretty simple, Orange's visual programming makes for an interesting mental model of data processing: 

![alt text](<FBI Data Visualizations.svg>)

The pipeline used in Orange is saved to `FBI Data Visualizations.ows`. 
# AI Policy

I consulted Claude Code for setup, debugging, documentation, and menial data processing tasks. All code in this repo was written by me. 