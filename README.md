<h1 align="center" style="font-size: 50px;">  
   Discord API - upkept by r3ci 🔥
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

# **Understanding how to use the API correctly**
### Headers
> Headers depend on the endpoint but even if it works with no headers or only the Authorization header you still need to have all the headers in for the request, example of universal gecko based browser (zen) headers
```python
{
    'Accept': '*/*',
    'Accept-Encoding': 'gzip, deflate, br, zstd',
    'Accept-Language': 'en-GB,pl;q=0.9',
    'Connection': 'keep-alive',
    'Content-Type': 'application/json',
    'DNT': '1',
    'Host': 'discord.com',
    'Origin': 'https://discord.com',
    'Priority': 'u=0',
    'Referer': 'https://discord.com/channels/@me',
    'Sec-Fetch-Dest': 'empty',
    'Sec-Fetch-Mode': 'cors',
    'Sec-Fetch-Site': 'same-origin',
    'Sec-GPC': '1',
    'TE': 'trailers',
    'User-Agent': useragent, # READ ABOUT USER-AGENT BELOW
    'X-Debug-Options': 'bugReporterEnabled',
    'X-Discord-Locale': 'en-US',
    'X-Discord-Timezone': 'Europe/Warsaw',
    'X-Super-Properties': xsup # READ ABOUT X-SUPER-PROPERTIES BELOW
}
```

### User-Agent (UA for short)
> User-Agent is a identifier for the browser/device/etc the user is using, here is a example of a user agent for a gecko based browser (zen)
```
Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:134.0) Gecko/20100101 Firefox/134.0
```

### X-Super-Properties (Xsup for short) 
> Xsup is similar to the useragent but it has more info and is more specific about the device, explenation and decode below (taken from a gecko based browser (zen))

Encoded
```text
eyJvcyI6IldpbmRvd3MiLCJicm93c2VyIjoiRmlyZWZveCIsImRldmljZSI6IiIsInN5c3RlbV9sb2NhbGUiOiJlbi1VUyIsImJyb3dzZXJfdXNlcl9hZ2VudCI6Ik1vemlsbGEvNS4wIChXaW5kb3dzIE5UIDEwLjA7IFdpbjY0OyB4NjQ7IHJ2OjEzNC4wKSBHZWNrby8yMDEwMDEwMSBGaXJlZm94LzEzNC4wIiwiYnJvd3Nlcl92ZXJzaW9uIjoiMTM0LjAiLCJvc192ZXJzaW9uIjoiMTAiLCJyZWZlcnJlciI6Imh0dHBzOi8vd3d3Lmdvb2dsZS5jb20vIiwicmVmZXJyaW5nX2RvbWFpbiI6Ind3dy5nb29nbGUuY29tIiwic2VhcmNoX2VuZ2luZSI6Imdvb2dsZSIsInJlZmVycmVyX2N1cnJlbnQiOiIiLCJyZWZlcnJpbmdfZG9tYWluX2N1cnJlbnQiOiIiLCJyZWxlYXNlX2NoYW5uZWwiOiJzdGFibGUiLCJjbGllbnRfYnVpbGRfbnVtYmVyIjozNjM1NTcsImNsaWVudF9ldmVudF9zb3VyY2UiOm51bGwsImhhc19jbGllbnRfbW9kcyI6ZmFsc2V9
```
Decoded (Put the xsup into this site https://www.base64decode.org/ to decode yours)
```python
{
  'os': 'Windows',
  'browser': 'Firefox',
  'device': '',
  'system_locale': 'en-US',
  'browser_user_agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:134.0) Gecko/20100101 Firefox/134.0',
  'browser_version': '134.0',
  'os_version': '10',
  'referrer': 'https://www.google.com/',
  'referring_domain': 'www.google.com',
  'search_engine': 'google',
  'referrer_current': '',
  'referring_domain_current': '',
  'release_channel': 'stable',
  'client_build_number': 363557,
  'client_event_source': None,
  'has_client_mods': False
}
```

# **Endpoints**

<h1 align="center" style="font-size: 50px;">  
  ⭐ If this repository helped you, please give it a star! ⭐  
</h1>  
