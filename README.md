import time
import hashlib
import random

LOG_FILE = "C:\\ProgramData\\miner_log.txt"

while True:
    # Doe wat rekenwerk (hash berekenen)
    nonce = 0
    while nonce < 10000:   # 10.000 iteraties per cyclus
        data = f"{nonce}{random.random()}".encode()
        hash_result = hashlib.sha256(data).hexdigest()
        nonce += 1

    # Schrijf een logregel
    with open(LOG_FILE, "a") as f:
        f.write(f"{time.ctime()} - Mijncyclus voltooid\n")

    # Korte pauze om de laptop niet helemaal vast te laten lopen
    time.sleep(0.5)