<h1 align="center" style="font-size: 50px;">  
   Discord API - upkept by r3ci 🔥 (More stars ⭐ = more updates)
</h1>  

> [!NOTE]  
> This repository is not focused on bypassing discord security in any way just the endpoints and usage
>
> **Last Updated:** 05/02/2025 (day/month/year)  
> 
> **Quick API Information**  
> - **Base URL:** `https://discord.com/api/v9`  
> - **Version:** `v9`

# **Table of Contents**  
- Understanding how to use the API correctly
  - Headers
  - User-Agent
- Endpoints

# **Headers**
> [!NOTE]  
> All headers shown here are based from a desktop chromium browser (google chrome) headers on geckobased browsers (firefox, etc) will be diffrent

### Header base
> The header base depends on the endpoint (as diffrent ones may require additional header values) but even if it works with no headers or only the Authorization header you still need to have all the headers in for the request, example of headers for chrome133
```python
{
    'Accept': '*/*',
    'Accept-Encoding': 'gzip, deflate, br, zstd',
    'Accept-Language': 'en-US,en;q=0.9', # Language you want the response in (locale value in cookies and X-Discord-Locale also matter)
    'Connection': 'keep-alive', # Keeps the connection open instead of closing
    'Content-Type': 'application/json', # Format of the json 
    'Authorization': 'TokenToDiscordTheDiscordAccount', # READ ABOUT TOKENS BELOW
    'Priority': 'u=1, i',
    'Referer': 'https://discord.com/channels/@me', # From wheare the request was made
    'Sec-Ch-Ua': '"Not(A:Brand";v="99", "Google Chrome";v="133", "Chromium";v="133"',
    'Sec-Ch-Ua-Mobile': '?0', # ?0 Means that is is not a mobile device
    'Sec-Ch-Ua-Platform': '"Windows"', # The OS
    'Sec-Fetch-Dest': 'empty',
    'Sec-Fetch-Mode': 'cors',
    'Sec-Fetch-Site': 'same-origin', # Means the requiest got sent from the same orgin so from discord to discord
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/133.0.0.0 Safari/537.36', # Explained below
    'X-Debug-Options': 'bugReporterEnabled', 
    'X-Discord-Locale': 'en-US', # Launguage (same as with accept language)
    'X-Discord-Timezone': 'Europe/Warsaw', # Timezone
    'X-Super-Properties': 'eyJvcyI6IldpbmRvd3MiLCJicm93c2VyIjoiQ2hyb21lIiwiZGV2aWNlIjoiIiwic3lzdGVtX2xvY2FsZSI6ImVuLVVTIiwiaGFzX2NsaWVudF9tb2RzIjpmYWxzZSwiYnJvd3Nlcl91c2VyX2FnZW50IjoiTW96aWxsYS81LjAgKFdpbmRvd3MgTlQgMTAuMDsgV2luNjQ7IHg2NCkgQXBwbGVXZWJLaXQvNTM3LjM2IChLSFRNTCwgbGlrZSBHZWNrbykgQ2hyb21lLzEzMy4wLjAuMCBTYWZhcmkvNTM3LjM2IiwiYnJvd3Nlcl92ZXJzaW9uIjoiMTMzLjAuMC4wIiwib3NfdmVyc2lvbiI6IjEwIiwicmVmZXJyZXIiOiJodHRwczovL2R1Y2tkdWNrZ28uY29tLyIsInJlZmVycmluZ19kb21haW4iOiJkdWNrZHVja2dvLmNvbSIsInNlYXJjaF9lbmdpbmUiOiJkdWNrZHVja2dvIiwicmVmZXJyZXJfY3VycmVudCI6IiIsInJlZmVycmluZ19kb21haW5fY3VycmVudCI6IiIsInJlbGVhc2VfY2hhbm5lbCI6InN0YWJsZSIsImNsaWVudF9idWlsZF9udW1iZXIiOjM2NTk2NSwiY2xpZW50X2V2ZW50X3NvdXJjZSI6bnVsbH0='
    # READ ABOUT X-SUPER-PROPERTIES BELOW
}
```

