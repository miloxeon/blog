---
layout: post
title: Firefox sends data to Google by default. Here's how to prevent it
tags: [privacy]
image: "/images/covers/firefox-privacy.webp"
tldr: about:config → browser.safebrowsing → disable everything
---

The very names “Mozilla” and Firefox browser particularly are perceived as caring about your privacy. While they claim they don’t buy or sell user data directly, there is still some stuff involved under the hood that I consider shady.

![Mozilla in their FAQ claims they don’t buy or sell your data](/blog/images/content/mozilla-business-model-4.webp)

Look! Firefox serves their logo from an address beginning with “chrome”! Are they silently switched to Chromium which [sends your IP to Google on startup](https://www.reddit.com/r/privacy/comments/34tc2f/how_safe_is_chromium_privacy_wise/cqxzhh8?utm_source=share&utm_medium=web2x&context=3)?

![Firefox serves their logo from an address beginning with “chrome”](/blog/images/content/hpcvvjf9iizfyh21vifa.jpg)

# What?

Firefox using `chrome://` somewhere in their browser may be suspicious, but there is something straight up alarming ahead.

According to [Mozilla forum](https://support.mozilla.org/en-US/questions/922449), there is a thing called Google SafeBrowsing that “has been a part of Firefox for a very long time”. This thing is essentially the catalogue of unwanted websites and software that Mozilla is striving to protect you from.

The problem is every website you visit is checked up with Google’s service by the very nature of how the aforementioned protection mechanism works. This may be the huge problem for those who are switching to Firefox trying to escape Google.

Even if Google can’t acquire your IP while performing the check-up (which I doubt), with the sheer amount of data they have [it’s trivial to tie your requests to your identity](https://arstechnica.com/tech-policy/2009/09/your-secrets-live-online-in-databases-of-ruin/).

# The solution

1. Type `about:config` in your address bar. You’ll end up on advanced settings page.
2. Type `browser.safebrowsing` in the search bar on top.
3. You’ll see Google services’ URLs. Replace every single URL with `https://127.0.0.1`. Disable everything you can switching `true` to `false`.

This is how I set things up:

| Parameter                                                                                  | Value                |
| :----------------------------------------------------------------------------------------- | :------------------- |
| browser.safebrowsing.allowOverride                                                         | false                |
| browser.safebrowsing.blockedURIs.enabled                                                   | false                |
| browser.safebrowsing.debug                                                                 | false                |
| browser.safebrowsing.downloads.enabled                                                     | false                |
| browser.safebrowsing.downloads.remote.block_dangerous                                      | false                |
| browser.safebrowsing.downloads.remote.block_dangerous_host                                 | false                |
| browser.safebrowsing.downloads.remote.block_potentially_unwanted                           | false                |
| browser.safebrowsing.downloads.remote.block_uncommon                                       | false                |
| browser.safebrowsing.downloads.remote.enabled                                              | false                |
| browser.safebrowsing.downloads.remote.timeout_ms                                           | 15000                |
| browser.safebrowsing.downloads.remote.url                                                  | https://127.0.0.1    |
| browser.safebrowsing.id                                                                    | null                 |
| browser.safebrowsing.malware.enabled                                                       | false                |
| browser.safebrowsing.passwords.enabled                                                     | false                |
| browser.safebrowsing.phishing.enabled                                                      | false                |
| browser.safebrowsing.prefixset_max_array_size                                              | 524288               |
| browser.safebrowsing.provider.google.advisoryName                                          | Google Safe Browsing |
| browser.safebrowsing.provider.google.advisoryURL                                           | https://127.0.0.1    |
| browser.safebrowsing.provider.google.gethashURL                                            | https://127.0.0.1    |
| browser.safebrowsing.provider.google.lists                                                 | **(empty list)**     |
| browser.safebrowsing.provider.google.pver                                                  | 2.2                  |
| browser.safebrowsing.provider.google.reportMalwareMistakeURL                               | https://127.0.0.1    |
| browser.safebrowsing.provider.google.reportPhishMistakeURL                                 | https://127.0.0.1    |
| browser.safebrowsing.provider.google.reportURL                                             | https://127.0.0.1    |
| browser.safebrowsing.provider.google.updateURL                                             | https://127.0.0.1    |
| browser.safebrowsing.provider.google4.advisoryName                                         | Google Safe Browsing |
| browser.safebrowsing.provider.google4.advisoryURL                                          | https://127.0.0.1    |
| browser.safebrowsing.provider.google4.dataSharing.enabled                                  | false                |
| browser.safebrowsing.provider.google4.dataSharingURL                                       | https://127.0.0.1    |
| browser.safebrowsing.provider.google4.gethashURL                                           | https://127.0.0.1    |
| browser.safebrowsing.provider.google4.lastupdatetime                                       | 1603739550029        |
| browser.safebrowsing.provider.google4.lists                                                | **(empty list)**     |
| browser.safebrowsing.provider.google4.nextupdatetime                                       | 1603741356029        |
| browser.safebrowsing.provider.google4.pver                                                 | 4                    |
| browser.safebrowsing.provider.google4.reportMalwareMistakeURL                              | https://127.0.0.1    |
| browser.safebrowsing.provider.google4.reportPhishMistakeURL                                | https://127.0.0.1    |
| browser.safebrowsing.provider.google4.reportURL                                            | https://127.0.0.1    |
| browser.safebrowsing.provider.google4.updateURL                                            | https://127.0.0.1    |
| browser.safebrowsing.provider.mozilla.gethashURL                                           | https://127.0.0.1    |
| browser.safebrowsing.provider.mozilla.lastupdatetime                                       | 1603739273301        |
| browser.safebrowsing.provider.mozilla.lists                                                | **(empty list)**     |
| browser.safebrowsing.provider.mozilla.lists.base                                           | moz-std              |
| browser.safebrowsing.provider.mozilla.lists.content                                        | moz-full             |
| browser.safebrowsing.provider.mozilla.nextupdatetime                                       | 1603742873301        |
| browser.safebrowsing.provider.mozilla.pver                                                 | 2.2                  |
| browser.safebrowsing.provider.mozilla.updateURL                                            | https://127.0.0.1    |
| browser.safebrowsing.reportPhishURL                                                        | https://127.0.0.1    |
| services.sync.prefs.sync.browser.safebrowsing.downloads.enabled                            | false                |
| services.sync.prefs.sync.browser.safebrowsing.downloads.remote. block_potentially_unwanted | false                |
| services.sync.prefs.sync.browser.safebrowsing.malware.enabled                              | false                |
| services.sync.prefs.sync.browser.safebrowsing.phishing.enabled                             | false                |
| browser.safebrowsing                                                                       | false                |

# Additional steps

This is what you can also consider disabling. Those are DRM options, geolocation and telemetry reports:

-  `privacy.resistFingerprinting` (set to `true`, though some less ethical sites may break)
-  `toolkit.telemetry.enabled`
-  `datareporting.healthreport.service.enabled`
-  `datareporting.healthreport.uploadEnabled`
-  `media.eme.enabled`
-  `media.gmp-eme-adobe.enabled`
-  `browser.pocket.enabled`
-  `geo.enabled`

# Today I learned

-  [Chromium is not private at all](https://www.reddit.com/r/privacy/comments/34tc2f/how_safe_is_chromium_privacy_wise/cqxzhh8?utm_source=share&utm_medium=web2x&context=3)
-  Firefox sends data to a Google service by default
-  Firefox uses `chrome://` in their browser’s code just like Chromium-based browsers

Always doubt the defaults.
