# Snapchat-Memory-Date-Correction
Quick and dirty attempt to use exifTool to correct the creation date for memories downloaded from snapchat

V 0.1 Correctly modify the date on one file. 

Files from macie-k/download-snap-memories (IIRC come in the following format):
YYYY-MM-DD_HH-mm-SS.jpg/mp4

The problem is, those dates and times are all UTC time-stamped. When I mass-download in order to put them on iCloud or Google Photos, they're going to be offset. Nighttime photos will have been taken during the day and viceversa. To make it worse, the offset isn't always the same -- people travel and daylight savings exists.

Luckily, exiftool can help extract more detailed information from the pictures. For example, I have a picture called 2016-07-09_02-56-52.jpg. The Snap app says it was taken on July 8th 2016 at 9:56 pm. Something is missing. Running exiftool, we get 

File Modification Date/Time     : 2016:07:09 02:56:52-07:00

as one of the tags. 
The -07:00 seems to indicate where this picture was taken timezone-wise, relative to UTC. 

