Dim bestanden(4)
bestanden(0) = "C:\ProgramData\ronjans.mp3"
bestanden(1) = "C:\ProgramData\brainrot_rap.mp3"
bestanden(2) = "C:\ProgramData\max33.mp3"
bestanden(3) = "C:\ProgramData\Freaky_fish.mp3"
bestanden(4) = "C:\ProgramData\hemel_meneer.mp3"

Set player = CreateObject("WMPlayer.OCX")
Randomize
Do
    index = Int(Rnd * 5)
    player.URL = bestanden(index)
    player.controls.play
    Do While player.playState <> 1
        WScript.Sleep 100
    Loop
    WScript.Sleep 300000   ' 5 minuten
Loop