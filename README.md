# Importeer het gedownloade script
Import-Module "$env:TEMP\Invoke-PSImage.ps1"

# Verstop het bericht in de afbeelding
Invoke-PSImage -Image C:\temp\mooie_plaat.png -Data C:\temp\StoerBericht.txt -Out C:\temp\geheime_afbeelding.png -PassThru