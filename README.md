Mr.Tarek Rizq -QSTSS 
# Fifittbit Lock Screen & Telegram Notifier

This project monitors daily calorie burn from a Fitbit device and takes action on a Raspberry Pi 4. If the daily calories burned are below a specified threshold, a full-screen lock message is displayed on the tablet (with custom logos) and a Telegram notification is sent to a designated parent. Otherwise, a popup message is shown to indicate that the screen remains unlocked.

## Features

- **OAuth 2.0 Authentication with Fitbit:**  
  Retrieves an access token by launching a browser for user authorization.

- **Daily Calories Summary:**  
  Uses the Fitbit daily summary endpoint to obtain the total calories burned today.

- **Graphical User Interface (GUI):**  
  Uses Tkinter (with Pillow for image processing) to display a full-screen lock message (including two logos) when calories are below threshold, or a popup message when the threshold is met.

- **Telegram Notifications:**  
  Sends a Telegram message to a parent if the tablet locks due to low calorie burn.

- **Raspberry Pi 4 Compatibility:**  
  Designed to run on a Raspberry Pi 4 in a desktop environment.

## Requirements

- **Hardware:**  
  Raspberry Pi 4 running Raspberry Pi OS (with desktop environment).

- **Software:**  
  - Python 3.x  
  - Tkinter (usually pre-installed on Raspberry Pi OS)  
  - [Pillow](https://pillow.readthedocs.io/) for image processing  
  - [Requests](https://requests.readthedocs.io/) for HTTP requests

- **APIs & Accounts:**  
  - Fitbit Developer account with an app (preferably set as a "Personal" app to enable intraday/daily access).  
  - Telegram Bot (obtained via [@BotFather](https://t.me/BotFather)) with its token and the target chat ID.

## Installation

1. **Clone the Repository (or copy the script):**
   ```bash
   git clone <repository_url>
   cd <repository_directory>
(Optional) Create and Activate a Virtual Environment:

bash
Copy
python3 -m venv env
source env/bin/activate
Install Required Packages:

bash
Copy
pip install pillow requests
Place Logo Images: Ensure that moe1.png and moe2.png are in the same directory as the script, or update the file paths in the code accordingly.

Configuration
Open the script file (e.g., tarek.py) and update the following variables with your specific information:

Fitbit Credentials:

CLIENT_ID
CLIENT_SECRET
REDIRECT_URI (typically set to http://localhost:8080/callback)
Telegram Configuration:

TELEGRAM_BOT_TOKEN (your bot token)
TELEGRAM_CHAT_ID (the chat ID of the parent)
Threshold Settings:

The script is set to lock the screen if daily calories are less than 1000. Adjust this value in the code if needed.
Usage
Run the Script:

bash
Copy
python3 tarek.py
Complete Fitbit OAuth Authorization:

A browser window will open for Fitbit authorization.
Log in and grant the requested permissions. Once authorized, the script will capture the authorization code and exchange it for an access token.
Operation:

The script fetches today's daily calories summary from Fitbit.
If daily calories < 1000:
A full-screen lock message is displayed, showing the calories value.
A Telegram message is sent to the parent with the calories details.
If daily calories ≥ 1000:
A popup message is displayed, indicating that the screen is unlocked.
Running on Raspberry Pi 4
Ensure you are running in a graphical desktop environment (X11) so that Tkinter can display windows.
Open a terminal, navigate to the script's directory, and run:
bash
Copy
python3 tarek.py
Make sure your Raspberry Pi is connected to the internet so that the OAuth process and API calls function correctly.
Troubleshooting
Image Issues:
If the logos do not appear, verify that moe1.png and moe2.png are in the correct directory. The script uses the current script directory (or os.getcwd() if __file__ is unavailable).

Telegram Notifications:
Confirm that your TELEGRAM_BOT_TOKEN and TELEGRAM_CHAT_ID are correct. Test sending a message using the Telegram Bot API manually if needed.

Pillow Import Errors:
If you encounter errors importing ImageTk, ensure that you are running the script inside a virtual environment with an updated version of Pillow.

License
This project is licensed under the MIT License.

Acknowledgements
Fitbit Developer Documentation
Telegram Bot API
Pillow Documentation
Tkinter Documentation
pgsql
Copy

This `readme.dm` file explains the project, its features, requirements, installation steps, configuration instructions, usage, and troubleshooting tips. Save it as `readme.dm` (or change the extension to `.md` if preferred) and adjust details as needed.
