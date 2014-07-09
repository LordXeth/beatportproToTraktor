beatportproToTraktor
====================

A utility for converting id3 tags from Beatport Pro into a better format for Traktor's tag importer

Features
--------
+ Sync Release date to a tag Traktor will recognize
+ Sync 'Key' in code form (Open or other) to 'Key Text' so Traktor can search on that field
++ Traktors "Key" (not 'Key Text') field is not a key but a database entry and is not supported
+ Strip old key codes from Comments field

Installation
------------

Before you install the gem, make sure to have taglib installed with header files (and a C++ compiler of course):
+ Debian/Ubuntu: sudo apt-get install libtag1-dev
+ Fedora/RHEL: sudo yum install taglib-devel
+ Brew: brew install taglib
+ MacPorts: sudo port install taglib

Then do:
```
gem install taglib-ruby
```

Execution
---------
Recursively run on directory
```
./tagsync.rb -s <dir>
```

For help
```
./tagsync.rb --help
```


Details
-------
Beatport Pro (and iTunes) writes the id3v2 'Date' field "TDRC" with the Year value only.
It instead writes the fully YYYY-MM-DD value to "TDOR" and "TDRL", "Original Release" and "Release Tine" respecively. 

This script simply copies the values to the TDRC field.

For key, Beatport Pro writes the Open key code to [TKY2] and the musical expression 'ie; fMaj' to [TKEY]
Traktor uses a propietry field for its Key field, but uses [TKEY] for any format the user wants. If you want to be able to search
the key codes, I this script allows that by copying the [TKY2] field into [TKEY].

TODO
----
+ Code clean up (my first ruby project)
+ Add open key in addition to camelot keys in comment cleaner
+ Support key code stripping from Title/Artist fields since Mixed in Key supports writing to there
