- 
- apt install python3.12-venv -y
- python3 -m venv venv
- source venv/bin/activate
- pip install -r requirements.txt
- python3 bot.py

SERVICE :

[Unit]
Description=Telegram Bot MyXL
After=network.target

[Service]
# Sebaiknya jangan dijalankan sebagai root.
# Buat user baru (misal: sudo adduser botuser) dan ganti 'root' di bawah.
User=root
Group=root

# Sesuaikan path ini jika direktori proyek Anda bukan di /root
WorkingDirectory=/root

# Perintah untuk menjalankan bot menggunakan python dari venv
# Sesuaikan path jika berbeda
ExecStart=/root/venv/bin/python3 /root/bot.py

# Selalu restart service jika gagal atau berhenti
Restart=always
RestartSec=5s

[Install]
WantedBy=multi-user.target
