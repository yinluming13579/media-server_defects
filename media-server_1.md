Affected Version: media-server 1.0.0 0d60f4d784fe7f19365a5b1fcf6d05c7bc5633fb(the current latest branch)
Vulnerability Description: This vulnerability is a UAF (Use-After-Free) vulnerability discovered in the file /media-server/libsip/src/uac/sip-uac-subscribe.c. It could be maliciously exploited, leading to a denial-of-service attack.
media-server download address:https://github.com/ireader/media-server.git
Defect Location and Description: 
