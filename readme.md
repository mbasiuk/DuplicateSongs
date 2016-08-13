Find dublicates songs in the folder

```powershell
PS C:\Users\MBasiuk\Music> gci | group Length | where Count -gt 1 | sort count -Descending | select -ExpandProperty Group | select name, length
```

    Name                                                                                               Length
    ----                                                                                               ------
    18cb785f054f06 (1).mp3                                                                             3848320
    18cb785f054f06.mp3                                                                                 3848320
    703dcab9cc2ba1.mp3                                                                                 3848320
    6a3ee2537f48ba.mp3                                                                                 8925588
    724817d29e058a.mp3                                                                                 8925588
    619557fab8fed8.mp3                                                                                 9789649
    9a0bed83e4beb9.mp3                                                                                 9789649

Get list of songs that will be deleted:

```powershell
gci | group Length | where Count -gt 1 | % { $_.group | select -Skip 1 }
```

get cound of songs that will be deleted:

```powershell
gci | group Length | where Count -gt 1 | % { $_.group | select -Skip 1 } | measure
```

remove the dublicate songs:

```powershell
PS C:\Users\MBasiuk\Music\Music> gci | group Length | where Count -gt 1 | % { $_.group | select -Skip 1 | ri }
```

In case of error on delete close the player. 
