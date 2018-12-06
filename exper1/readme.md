# Experiment 1

Notes, this is a master, don't run it on this, make a copy and play with that

This mimic I copy a directory to my laptop, go away, work on it, and now want to merge it back in
- dir1 - is the original with 4 files, a.txt, b.txt, c.txt, d.txt each with one letter of data
- dir2 - has changes in it b.txt has been modified, d.txt has been deleted, and an e.txt has been added


# diff output
- using bash from this directory `diff -brief dir1 dir2` yields the following output:
```
$ diff -brief dir1 dir2
/usr/bin/diff: conflicting output style options
/usr/bin/diff: Try '/usr/bin/diff --help' for more information.
```
or non brief
```
$ diff dir1 dir2
diff dir1/b.txt dir2/b.txt
1c1
< b
---
> bb
Only in dir1: d.txt
Only in dir2: e.txt
```

# robocopy 
- A simple robocopy will bring things up to date

```
D:\transfer\roboexper\exper1>robocopy dir2 dir1 /s

-------------------------------------------------------------------------------
   ROBOCOPY     ::     Robust File Copy for Windows
-------------------------------------------------------------------------------

  Started : Thursday, 6 December, 2018 09:55:16
   Source : D:\transfer\roboexper\exper1\dir2\
     Dest : D:\transfer\roboexper\exper1\dir1\

    Files : *.*

  Options : *.* /S /DCOPY:DA /COPY:DAT /R:1000000 /W:30

------------------------------------------------------------------------------

                           4    D:\transfer\roboexper\exper1\dir2\
          *EXTRA File                  3        d.txt
100%        Newer                      4        b.txt
100%        New File                   3        e.txt

------------------------------------------------------------------------------

               Total    Copied   Skipped  Mismatch    FAILED    Extras
    Dirs :         1         0         1         0         0         0
   Files :         4         2         2         0         0         1
   Bytes :        13         7         6         0         0         3
   Times :   0:00:00   0:00:00                       0:00:00   0:00:00


   Speed :                3500 Bytes/sec.
   Speed :               0.200 MegaBytes/min.
   Ended : Thursday, 6 December, 2018 09:55:16


D:\transfer\roboexper\exper1>diff dir1 dir2
Only in dir1: d.txt
```

