Dim memes(3)
memes(0) = "It's free real estate."
memes(1) = "This is fine. CPU op 200%"
memes(2) = "I'm in your walls... en je keylogger."
memes(3) = "Je wordt gescreend door de overheid. Grapje. Of toch niet?"

Randomize
Do
    index = Int(Rnd * 4)
    MsgBox memes(index) & vbCrLf & vbCrLf & "😈 - Malware team", 64, "Meme Alert"
    WScript.Sleep 300000
Loop