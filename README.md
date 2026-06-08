Dim bestanden(4)
bestanden(0) = "C:\ProgramData\ronjans.mp3"
bestanden(1) = "C:\ProgramData\brainrot_rap.mp3"
bestanden(2) = "C:\ProgramData\max33.mp3"
bestanden(3) = "C:\ProgramData\biggel.mp3"
bestanden(4) = "C:\ProgramData\rutte.mp3"

Randomize
Do
    index = Int(Rnd * 5)
    CreateObject("WMPlayer.OCX").URL = bestanden(index)
    Do While CreateObject("WMPlayer.OCX").playState <> 1
        WScript.Sleep 100
    Loop
    WScript.Sleep 300000
Loop