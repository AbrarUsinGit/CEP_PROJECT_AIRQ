# Project Dependencies & Tech Stack

Here is a complete list of everything used in this project.

## 1. Languages
-   **Python (v3.x)**: The core programming language for the backend.
-   **HTML5**: Structure of the web pages.
-   **CSS3**: Styling (Vanilla CSS, no frameworks like Bootstrap/Tailwind).
-   **JavaScript (ES6+)**: Frontend logic (fetching API data, handling UI).

## 2. Python Modules (Libraries)
These are installed via `pip` and listed in `requirements.txt`.

| Module | Purpose |
| :--- | :--- |
| **`django`** | The main web framework. |
| **`requests`** | For making HTTP requests to OpenMeteo API. |
| **`openmeteo-requests`** | Official client for OpenMeteo API. |
| **`requests-cache`** | Caches API responses to speed up the app. |
| **`retry-requests`** | Automatically retries failed API calls. |
| **`numpy`** | Required by `openmeteo-requests` for data handling. |
| **`pandas`** | Required by `openmeteo-requests` for data handling. |

## 3. VS Code Extensions (Recommended)
To work on this project efficiently in VS Code, install these extensions:

-   **Python** (by Microsoft): Essential for Python support.
-   **Django** (by Baptiste Darthenay): Syntax highlighting for Django templates.
-   **Prettier - Code formatter**: Keeps your HTML/CSS/JS clean.
-   **SQLite Viewer**: Lets you view the `db.sqlite3` database directly in VS Code.

## 4. APIs Used
-   **OpenMeteo Geocoding API**: Converts city names to coordinates.
-   **OpenMeteo Air Quality API**: Fetches pollution data (PM2.5, AQI).
-   **Gmail SMTP**: Used for sending email alerts.

## How to Install Everything
If you are setting this up on a new computer, just run:

```bash
pip install -r requirements.txt
```
*(Note: I will create this file for you now so it's up to date).*
