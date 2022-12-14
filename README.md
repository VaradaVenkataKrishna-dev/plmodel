# Private Label Products Dashboard Tool

**To use the tool:**

The only file with which one has to interact in order to use the tool is `app.py`.

If you wish to use the tool for a new product (i.e. with a new set of product links), then open the terminal within this _dashboard_ directory, and type in the following command:
`python3 app.py models-not-trained`

On the other hand, if you wish to use a tool for a product for which you have previously generated the dashboard, then open the terminal within this _dashboard_ directory, adn type in the following command:
`python3 app.py models-trained`

In either one of these cases, after you have run this command, import statements will run, and you should wait till you see the following message in the terminal:
`Running on http://127.0.0.1:5000 (Press CTRL+C to quit)`

At this point, you can copy this link (`http://127.0.0.1:5000`) and paste it in your browser (preferably Chrome) and you will be redirected to the relevant section of the dashboard tool.

<hr>

<br>

There are 3 code-containing files in the main directory of this project:
1. `app.py`
2. `run_before.py`
3. `data_files_loader.py`

The code in all of the subdirectories of this project are called from within these files at the appropriate times.

<br>

**`app.py`:**

_Dependencies:_
- [`flask`](https://flask.palletsprojects.com/en/2.2.x/)
- [`werkzeug`](https://pypi.org/project/Werkzeug/)
- [`os`](https://docs.python.org/3/library/os.html) (Note: `os` does not need to be installed; it comes by default with `python`)
- [`sys`](https://docs.python.org/3/library/sys.html) (Note: `sys` does not need to be installed; it comes by default with `python`)
- [`webbrowser`](https://docs.python.org/3/library/webbrowser.html) (Note: `webbrowser` does not need to be installed; it comes by default with `python`)

This file contains the code that spins up the Flask server which runs the backend code for the different screens of the dashbaord webapp. The code in this file passes all the data from the backend to the frontend HTML files, so that the relevant results can be displayed on the frontend.

In order to do this, once the user has submitted the product links CSV file, the code from the `run_before.py` file is run from within `app.py`, and later, when the dashboard is being shown, the results that need to be passed to the frontend are first generated by running functions contained within `data_files_loader.py` (these functions are also called from within `app.py`).

<br>

**`run_before.py`:**

The code in this file is run after the user has uploaded a CSV file containing product links. This file then runs code that is contained within files in some of the subdirectories of this project to scrape the data, run the ABSA models, generate the report results (CSV files in the `static/data-files` folder), generate product rankings, train the topic modelling models, extract the improvement areas, and generate the mindmap image.

After all of this is complete, the dashboard webapp redirects to the actual dashboard page, and the extracted results can be viewed (and interacted with) over there.

<br>

**`data_files_loader.py`:**

_Dependencies:_
- [`pandas`](https://pandas.pydata.org/)
- [`ast`](https://docs.python.org/3/library/ast.html)

This file contains functions that fetch results from the various CSV files in the `static/data-files` folder, and from the topic modelling models, and returns those results in a format that can be consumed by `app.py` and directly pushed to the HTML files for rendering.
