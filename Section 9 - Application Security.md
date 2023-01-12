# 9.2 Web Browser Security
- Ensure that your web browser is patched, but don't adopt the newest browser immediately.
	- Look at reports of bugs and other problems
- #### Implement policies
	- Create and implement browsing policies
		- Block ads, use content filters, etc.
- #### Train users
	- i.e. always go the HTTPS URL, using keyboard shortcuts to close browsers to avoid clicking on pop-ups
- #### Use proxy / content filters 
	- Proxies cache the website to reduce requests and bandwidth usage
	- Content filters can be used to blacklist specific sites or entire categories of sites
- #### Prevent malicious code
	- Configure your machine to prevent ActiveX controls, Java/JavaScript, Flash, and other active content

# 9.3 Web Browser Concerns
- #### Cookies
	- Text files stored on a local machine to store information like browsing habits, credentials, etc.
	- Used for authentication, session tracking, shopping carts, and many more purposes
	- **Tracking cookies** are used by spyware to gather details on you. 
		- Learn what websites you visit, looking at what you put in your cart, etc. to advertise to "your tastes".
		- Many companies are moving away from local tracking cookies to server-side tracking, allowing users to block cookies, yet still monitor these habits
- #### Locally Shared Object (LSO)
	- Also known as Flash cookies, they are stored in your Windows user profile under the Flash folder instead of AppData