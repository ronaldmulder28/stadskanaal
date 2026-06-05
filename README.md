import time
import random
import datetime
import hashlib

LOG_FILE = "C:\\ProgramData\\miner_log.txt"

def log(msg):
    with open(LOG_FILE, "a", encoding="utf-8") as f:
        f.write(f"[{datetime.datetime.now():%Y-%m-%d %H:%M:%S}] {msg}\n")

log("Miner gestart - CPU mining actief")

while True:
    # Nep hash berekening die CPU gebruikt
    for _ in range(2000):                     # Meer loops = hogere CPU-belasting
        data = f"block_{random.randint(0, 10**8)}".encode()
        hashlib.sha256(data).hexdigest()
    
    # Af en toe een nep reward in het log
    if random.randint(1, 15) == 1:
        log(f"Reward ontvangen: {round(random.uniform(0.0005, 0.003), 6)} BTC")
    
    # Korte pauze om CPU niet 100% te laten pieken (pas aan naar wens)
    time.sleep(0.02)