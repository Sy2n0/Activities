# Broken Datasheet

## Description
```
One of my friend sent me an important datasheet to me. But the sheet seems broken. Can you please help me to recover or read the datasheet.
```

<hr>

## Write up
All Microsoft files like Word and Excel are essentially zip files holding a bunch of xml so I just ran ```7z x *.xlsx``` twice and the flag was in ```sharedStrings.xml```

## Flag
```
KCTF{XLSX_Fil3$_4R3_Actually_0n3_Kind_0f_Zip_Fil3}
``` 
