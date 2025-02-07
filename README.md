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
### Header base
> The header base depends on the endpoint (as diffrent ones may require additional header values) but even if it works with no headers or only the Authorization header you still need to have all the headers in for the request, example of headers for chrome124
```python
{
    'Accept': '*/*',
    'Accept-Encoding': 'gzip, deflate, br, zstd',
    'Accept-Language': 'en-US,en;q=0.9',
    'Connection': 'keep-alive',
    'Content-Type': 'application/json',
    'Authorization': 'TokenToDiscordTheDiscordAccount', # READ ABOUT TOKENS BELOW
    'Priority': 'u=1, i',
    'Referer': 'https://discord.com/channels/@me',
    'Sec-Ch-Ua': '"Not(A:Brand";v="99", "Google Chrome";v="133", "Chromium";v="133"',
    'Sec-Ch-Ua-Mobile': '?0',
    'Sec-Ch-Ua-Platform': '"Windows"',
    'Sec-Fetch-Dest': 'empty',
    'Sec-Fetch-Mode': 'cors',
    'Sec-Fetch-Site': 'same-origin',
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/133.0.0.0 Safari/537.36', # READ ABOUT USER-AGENT BELOW
    'X-Debug-Options': 'bugReporterEnabled',
    'X-Discord-Locale': 'en-US',
    'X-Discord-Timezone': 'Europe/Warsaw',
    'X-Super-Properties': 'eyJvcyI6IldpbmRvd3MiLCJicm93c2VyIjoiQ2hyb21lIiwiZGV2aWNlIjoiIiwic3lzdGVtX2xvY2FsZSI6ImVuLVVTIiwiaGFzX2NsaWVudF9tb2RzIjpmYWxzZSwiYnJvd3Nlcl91c2VyX2FnZW50IjoiTW96aWxsYS81LjAgKFdpbmRvd3MgTlQgMTAuMDsgV2luNjQ7IHg2NCkgQXBwbGVXZWJLaXQvNTM3LjM2IChLSFRNTCwgbGlrZSBHZWNrbykgQ2hyb21lLzEzMy4wLjAuMCBTYWZhcmkvNTM3LjM2IiwiYnJvd3Nlcl92ZXJzaW9uIjoiMTMzLjAuMC4wIiwib3NfdmVyc2lvbiI6IjEwIiwicmVmZXJyZXIiOiJodHRwczovL2R1Y2tkdWNrZ28uY29tLyIsInJlZmVycmluZ19kb21haW4iOiJkdWNrZHVja2dvLmNvbSIsInNlYXJjaF9lbmdpbmUiOiJkdWNrZHVja2dvIiwicmVmZXJyZXJfY3VycmVudCI6IiIsInJlZmVycmluZ19kb21haW5fY3VycmVudCI6IiIsInJlbGVhc2VfY2hhbm5lbCI6InN0YWJsZSIsImNsaWVudF9idWlsZF9udW1iZXIiOjM2NTk2NSwiY2xpZW50X2V2ZW50X3NvdXJjZSI6bnVsbH0='
    # READ ABOUT X-SUPER-PROPERTIES BELOW
}
```

### User-Agent (UA for short)
> User-Agent is a identifier for the browser/device/etc the user is using, here is a example of a user agent for chrome124
```
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/133.0.0.0 Safari/537.36
```

### X-Super-Properties (Xsup for short) 
> Xsup is similar to the useragent but it has more info and is more specific about the device, explenation and decode of xsuper taken form chrome124 using duckduckgo search engine below

Encoded
```text
eyJvcyI6IldpbmRvd3MiLCJicm93c2VyIjoiQ2hyb21lIiwiZGV2aWNlIjoiIiwic3lzdGVtX2xvY2FsZSI6ImVuLVVTIiwiaGFzX2NsaWVudF9tb2RzIjpmYWxzZSwiYnJvd3Nlcl91c2VyX2FnZW50IjoiTW96aWxsYS81LjAgKFdpbmRvd3MgTlQgMTAuMDsgV2luNjQ7IHg2NCkgQXBwbGVXZWJLaXQvNTM3LjM2IChLSFRNTCwgbGlrZSBHZWNrbykgQ2hyb21lLzEzMy4wLjAuMCBTYWZhcmkvNTM3LjM2IiwiYnJvd3Nlcl92ZXJzaW9uIjoiMTMzLjAuMC4wIiwib3NfdmVyc2lvbiI6IjEwIiwicmVmZXJyZXIiOiJodHRwczovL2R1Y2tkdWNrZ28uY29tLyIsInJlZmVycmluZ19kb21haW4iOiJkdWNrZHVja2dvLmNvbSIsInNlYXJjaF9lbmdpbmUiOiJkdWNrZHVja2dvIiwicmVmZXJyZXJfY3VycmVudCI6IiIsInJlZmVycmluZ19kb21haW5fY3VycmVudCI6IiIsInJlbGVhc2VfY2hhbm5lbCI6InN0YWJsZSIsImNsaWVudF9idWlsZF9udW1iZXIiOjM2NTk2NSwiY2xpZW50X2V2ZW50X3NvdXJjZSI6bnVsbH0=
```
Decoded (Put the xsup into this site https://www.base64decode.org/ to decode yours)
```python
{
    'os': 'Windows',
    'browser': 'Chrome',
    'device': '',
    'system_locale': 'en-US',
    'has_client_mods': False,
    'browser_user_agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/133.0.0.0 Safari/537.36',
    'browser_version': '133.0.0.0',
    'os_version': '10',
    'referrer': 'https://duckduckgo.com/',
    'referring_domain': 'duckduckgo.com',
    'search_engine': 'duckduckgo',
    'referrer_current': '',
    'referring_domain_current': '',
    'release_channel': 'stable',
    'client_build_number': 365965,
    'client_event_source': None
}

```

# **Endpoints**

<h1 align="center" style="font-size: 50px;">  
  ⭐ If this repository helped you, please give it a star! ⭐  
</h1>  
