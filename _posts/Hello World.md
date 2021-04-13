# Hello World

```powershell
'Hello World'
```

Damit das möglich ist, übernimmt Powershell ein Haufen Arbeit für euch.
In passiert ungefähr das

```powershell
$PSCmdlet.WriteObject('Hello World') | Out-Default | Out-Host
```
Das können wir so nicht in der Shell ausführen, da `$PSCmdlet` nur in Advanced Functions
zur Verfügung steht. Intern benutzt Powershell aber die selbe `.WriteObject()` Methode
um Objekte in die Pipeline zu schreiben. 
In Powershell ist ALLES ein Objekt.
Wir könnten auch mit `Write-Output` explizit in den Output Stream schreiben.

Das wird an `Out-Default`gepiped. Ein Kommando das nach der Formatierung schaut.
Im Falle eines String Objektes, wie hier, muss es nicht weiter formatiert werden 
und kann weitergereicht werden.

`Out-Host` übergibt die Informationen dann an die Host Anwendung.
Dabei ist der Host nicht der Computer sondern die Anwendung die Powershell hostet.
Im klassischen Falle `ConsoleHost`. Heutzutage meistens das `Microsoft Terminal`  
Es gibt aber auch noch viele weitere Host Anwendungen. Für Remote Endpoints, VSCode,
ISE, Administrative Center usw.


```powershell
Function Get-Greeting {
    [CmdletBinding()] # Das macht aus einer Funktion eine Advanced Funktion
    param()
    $PSCmdlet.WriteObject('Hello World') | Out-Default | Out-Host
}
```