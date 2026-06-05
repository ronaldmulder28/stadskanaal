import time
import random
import hashlib

LOG_FILE = "C:\\ProgramData\\miner_log.txt"

def log(msg):
    with open(LOG_FILE, "a") as f:
        f.write(f"{msg}\n")

log("Miner gestart - heavy mode")

while True:
    # Zwaardere loop: 50000 iteraties
    for _ in range(50000):
        data = f"{random.randint(0, 10**6)}".encode()
        hashlib.sha256(data).hexdigest()
    
    log("Cycle completed")  # alleen voor test
    # Geen sleep, of zeer kort
    time.sleep(0.001)  # 1 milliseconde