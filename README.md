import time
import hashlib

LOG_FILE = "C:\\ProgramData\\miner_log.txt"

counter = 0
while True:
    # Doe een zware berekening: 200.000 SHA256-hashes per cyclus
    for i in range(200000):
        hashlib.sha256(f"{counter}{i}".encode()).hexdigest()
    
    # Log elke cyclus
    with open(LOG_FILE, "a") as f:
        f.write(f"{time.ctime()} - Cycle {counter} completed\n")
    
    counter += 1
    
    # Pas deze slaaptijd aan om CPU te regelen:
    # - lagere waarde = hogere CPU (bijv. 0.00005 = ~80%)
    # - hogere waarde = lagere CPU (bijv. 0.001 = ~20%)
    time.sleep(0.0003)   # Start hiermee: geeft ongeveer 30-40% op een moderne laptop