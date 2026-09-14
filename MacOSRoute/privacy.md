# Privacy Policy

Effective date: September 14, 2026

This Privacy Policy applies to MacOSRoute (bundle identifier: `com.hyperits.app.MacOSRoute`, referred to below as the "App"), including its background service (`com.hyperits.app.MacOSRoute.helper`, referred to below as the "Background Service").

The App is a macOS utility for managing IPv4 routes. It keeps selected IP addresses, network ranges, and domains routed through a chosen network exit, such as the gateway of your physical network while a VPN is active, and it re-applies those routes when your network changes. The App works entirely on your Mac. It has no accounts, no servers of its own, and no analytics. Please read this policy carefully before using the App.

## 1. What Information We Process

### 1.1 Rules and Settings You Create

When you use the App, you may create and store the following information on your Mac:

- Route rules: IP addresses, network ranges (CIDR), and domain names you add
- Notes, group names, enabled state, priority, and the network exit chosen for each rule
- Settings such as the preferred network interface, DNS mode, custom DNS servers, re-resolution interval, retention period for previously resolved addresses, and pause state

This information is stored locally in `/Library/Application Support/MacOSRoute/` so that the Background Service can keep your routes in effect, even when the App window is closed or the App is not running.

### 1.2 Route and DNS State

To keep routes consistent and to recover safely after a restart, the Background Service stores the following on your Mac:

- A record of the routes it has added or adopted, including destination, gateway, and network interface (`applied.json`)
- The IP addresses resolved for domains in your rules and when they were resolved (`dns.json`)
- An activity log containing rule targets, resolved IP addresses, gateway addresses, network interface names, and error messages (`/Library/Logs/MacOSRoute/helper.log`)

The App also keeps ordinary local preferences, such as window size and position, in the standard macOS preferences for the App.

### 1.3 Network Configuration of Your Mac

To determine where routes should point and to show diagnostics, the App reads the following information from macOS:

- Network interfaces, local IP addresses, subnet masks, gateways (routers), and DNS servers of your current networks
- The system IPv4 routing table

This information is read and processed only on your Mac. It is not sent anywhere.

### 1.4 Network Requests Made by the App

The App does not communicate with any server operated by us. It makes network requests only in the following cases:

- **DNS lookups for domain rules.** To find the IP addresses of domains in your rules, the App sends DNS queries containing those domain names. Depending on the DNS mode you choose, queries are sent to:
  - the DNS servers of your current physical network (default), and, only if those servers do not respond, the public DNS servers `223.5.5.5` (Alibaba Cloud), `119.29.29.29` (Tencent Cloud DNSPod), and `8.8.8.8` (Google Public DNS), sent through your physical network interface;
  - the DNS servers configured in macOS (System DNS mode), which may be provided by your VPN or proxy software; or
  - DNS servers you enter yourself (Custom DNS mode).
- **Diagnostics you start.** When you run a diagnosis for a target you enter, the App looks up that target using both the DNS servers of your physical network (with the public fallback servers above) and the DNS servers configured in macOS, so the results can be compared; queries the system routing table, and attempts a TCP connection to each resolved address on the port you specify, measuring how long the connection takes. No application data is sent over these connections, and they are closed immediately.

DNS servers that receive these queries can see the domain names being looked up and the IP address the query comes from, and they process that information under their own privacy policies. Routes created by the App change how your Mac's network traffic is forwarded, but the App does not inspect, record, or modify the content of that traffic.

### 1.5 System Permissions

The App may ask for the following permissions. Each is used only for the purpose described.

- **Administrator authorization.** Installing, updating, or uninstalling the Background Service requires an administrator password. The password is entered in a standard macOS authorization dialog and handled by macOS; the App never sees or stores it.
- **Background item.** The Background Service runs as a system launch daemon so that routes stay in effect. macOS lists it in System Settings under Login Items & Extensions, where you can review it.
- **Local Network access.** Diagnostics may send DNS queries to DNS servers on your local network. macOS may ask you to allow Local Network access for this purpose.
- **Launch at login.** If you turn on "Launch at login", the App registers itself with macOS to start when you log in. You can turn this off at any time.

The App does not request access to your contacts, photos, location, camera, microphone, files, or other personal data. The Background Service accepts commands only from the signed MacOSRoute app running under an administrator account.

### 1.6 Import and Export

If you use import or export, the App reads from or writes to the file you choose in a standard macOS file dialog. Exported files contain your rules and settings and are saved only where you choose.

## 2. How We Use Information

We process the information described above only for the following purposes:

- To add, verify, repair, and remove the routes defined by your rules
- To detect network changes and determine the correct gateway and network interface
- To resolve domains in your rules and to keep recently used addresses routed
- To show rule status, the routing table, diagnostics, and logs in the App
- To import and export your rules when you ask the App to do so

## 3. How We Share Information

We do not collect your information on our servers, do not sell personal information, and do not use data for advertising or cross-app tracking. The App contains no analytics, advertising, or crash-reporting SDKs.

Information leaves your Mac only in the following situations:

- DNS queries for domain names in your rules or diagnostics are sent to the DNS servers described in Section 1.4
- TCP connection tests are made to the addresses of diagnostic targets you enter

## 4. Data Retention

All data is kept on your Mac:

- Rules, settings, route records, and DNS state are kept in `/Library/Application Support/MacOSRoute/` until you delete the rules in the App or delete that folder. Uninstalling the Background Service from the App keeps your rules so they can be restored by reinstalling.
- Resolved addresses that are no longer returned for a domain are removed after the retention period you configure (6 hours by default).
- The in-app log view shows recent entries only. The log file `/Library/Logs/MacOSRoute/helper.log` is kept until you delete it.

To remove all data created by the App, uninstall the Background Service from the App's settings, delete the App, and then delete `/Library/Application Support/MacOSRoute` and `/Library/Logs/MacOSRoute` (administrator permission is required).

## 5. Your Choices and Controls

You can control how the App processes data in the following ways:

- Add, edit, disable, or delete rules at any time, or pause all routes
- Use IP address and network range rules instead of domain rules to avoid DNS lookups
- Choose which DNS servers are used for domain lookups in Settings
- Uninstall the Background Service, which removes routes added by the App
- Turn off "Launch at login", and review background items in System Settings
- Revoke Local Network access in System Settings

## 6. Children's Privacy

The App is not specifically directed to children. We do not knowingly collect personal information from children through the App.

## 7. International Transfers

We do not transfer your data. DNS queries sent to the public DNS servers listed in Section 1.4, or to DNS servers you configure, may be processed in the countries or regions where those providers operate.

## 8. Changes to This Privacy Policy

We may update this Privacy Policy from time to time based on feature changes, legal requirements, or product updates. If material changes are made, we will publish an updated version at this location. The updated policy becomes effective on the date it is published.

## 9. Contact Us

The App is developed by Chongqing Hyperits Network Technology Co., Ltd. If you have questions about this Privacy Policy or how the App processes data, please contact us:

- Contact: RICL
- Email: [riclavaz@gmail.com](mailto:riclavaz@gmail.com)
