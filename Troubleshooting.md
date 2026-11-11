## 1. Claude Code Cannot Connect to Anthropic (DNS)

Environment: Windows 11, PowerShell, Claude Code (native installer), Claude Pro, mobile hotspot (phone data)

Error:
Unable to connect to Anthropic services
Connection to api.anthropic.com timed out after 10 seconds

Problem:
Running `claude` in the terminal fails at first-run setup, before login.
Test command also fails:
curl.exe -I https://api.anthropic.com
→ curl: (6) Could not resolve host: api.anthropic.com

Cause:
DNS failure: the mobile carrier's DNS (automatic DNS on the hotspot) could not resolve api.anthropic.com
Not a country/region issue and not a Pro plan issue

Solution:
1. Confirm DNS is the cause:
   nslookup api.anthropic.com 1.1.1.1   (returns IPs = carrier DNS is the problem)
2. Test again:
   curl.exe -I https://api.anthropic.com
   → HTTP/1.1 404 Not Found (OK, server is reachable)
3. Run `claude` in powershell or cmd

Note:
- 404 from the curl test is normal; any HTTP response means the connection works
- In PowerShell use `curl.exe`, not `curl` (curl is an alias for Invoke-WebRequest)
- DNS setting is per network: connecting to a new Wi-Fi/hotspot may need the same change
- If DNS change doesn't help: check VPN/proxy, firewall/antivirus, or try another network
- Alternative while terminal is broken: Claude desktop app → </> code view (built-in Claude Code)
---

