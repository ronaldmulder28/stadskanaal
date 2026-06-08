Dim zinnen(7)
zinnen(0) = "Je toetsenbord wordt nu uitgelezen."
zinnen(1) = "Ik zie alles wat je typt."
zinnen(2) = "De miner draait op volle kracht."
zinnen(3) = "Je computer is van mij. Grapje. Of toch niet?"
zinnen(4) = "Kijk eens naar je CPU-gebruik. Grappig, hè?"
zinnen(5) = "Heb je al een screenshot gezien? Nee? Ik wel."
zinnen(6) = "Je wachtwoord is misschien niet zo veilig als je denkt."
zinnen(7) = "Ik ben een vriendelijke malware. Veel plezier!"

Randomize
Do
    index = Int(Rnd * 8)
    CreateObject("SAPI.SpVoice").Speak zinnen(index)
    WScript.Sleep 300000  ' 5 minuten
Loop