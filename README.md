import time
import hashlib
import os
import random

LOG_FILE = "C:\\ProgramData\\miner_log.txt"
PID_FILE = "C:\\ProgramData\\miner.pid"

def mine():
    """Doe nep-mining met echte CPU-belasting."""
    nonce = 0
    while True:
        # Simuleer hashing (dit kost CPU)
        data = f"{nonce}{random.random()}".encode()
        hash_result = hashlib.sha256(data).hexdigest()
        
        # Log af en toe een regel (elke 1000 iteraties)
        if nonce % 1000 == 0:
            with open(LOG_FILE, "a") as f:
                f.write(f"{time.ctime()} - Hash: {hash_result[:16]}... nonce={nonce}\n")
        
        nonce += 1
        
        # Optioneel: even pauzeren om de CPU niet 100% te laten pieken
        # Pas dit aan: 0.01 = lichte belasting, 0.001 = zware belasting
        time.sleep(0.001)   # <-- pas hier aan voor meer/minder CPU

if __name__ == "__main__":
    with open(PID_FILE, "w") as f:
        f.write(str(os.getpid()))
    mine()