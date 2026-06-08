On Error Resume Next
Set player = CreateObject("WMPlayer.OCX")
If Err.Number <> 0 Then
    MsgBox "WMPlayer.OCX bestaat niet op dit systeem. Fout: " & Err.Description
    WScript.Quit
End If

player.URL = "C:\ProgramData\ronjans.mp3"
player.controls.play

WScript.Sleep 3000

If player.playState = 1 Then
    MsgBox "Bestand is klaar met afspelen."
Else
    MsgBox "PlayState = " & player.playState & " (3 = spelen, 1 = gestopt)"
End If