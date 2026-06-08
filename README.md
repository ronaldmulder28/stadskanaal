' [SCRIPT VOOR 17 INTERNET MEMES]
' Dit script toont elke 5 minuten een willekeurige meme in een pop-up.

' --- Array met Meme-Teksten ---
Dim memes(16)

memes(0) = "6-7."
memes(1) = "Suczas gegarandeerd."
memes(2) = "Lekker kort, niets meer aan doen."
memes(3) = "AAAAAAAH."
memes(4) = "Nummer 5?! Op je muil, gauw."
memes(5) = "Hatseflats!"
memes(6) = "This is fine. (met CPU op 200%🔥)"
memes(7) = "I'm in your computer, stealin' your keystrokes."
memes(8) = "Task Manager? Ik ken haar niet."
memes(9) = "Je hebt goud? Nee, je hebt een miner."
memes(10) = "It's free real estate."
memes(11) = "I'm in your walls... en je keylogger."
memes(12) = "Ik ben niet lui, ik spaar energie."
memes(13) = "Mijn computer begrijpt me beter dan mijn vrienden."
memes(14) = "Waarom moeilijk doen als het ook ingewikkeld kan?"
memes(15) = "Het leven is geen ponykamp, maar ik wil wel een pony."
memes(16) = "Press any key to continue or any other key to quit."

' --- Willekeurige Kiezer ---
Randomize
Do
    index = Int(Rnd * 17)
    MsgBox memes(index) & vbCrLf & vbCrLf & "😈 - Team Malware", 64, "Meme Alert"
    WScript.Sleep 300000  ' 5 minuten (300.000 milliseconden)
Loop