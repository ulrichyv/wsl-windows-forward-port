# wsl-windows-forward-port
l'objection est de fusionné  l'address de wls et la machine hote
# active le script sur powershell
execucute la commande
Get-ExecutionPolicy

"tu dois obtenir :Si le résultat n'est pas "RemoteSigned" ou "Unrestricted", cela signifie que la politique d'exécution doit être modifiée. Pour modifier la politique d'exécution, exécutez la commande suivant"
# dans le cas contraire tu execute :
Set-ExecutionPolicy RemoteSigned

# recuperer ton address sur wsl ,avec :
ifconfig ou hostname -i
# À présent, utilisez la commande netsh pour rediriger le port de WSL vers le port de l'hôte
netsh interface portproxy add v4tov4 listenport=[PORT] listenaddress=0.0.0.0 connectport=[PORT] connectaddress=[WSL_IP]
# autisation du part feu

New-NetFirewallRule -DisplayName "WSL2 Port Bridge" -Direction Inbound -Action Allow -Protocol TCP -LocalPort [port list]
