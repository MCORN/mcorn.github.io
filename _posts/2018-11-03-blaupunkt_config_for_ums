Because I couldn't find one ready to go for Universal Media Server, I wrote this one. Not the most efficient since I transcode everything but it works!

```
#----------------------------------------------------------------------------
# Profile for Blaupunkt TVs
# See DefaultRenderer.conf for descriptions of all the available options.
#

RendererName = Blaupunkt TV
RendererIcon = Blaupunkt_TV.png

# ============================================================================
# This renderer has sent the following string/s:
#
# friendlyName=Blaupunkt_TV (74:72:b0:46:7c:3c)
# udn=uuid:41ecd396-1dd2-11b2-9451-7472b0ecfacd
# manufacturer=MStar
# modelName=MStarDMR
# modelNumber=0.0
# modelDescription=MStar Digital Media Renderer
# manufacturerURL=http://www.mstarsemi.com
# modelURL=http://www.mstarsemi.com
# ============================================================================
# http://www.umc-uk.co.uk/instruction-manuals/blaupunkt-brand.php
# https://en.wikipedia.org/wiki/MStar

UpnpDetailsSearch = Blaupunkt_TV|MStarDMR

SeekByTime = exclusive
DLNALocalizationRequired = true
TranscodeVideo = MPEGPS-MPEG2-AC3
KeepAspectRatio = true
MediaInfo = true

# Supported video formats: (MP4_BL_CIF15_AAC_520)
# Couldn't figure out which format worked so transcoding everything to the above format, that does work

# Supported audio formats:
Supported = f:3ga|3g2a        m:audio/3gpp            a:aac-lc|he-aac
Supported = f:adts            m:audio/vnd.dlna.adts   a:aac-lc|he-aac
Supported = f:m4a             m:audio/mp4             a:(?!alac)
Supported = f:mp3             m:audio/mpeg
Supported = f:wma             m:audio/x-ms-wma

```