### User-Agent (UA for short)
> User-Agent is a identifier for the browser/device/etc the user is using
> 
> **Explenation for diffrent values**  
> - **Mozilla/5.0** `Pretending to be Mozilla for compatibilty and its version`
> - **Windows NT 10.0** `The OS version`
> - **Win64; x64** `OS architecture`
> - **AppleWebKit/537.36** `Rendering engine and its version`
> - **(KHTML, like Gecko)** `Rendering engines`
> - **Chrome/133.0.0.0** `Browser name and its version`
> - **Safari/537.36** `Pretending to be safari for compatibilty and its version`
> 
> Example of chrome133 user agent
```
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/133.0.0.0 Safari/537.36
```

### X-Super-Properties (Xsup for short) 
> Xsup is similar to the useragent but it has more info and is more specific about the device, explenation and decode of xsuper taken form chrome133 using duckduckgo search engine below

Encoded
```text
eyJvcyI6IldpbmRvd3MiLCJicm93c2VyIjoiQ2hyb21lIiwiZGV2aWNlIjoiIiwic3lzdGVtX2xvY2FsZSI6ImVuLVVTIiwiaGFzX2NsaWVudF9tb2RzIjpmYWxzZSwiYnJvd3Nlcl91c2VyX2FnZW50IjoiTW96aWxsYS81LjAgKFdpbmRvd3MgTlQgMTAuMDsgV2luNjQ7IHg2NCkgQXBwbGVXZWJLaXQvNTM3LjM2IChLSFRNTCwgbGlrZSBHZWNrbykgQ2hyb21lLzEzMy4wLjAuMCBTYWZhcmkvNTM3LjM2IiwiYnJvd3Nlcl92ZXJzaW9uIjoiMTMzLjAuMC4wIiwib3NfdmVyc2lvbiI6IjEwIiwicmVmZXJyZXIiOiJodHRwczovL2R1Y2tkdWNrZ28uY29tLyIsInJlZmVycmluZ19kb21haW4iOiJkdWNrZHVja2dvLmNvbSIsInNlYXJjaF9lbmdpbmUiOiJkdWNrZHVja2dvIiwicmVmZXJyZXJfY3VycmVudCI6IiIsInJlZmVycmluZ19kb21haW5fY3VycmVudCI6IiIsInJlbGVhc2VfY2hhbm5lbCI6InN0YWJsZSIsImNsaWVudF9idWlsZF9udW1iZXIiOjM2NTk2NSwiY2xpZW50X2V2ZW50X3NvdXJjZSI6bnVsbH0=
```
Decoded (Put the xsup into this site https://www.base64decode.org/ to decode yours)
```python
{
    'os': 'Windows', # Os name
    'browser': 'Chrome', # Browser name
    'device': '', # Device type 
    'system_locale': 'en-US', # Locale of the system
    'has_client_mods': False, # If client has mods
    'browser_user_agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/133.0.0.0 Safari/537.36', # Useragent fo the browser
    'browser_version': '133.0.0.0', # Version of the browser
    'os_version': '10', # Version of the OS
    'referrer': 'https://duckduckgo.com/', # Reffering site
    'referring_domain': 'duckduckgo.com', # Domain of the reffering site
    'search_engine': 'duckduckgo', # Search engine
    'referrer_current': '', # Current reffering domain
    'referring_domain_current': '', # Reffering domain
    'release_channel': 'stable', # Relaese channel
    'client_build_number': 365965, # Client build number
    'client_event_source': None # Event source
}

```

# **Endpoints**

<h1 align="center" style="font-size: 50px;">  
  ⭐ If this repository helped you, please give it a star! ⭐  
</h1>  
