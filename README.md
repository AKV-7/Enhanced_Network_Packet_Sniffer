 
# Enhanced Network Packet Sniffer

An advanced network packet sniffer with real-time GUI visualization, SYN flood attack detection, email alerting, and SQLite logging. Built using Python, Scapy, and Tkinter.

---

## Features

- Capture live TCP packets and decode TCP flags
- Detect SYN flood attacks based on customizable thresholds
- Send email alerts for detected attacks
- Log packet details and alerts to a local SQLite database
- Simple Tkinter-based GUI with Start/Stop controls and live output
- Configurable via environment variables for secure credential handling

---

## Installation

1. **Clone the repository:**

```bash
git clone https://github.com/yourusername/enhanced-network-packet-sniffer.git
cd enhanced-network-packet-sniffer
````

2. **Create and activate a virtual environment (optional but recommended):**

* On Windows:

```powershell
python -m venv venv
.\venv\Scripts\activate
```

* On macOS/Linux:

```bash
python3 -m venv venv
source venv/bin/activate
```

3. **Install required Python packages:**

```bash
pip install -r requirements.txt
```

*If `requirements.txt` is not present, install manually:*

```bash
pip install scapy python-dotenv
```

4. **Set up environment variables:**

Create a `.env` file in the project root directory and add your email credentials:

```env
EMAIL_ADDRESS=your_email@example.com
EMAIL_PASSWORD=your_email_password_or_app_password
RECEIVER_EMAIL=receiver_email@example.com
```

> **Important:** For Gmail users with two-factor authentication (2FA), use an app password instead of your normal password.

---

## Usage

Run the main GUI application:

```bash
python src/sniffer_gui.py
```

* Click **Start Sniffing** to begin capturing packets.
* Click **Stop Sniffing** to stop.
* Alerts and packet info will display in the GUI window.
* Alerts will also be emailed and logged in `attacks.db`.

---

## Database

* SQLite database file: `attacks.db`
* Table: `alerts`
* Stores details of detected attacks with timestamp.

To query the database (requires `sqlite3` installed):

```bash
sqlite3 attacks.db
sqlite> SELECT * FROM alerts;
```

---

## Configuration

* Customize thresholds and alert intervals inside `src/sniffer_gui.py`
* Secure credentials via `.env` and `dotenv` package

---

## Dependencies

* Python 3.7+
* [Scapy](https://scapy.net/)
* [Tkinter](https://docs.python.org/3/library/tkinter.html) (usually included with Python)
* [python-dotenv](https://github.com/theskumar/python-dotenv)

---

## Troubleshooting

* **Permission Errors:** Running packet sniffing usually requires admin/root privileges.
* **Email Sending:** Ensure SMTP credentials are correct and app password used if needed.
* **Missing modules:** Install dependencies as shown in Installation.
* **SQLite3:** Usually pre-installed with Python, but can be installed separately if needed.

---

## License

This project is licensed under the MIT License.

---

 
