# Templates documentation

The `templates` directory contains 2 subdirctories:
1. `layouts`
2. `static`

**`layouts`:**

This directory contains the HTML files required to render the different screens of the dashboard webapp. These are:
1. `dashboard.html`: For the dashboard that users get to use see all the results. 
2. `load_data.html`: For the screen where users are asked to upload a CSV file with product links

<br>

**`static`:**

This directory contains all the static files and assets used in different parts of the website. The subdirectories are:
1. `css`: CSS files used to style the different webpages are located here. The files here are:
    - `dashboard.css`: to style the dashboard page
    - `load_data.css`: to style the data loading page
2. `data-files`: CSV files generated as intermediate results by the machine learning models are stored in this directory. These files are then used by `data_files_loader.py` to fetch the results and send them to `app.py`, so that relevant information can be displayed on the dashboard page.
3. `images`: some static image files used as assets in different parts of the website are stored in this directory
4. `wordclouds`: wordcloud images generated by the wordcloud searching tool of the website are stored here