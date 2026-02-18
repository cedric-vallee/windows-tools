# Powershell core

## usage

version beaucoup plus efficace de powershell

## assemblage du package

la taille max d'un package dans github étant de 100 Mo, il a fallu spliter le package en plusieurs parties :
```sh

split -b 60M PowerShell-7.5.4-win-x64.zip PowerShell-7.5.4-win-x64.zip.
```

ensuite pour assembler le package, il faut faire la commande suivante : 
```sh
cat PowerShell-7.5.4-win-x64.zip.* > PowerShell-7.5.4-win-x64.zip
```

