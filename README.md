# OpenPHD2Guiding_add_delay_between_corrections
OpenPHD2Guiding: Add delay between RA and Dec corrections.
This is for repository: https://github.com/OpenPHDGuiding/phd2

The changes add a checkbox labeled "Delay between RA and Dec correction" to the Guiding page of the Advanced Settings dialog.
When selected, a 1/4 second delay will occur between RA and Dec corrections for each guiding cycle.
Files changed:
    configdialog.h
    guider.cpp
    mount.cpp
    scope.cpp
    scope.h

This change was actually implemented a few years ago, tested numerous times, and has proven quite useful for my particular
mount - an old Celestron CI-700 with an ST-4 port. I just finally got around to submitting this change to OpenPHD2Guiding.

Without the delay, the mount would sometimes act erractically by bursting into a series of occillations
that would ruin the imaging sub-frame. Through trial-and-error, I determined the cause was that if both RA and Dec corrections
were applied, the mount would sometimes interpret the Dec correction period as an extension of the RA period. So, the RA period would
be increased, and the Dec correction would not be applied. This would lead to overshoot, over-correction, and hence occillation.

Question/comments welcome. Please be aware this is my first public "pull request", and I hope I did things right.
