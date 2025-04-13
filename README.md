# MAL-012: Reflected Cross-Site Scripting in Admin Console leading to Remote Code Execution in Payara Server

A reflected Cross Site Scripting (XSS) attack was found in the Payara Admin Console. By convincing an admin user to access the malicious URL and click the “Choose File” button, an attacker can run arbitrary JavaScript code, impersonating the user and leverage admin functionalities for malicious purposes.

Because the XSS is in the Payara Admin Console, an attacker can use this to perform arbitrary requests that leverage admin features (e.g. H2 Connection Strings, Web Application Deployment, etc.) in order to obtain Remote Code Execution (RCE).

### Why no CVE?

Could not be bothered to request a CVE for a Reflected XSS from 2022, but, as I am rather fond of the async "fetch" based JS script leading to RCE and the " target="_blank" " HTML trick, I have decided to post this writeup. Hope you find it useful/entertaining.

### Requirements:

This vulnerability requires:
<br/>
- Convincing a legitimate Payara Server admin user to access the malicious URL and click the "Choose File" button

### Proof Of Concept:

More details and the exploitation process can be found in this [PDF](https://github.com/mbadanoiu/MAL-012/blob/main/Payara%20-%20MAL-012.pdf).

### Timeline:

- H2 RCE was reported to security@payara.fish on 22-Mar-2022
- RCE was considered a non-issue as it occurs post-authentication in the admin console that contains other core functionalities such as deploying WARs
- Found and reported the Reflected XSS in the admin console that can be leveraged to perform the RCE on 25-Mar-2022
- Sent last email on 01-Apr-2022, no communication has been received since then
- Publicly disclosed the vulnerability on 13-Apr-2025
