# Auto Start Bitcoind Mainnet On Boot
# /etc/systemd/system/bitcoind_mainnet.service

[Unit]
Description=Bitcoin daemon mainnet
After=network.target

[Service]
#ExecStartPre=/bin/sh -c 'sleep 5'
ExecStart=/usr/local/bin/bitcoind -daemon -conf=/home/pi/.bitcoin/bitcoin.conf -pid=/home/pi/.bitcoin/bitcoind.pid
PIDFile=/home/pi/.bitcoin/bitcoind.pid
User=pi
Group=
Type=forking
KillMode=process
Restart=always
TimeoutSec=360
RestartSec=120

[Install]
WantedBy=multi-user.target
