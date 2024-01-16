Affected Version: media-server 1.0.0 0d60f4d784fe7f19365a5b1fcf6d05c7bc5633fb(the current latest branch)
Vulnerability Description: This vulnerability is a UAF (Use-After-Free) vulnerability discovered in the file /media-server/libsip/src/uac/sip-uac-subscribe.c. It could be maliciously exploited, leading to a denial-of-service attack.
media-server download address:https://github.com/ireader/media-server.git
Defect Location and Description: 
In the file /media-server/libsip/src/uac/sip-uac-subscribe.c, a struct pointer named "subscribe" is defined at line 15. This pointer is passed to the function sip_subscribe_remove at line 41, as shown in the following diagram.
![image](https://github.com/yinluming13579/media-server_defects/blob/main/media-server_1.png)
In the sip_subscribe_remove function, this pointer is passed to the sip_subscribe_release function at line 121, as illustrated in the diagram below.
![image](https://github.com/yinluming13579/media-server_defects/blob/main/media-server_2.png)
In the sip_subscribe_release function, the memory space pointed to by the subscribe pointer is released at line 42, as shown in the diagram below.
![image](https://github.com/yinluming13579/media-server_defects/blob/main/media-server_3.png)
Finally, at line 42, the assert statement uses subscribe->ref when the memory pointed to by subscribe has already been released, thereby creating a post-release usage vulnerability, as shown in the diagram below.
![image](https://github.com/yinluming13579/media-server_defects/blob/main/media-server_4.png)
