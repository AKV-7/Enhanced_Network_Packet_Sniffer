
# Enhanced Network Packet Sniffer

## Description
Enhanced Network Packet Sniffer is a Python-based tool with a graphical user interface (GUI) for real-time network packet capture and analysis. It detects SYN flood attacks by monitoring TCP packets, sends alert emails when attacks are detected, and logs suspicious activities into an SQLite database for further analysis.

---

## Features
- Real-time packet sniffing using Scapy
- Detection of SYN flood attacks based on customizable thresholds
- Email alerts for detected attacks via SMTP
- Logging of packet data and alerts to an SQLite database
- Simple Tkinter GUI to start/stop sniffing and view logs live

---

## Prerequisites
- Python 3.8 or higher
- [Scapy](https://scapy.net/)
- [python-dotenv](https://pypi.org/project/python-dotenv/) (for managing environment variables)
- SQLite3 (optional, for inspecting database)
- Access to an SMTP email account for sending alerts (e.g., Gmail with app passwords enabled)

---

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/enhanced-network-packet-sniffer.git
   cd enhanced-network-packet-sniffer
````

2. **Install required Python packages:**

   ```bash
   pip install -r requirements.txt
   ```

   Or manually:

   ```bash
   pip install scapy python-dotenv
   ```

3. **Set up environment variables:**

   Create a `.env` file in the project root with your email credentials:

   ```env
   EMAIL_ADDRESS=your_email@example.com
   EMAIL_PASSWORD=your_email_password_or_app_password
   RECEIVER_EMAIL=receiver_email@example.com
   ```

   > **Security tip:** Never hardcode passwords in source code.

---

## Usage

Run the sniffer GUI:

```bash
python src/sniffer_gui.py
```

* Click **Start Sniffing** to begin capturing packets.
* Click **Stop Sniffing** to stop.
* Packet summaries and alerts will be displayed in the GUI output box.
* If a SYN flood attack is detected, an email alert is sent and the event is logged to the database.

---

## Database

* Alerts and relevant packet info are logged in `attacks.db` (SQLite database).
* To inspect the database, use the SQLite CLI or GUI tools such as [DB Browser for SQLite](https://sqlitebrowser.org/).

Example CLI command to view alerts table:

```bash
sqlite3 attacks.db
sqlite> SELECT * FROM alerts;
 

## Configuration

* Adjust the SYN flood detection threshold and alert interval in `sniffer_gui.py`:

  ```python
  attack_threshold = 100  # Number of SYN packets from same IP to trigger alert
  alert_interval = 60     # Minimum seconds between alerts
  ```
* Modify email settings via your `.env` file.

---

## Troubleshooting

* **Email sending fails:**

  * Verify SMTP credentials and app password if using Gmail.
  * Check network/firewall restrictions.
* **Packet sniffing fails:**

  * Run script with administrator/root privileges.
  * Ensure Scapy is properly installed.
* **SQLite commands not found:**

  * Install SQLite CLI or use GUI tools.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

* [Scapy](https://scapy.net/) — powerful packet manipulation library
* [Tkinter](https://docs.python.org/3/library/tkinter.html) — Python GUI toolkit
* Inspiration and guidance from various network security tutorials and open-source projects.

---

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to open an issue or submit a pull request.

---

m
