import time
import random
import datetime
import os
import hashlib

LOG_FILE = "C:\\ProgramData\\miner_log.txt"

def current_time():
    return datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")

def log_message(msg):
    with open(LOG_FILE, "a") as f:
        f.write(f"[{current_time()}] {msg}\n")

def mine():
    log_message("Miner gestart. Hashrate: 1250 H/s")
    while True:
        nonce = random.randint(0, 10**8)
        # Simuleer een 'hash berekening' met een fractie van CPU
        attempt_hash = hashlib.sha256(f"block_{nonce}".encode()).hexdigest()[:8]
        log_message(f"[INFO] Hash: {attempt_hash} | Nonce: {nonce}")
        # Nep reward ~ elke 30-90 pogingen
        if random.randint(1, 50) == 1:
            reward = round(random.uniform(0.0001, 0.001), 6)
            log_message(f"[REWARD] +{reward} BTC ontvangen! Totaal: [GESIMULEERD]")
        time.sleep(15)   # Laag CPU-gebruik, maar genoeg voor het gevoel

if __name__ == "__main__":
    try:
        mine()
    except Exception as e:
        log_message(f"FOUT: {e}")