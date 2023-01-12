# 5.1 Securing mobile devices
-  WiFi and Bluetooth are the two protocols that need to be protected.
-  WFi needs to be protected at the highest level, using WPA2, which relies on the AES.
-  To secure bluetooth, you also need to consider the peripherals that connect via this medium. Wired devices are almost always **more secure** than wireless. Check your wireless devices to see if they rely on AES.

# 5.2 Mobile Malware
- Ensure that your device is patched and upated, much like any device / service.
- Moreover, only install apps from official App Stores. Most of these apps are digitally signed. There are instances of malicious apps getting downloaded via Google Play, however.
- Avoid jailbreaking/rooting, custom firmware/ROM

# 5.3 SIM cloning and ID theft
- A Subscriber Identity Module (**SIM**) card is an integrated circuit that securely stores the international mobile subscriber identity (IMSI) number and its related key. This tells the cell towars which device is assigned to each number
- #### SIM Cloning
	- SIM cloning was big on the advent of cell phones, because milking long distance calls meant charging you quite a bit
	- This techniques allows two phones to utilize the same service and allows an attacker to gain access to the phone's data.
	- Social engineering to take control of a phone to bypass 2FA. If an attacker can take your number, they can take any service that's attached to it.

# 5.4/5.5 Bluetooth attacks, mobile device theft
- #### Bluetooth attacks
	- Bluejacking occurs when an attacker is sending unsolicited messages to Bluetooth enabled devices
	- Bluesnarfing is unauthorized from a wireless device over a Bluetooth connection
	- Bluejacking focuses on SENDING, whereas Bluesnarfing is focused on RECEIVING
- #### Mobile device theft
	- Always ensure you have a backup...some data is irreplacable. A phone can be replaced, valuable photos, data, etc. usually cannot.
	- Don't try to recover your device alone if it's stolen
	- Take advantage of remote locking features, requiring a pin before accessing services on a mobile device.
	- Also, remote wipes can conduct a full disk wipe on a mobile device.

# 5.6/5.7/5.8 Security of apps, BYOD, Hardening mobile devices
- Essentially, only download signed apps from official stores (App Store, Google Play), update and patch phone consistently, and going to secure versions of websites. Using https URLs ensures a Transport Layer Security (TLS) between your device and the website. This prevents man-in-the-middle (MITM) attacks. 
- Using mobile device management (MDM), or a centralized software solution that allows sysAdmins to create and enforce policies across its mobile devices.
- Ideally, turn off location access to apps that don't really need it. 
- This is exacerbated with Geotagging, or embedded geographic locations on certain media such as images on Instagram or Facebook.
- #### BYOD
	- BYOD (Bring Your Own Device) is accompanied with security risks, but is obviously better for the immediate bottom line. A company doesn't have to buy laptops, phones, etc. for everyone
	- Companies can enact storage segmentation, creating a clear line between user and workplace data on a user's device. This can be accomplished an a clear technical or administrative way.
	- MDM can be used to enforce these limitiations/policies, as well.
	- CYOD (choose your own device) policies can be enacted, too.
# 5.9 Hardening
- Updating your devices
	- Most systems are "hurt" through vulnerabilities found in an prior, unpatched version of the OS on the given machine
- Install anti-virus software
- Training users on proper security and use of their device(s)
- Only install apps on official stores
- Don't jailbreak/root your device(s)
- Only use v2 SIM cards with your device
- Disabling all unnecessary features when they aren't needed
- Use encryption for voice and data 
- Use strong passwords or biometric authentication
- Don't allow BYOD or enforce strong policies if you do
