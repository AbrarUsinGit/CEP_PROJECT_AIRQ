# How to Deploy to PythonAnywhere

Follow these exact steps to get your Air Quality App live on the internet.

## Phase 1: Prepare your Code (Local Computer)

1.  **Create a GitHub Account** (if you don't have one) at [github.com](https://github.com).
2.  **Create a New Repository**:
    *   Name it `aqi-alert-system`.
    *   Make it **Public**.
    *   Do **not** add a README or .gitignore (we already have them).
3.  **Push your code**:
    Open your terminal in VS Code and run these commands one by one:
    ```bash
    git init
    git add .
    git commit -m "Initial commit"
    git branch -M main
    git remote add origin https://github.com/YOUR_USERNAME/aqi-alert-system.git
    git push -u origin main
    ```
    *(Replace `YOUR_USERNAME` with your actual GitHub username)*.

## Phase 2: PythonAnywhere Setup

1.  **Sign Up**: Go to [pythonanywhere.com](https://www.pythonanywhere.com/) and create a free account.
2.  **Open a Console**:
    *   Go to the **Consoles** tab.
    *   Click **Bash**.
3.  **Clone your Code**:
    Type this command (replace with your repo URL):
    ```bash
    git clone https://github.com/YOUR_USERNAME/aqi-alert-system.git
    ```
4.  **Create Virtual Environment**:
    Run these commands in the Bash console:
    ```bash
    cd aqi-alert-system
    mkvirtualenv --python=/usr/bin/python3.10 myenv
    pip install -r requirements.txt
    ```

## Phase 3: Configure Web App

1.  Go to the **Web** tab (top right).
2.  Click **Add a new web app**.
3.  Click **Next** -> Select **Manual configuration** (NOT Django) -> Select **Python 3.10** -> **Next**.
4.  **Virtualenv Section**:
    *   Enter the path: `/home/YOUR_USERNAME/.virtualenvs/myenv`
    *   (Replace `YOUR_USERNAME` with your PythonAnywhere username).
5.  **Code Section**:
    *   Source code: `/home/YOUR_USERNAME/aqi-alert-system`
    *   Working directory: `/home/YOUR_USERNAME/aqi-alert-system`

## Phase 4: The WSGI File

1.  In the **Web** tab, click the link next to **WSGI configuration file**.
2.  Delete **everything** in that file.
3.  Paste this code:
    ```python
    import os
    import sys

    # Assuming your username is 'yourusername', the app is in 'aqi-alert-system'
    path = '/home/YOUR_USERNAME/aqi-alert-system'
    if path not in sys.path:
        sys.path.append(path)

    os.environ['DJANGO_SETTINGS_MODULE'] = 'config.settings'

    from django.core.wsgi import get_wsgi_application
    application = get_wsgi_application()
    ```
    *(Make sure to replace `YOUR_USERNAME` with your actual username)*.
4.  Click **Save**.

## Phase 5: Final Steps

1.  **Database**:
    Go back to the **Bash** console and run:
    ```bash
    python manage.py migrate
    python manage.py createsuperuser
    ```
2.  **Static Files** (CSS/JS):
    *   Go to the **Web** tab.
    *   Under **Static files**:
        *   **URL**: `/static/`
        *   **Directory**: `/home/YOUR_USERNAME/aqi-alert-system/static`
3.  **Reload**:
    *   Click the green **Reload** button at the top of the Web tab.
4.  **Visit your site!**
    *   Go to `https://YOUR_USERNAME.pythonanywhere.com`.
