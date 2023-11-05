
---
title: "Firefox / Chrome Setting Management"
date: 2023-10-13 11:48:38
lastmod: 2023-10-15 23:31:04
categories: ['firefox', 'chrome', 'macos', 'mdm', 'profile']
draft: false
---


# Firefox / Chrome Setting Management

If you need to manage a configuration of a specific extension (eg. Add a website to the “Trusted Site” list on uBlock)

## Firefox
Firefox’s extension config is put under a `3rdparty` key that can be in a profile along all your other Firefox Settings

Profile:
```
<dict>
  <key>EnterprisePoliciesEnabled</key>
  <true />
  <key>3rdparty</key>
  <dict>
    <key>Extensions</key>
    <dict>
      <key>uBlock0@raymondhill.net</key>
      <dict>
        <key>toAdd</key>
        <dict>
          <key>trustedSiteDirectives</key>
          <array>
            <string>example.com</string>
            <string>example-two.com</string>
          </array>
        </dict>
      </dict>
    </dict>
  </dict>
  <key>PayloadDisplayName</key>
  <string>Firefox Config</string>
  <key>PayloadIdentifier</key>
  <string>some.identifier.here</string>
  <key>PayloadType</key>
  <string>org.mozilla.firefox</string>
  <key>PayloadUUID</key>
  <string>0CA00E46-3E4C-49CD-8DE3-40D08C20EB66</string>
  <key>PayloadVersion</key>
  <integer>1</integer>
</dict>
```

## Chrome
Chrome’s extension configuration is a bit different in that it is actually a separate profile for different extensions. So you will create a profile called `com.google.Chrome.EXTENSIONID`.

Profile:
```
<dict>
    <key>toAdd</key>
    <dict>
      <key>trustedSiteDirectives</key>
      <array>
        <string>example.com</string>
        <string>example-two.com</string>
      </array>
    </dict>
    <key>PayloadDisplayName</key>
    <string>Chrome UBlock Config</string>
    <key>PayloadIdentifier</key>
    <string>some.identifier.here</string>
    <key>PayloadType</key>
    <string>com.google.Chrome.extensions.cjpalhdlnbpafiamejdnhcphjbkeiagm</string>
    <key>PayloadUUID</key>
    <string>0C06F283-26C7-4BDA-86E9-D6506F025B30</string>
    <key>PayloadVersion</key>
    <integer>1</integer>
</dict>
```
## Resources
https://github.com/gorhill/uBlock/wiki/Deploying-uBlock-Origin:-configuration#trustedsitedirectives-1

THANK YOU MAC ADMINS Slack. Now if only it wasn’t a walled garden for this.
https://macadmins.slack.com/archives/C5ACP4TUZ/p1677592077914009  
https://community.jamf.com/t5/jamf-pro/ublock-origin-trusted/m-p/295762#M262076


<!-- #public #firefox #chrome #macos #mdm #profile -->

<!-- {BearID:BAAC74AD-24E7-44A3-8B9F-9B1C7B87EBE9} -->
