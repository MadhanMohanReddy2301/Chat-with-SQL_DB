# Vanna AI SQL Querying Application

This project demonstrates how to use the Vanna AI library to connect to a SQLite database and query for the top 10 albums by sales from the Chinook database. Additionally, a Flask application is created to run the Vanna AI interface.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [License](#license)

## Prerequisites

Before you begin, ensure you have met the following requirements:
- Python 3.6 or later installed on your machine.
- The required Python packages installed (listed in the `requirements.txt`).

## Installation

1. Clone this repository to your local machine:
    ```sh
    git clone https://github.com/your-username/vanna-ai-sql-query.git
    cd vanna-ai-sql-query
    ```

2. Install the required Python packages:
    ```sh
    pip install -r requirements.txt
    ```

3. Ensure you have the Chinook SQLite database file (`Chinook.sqlite`) in the `vannaAi` directory. You can download it from [here](https://github.com/lerocha/chinook-database).

## Usage

1. Set your Vanna API key by replacing `your-email@example.com` with your email address:
    ```python
    vn = VannaDefault(model='chinook', api_key=vanna.get_api_key('your-email@example.com'))
    ```

2. Ensure the path to your SQLite database is correct in the `connect_to_sqlite` method:
    ```python
    vn.connect_to_sqlite('vannaAi/Chinook.sqlite') # Adjust the path if necessary
    ```

3. Run the application:
    ```sh
    python app.py
    ```

    This will start a Flask server running the Vanna AI interface.

4. Access the application in your web browser at `http://127.0.0.1:5000`.

## Code Overview

Here is the main code used in the application:

```python
import vanna
from vanna.remote import VannaDefault
from vanna.flask import VannaFlaskApp

# Initialize VannaDefault with the specified model and API key
vn = VannaDefault(model='chinook', api_key=vanna.get_api_key('pmadhan006@gmail.com'))

# Connect to the SQLite database
vn.connect_to_sqlite('vannaAi/Chinook.sqlite') # Path to your SQLite database

# Ask a query to Vanna
vn.ask("What are the top 10 albums by sales?")

# Create and run the Flask app
VannaFlaskApp(vn).run()
