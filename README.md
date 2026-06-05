Dim objWS, cmd, timestamp, fileName, filePath
Set objWS = CreateObject("WScript.Shell")

' Maak een timestamp voor de bestandsnaam
timestamp = Year(Now) & Right("0" & Month(Now), 2) & Right("0" & Day(Now), 2) & "_" & Right("0" & Hour(Now), 2) & Right("0" & Minute(Now), 2) & Right("0" & Second(Now), 2)

' Bepaal de bestandsnaam en het volledige pad
fileName = "screenshot_" & timestamp & ".png"
filePath = "C:\ProgramData\" & fileName

' Bouw het PowerShell-commando stap voor stap op
cmd = "powershell -Command ""& {"
cmd = cmd & "Add-Type -AssemblyName System.Windows.Forms; "
cmd = cmd & "Add-Type -AssemblyName System.Drawing; "
cmd = cmd & "$vs = [System.Windows.Forms.SystemInformation]::VirtualScreen; "
cmd = cmd & "$bmp = New-Object System.Drawing.Bitmap($vs.Width, $vs.Height); "
cmd = cmd & "$g = [System.Drawing.Graphics]::FromImage($bmp); "
cmd = cmd & "$g.CopyFromScreen($vs.Left, $vs.Top, 0, 0, $bmp.Size); "
cmd = cmd & "$bmp.Save('" & filePath & "'); "
cmd = cmd & "$g.Dispose(); $bmp.Dispose()"
cmd = cmd & "}"""

' Voer het PowerShell-commando uit (onzichtbaar)
objWS.Run cmd, 0, True