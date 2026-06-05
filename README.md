import time
import hashlib

LOG_FILE = "C:\\ProgramData\\miner_log.txt"

def mine():
    counter = 0
    while True:
        # Blijven hashen (CPU intensief)
        for i in range(100000):
            hashlib.sha256(f"{counter}{i}".encode()).hexdigest()
        
        # Elke 100.000 iteraties een logregel
        with open(LOG_FILE, "a") as f:
            f.write(f"{time.ctime()} - Cycle {counter} done\n")
        
        counter += 1
        time.sleep(0.0001)  # Kleine pauze, CPU blijft hoog

if __name__ == "__main__":
    mine()