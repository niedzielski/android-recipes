# Database

### Backup and Restore Database (Debug)
    pkg=com.foo.bar
    db="/data/data/$pkg/databases/baz.db"
    tmpdb=tmp.db
    
    # backup
    adb shell "run-as '$pkg' cat '$db' > '/sdcard/$tmpdb'" &&
    adb pull "/sdcard/$tmpdb"
    
    # restore
    adb push "$tmpdb" /sdcard/ &&
    adb shell "run-as '$pkg' cp '/sdcard/$tmpdb' '$db'"

Note: see "[package is unknown](http://visualgdb.com/KB/?ProblemID=nopkg)" bug.

### Backup and Restore Database (Root)
    pkg=com.foo.bar
    db="/data/data/$pkg/databases/baz.db"
    tmpdb=tmp.db
    
    adb shell su -c "cat '$db' > '/sdcard/$tmpdb'" &&
    adb pull "/sdcard/$tmpdb"
    
    adb push "$tmpdb" /sdcard/ &&
    adb shell su -c "cat '/sdcard/$tmpdb' > '$db'"

### Nice Database Tools
- [sqlitebrowser](http://sqlitebrowser.org/)
