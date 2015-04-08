# MacAppStoreRedist
Script to parse the Mac App Store Manifest.plist and hard link and rename any current downloads from the Mac App Store for redistribution. Maybe later for Munki or Casper import.

This shell script searches for the Mac App Store folder and creates hard links to any pkg and also creates a matching text file with details of the pkg.

I'm hoping to automate this process via a launchd "watch" process that watches the AppStores manifest.plist for changes and then kicks off the script.

I'd like to eventually have it wait until the size of the pkg is correct (downloaded) and then work on the pkg and flatten it/repackage it if needed.

It creates and saves to "/tmp/appstorerepkg" for now to be worked on so will be deleted upon reboot. 
No need for sudo.

![Screenshot]\(http://i.imgur.com/DgxvpQk.png) 

References:

https://derflounder.wordpress.com/2013/08/22/downloading-apples-server-app-installer-package/
https://jamfnation.jamfsoftware.com/discussion.html?id=5591

May need to add this to the end of the script once filesize = 100% downloaded:
pkgutil --expand mzm.exgoawfi.pkg appstore.pkg 
pkgutil --flatten appstore.pkg/whatever.pkg whatever.pkg 
ref:https://jamfnation.jamfsoftware.com/discussion.html?id=5591

Also:
https://groups.google.com/forum/#!topic/munki-dev/XvrAXe7J5oE
https://groups.google.com/forum/#!msg/munki-dev/XvrAXe7J5oE/vm4s3Xd0Qw4J
https://groups.google.com/forum/#!searchin/macenterprise/appstore/macenterprise/Vs3sAalXNzI/mIUN-GtJMc8J
https://groups.google.com/forum/#!searchin/macenterprise/appstore/macenterprise/nbL6HrMRG-0/m9pzYYxYb1UJ
https://groups.google.com/forum/#!searchin/macenterprise/appstore/macenterprise/Y9cej17S_ag/mFqLWni33JYJ
