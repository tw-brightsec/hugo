---
title: "How to Add Bright to the WAF Allowlist"
slug: "how-to-add-bright-to-the-waf-allowlist"
hidden: false
createdAt: "2022-08-03T09:30:17.314Z"
updatedAt: "2022-08-29T10:30:27.320Z"
---
This section provides information on how to add Bright to the WAF allowlist. For instructions, go to the necessary WAF type below, and then click the link to access the document. 

# Reblaze WAF

To add Bright to the allowlist, add Bright IP addresses **as Bypass** and add an **OC policy** according to the [ACL Policies](https://gb.docs.reblaze.com/product-walkthrough/security/profiles/acl-policies) guide.

# AKAMAI WAF, AKAMAI V2, Trellix and Akamai Collaboration

To modify an API Client IP allowlist for BrightSec, follow the instructions under the links below.

- [Official documentation](https://techdocs.akamai.com/identity-cloud-legacy-clients/reference/post-set-whitelist)
- [Non-official documentation](https://janrain-education-center.knowledgeowl.com/home/clientsset-whitelist)

# Cerber WP

The IP Access List (ACL) enables the users to restrict access to the WordPress admin dashboard, and vital WordPress features, and protect login and registration forms from access by unwanted computers and bots. For information on how to use the IP Access Lists, see [Using IP Access Lists to Limit Access and Protect WordPress](https://wpcerber.com/using-ip-access-lists-to-protect-wordpress/).

# Siteguard

This WAF doesn't have ACL. For instructions on adding Bright to the Siteguard allowlist, see [How to Limit Access to Website During Development](https://www.siteground.com/kb/limit-access-website-development/).

# Cloudflare CF-RAY, Cloudflare DNS WAF

Access Control Lists (ACLs) define allowed source IP addresses from where servers accept incoming data or control messages. For details, see the links below.

- [Access Control Lists (ACLs)](https://developers.cloudflare.com/dns/zone-setups/zone-transfers/access-control-lists/)
- [Allow Cloudflare IP Addresses](https://developers.cloudflare.com/fundamentals/get-started/setup/allow-cloudflare-ip-addresses/)

To add Bright to the Cloudflare allowlist, see [Adding Bright DAST to the Allowlist on Cloudflare](https://docs.brightsec.com/docs/troubleshooting-for-problematic-scans#adding-bright-dast-to-the-allowlist-on-cloudflare).

# BlockDOS WAF

BlockDOS WAF has a cookie policy. Cookies consist of portions of code installed in the browser that assist the Owner in providing the Service according to the purposes described. For details on BlockDOS WAF Cookie Policy see [Cookie Policy](https://www.blockdos.net/cookie-policy/).

# Wallarm

For adding IP address to the allowlist for Brightsec, see [IP Address Whitelist](https://docs.wallarm.com/user-guides/ip-lists/whitelist/).

# OpenResty Lua WAF

lua-resty-waf is distributed with a number of rulesets that are designed to mimic the functionality of the ModSecurity CRS. For more information about rules, see [lua-resty-waf - High-Performance WAF Built on the OpenResty Stack](https://github.com/p0pr0ck5/lua-resty-waf#included-rulesets).

# A10 Thunder

**access-list extended**: Configure an extended Access Control List (ACL) to permit or deny traffic based on source and destination IP addresses, IP protocol, and TCP/UDP ports. For details, see [ACOS 1.0 Documentation - Access-List Extended](https://documentation.a10networks.com/ACOS/410x/410-P9/ACOS_4_1_0-P9/html/axapiv3/access_list_extended.html).

# BulletProof Security Pro

BulletProof Security Pro has a cookie policy. For information on how cookies are used on [bulletproof.co.uk](https://www.bulletproof.co.uk/), the options for controlling the use of cookies, and what cookies are used, see [Bulletproof cookie Policy](https://www.bulletproof.co.uk/cookie-policy).

# Nemesida

Nemesida has a personal pane where administrators can set up correct rules. The appropriate sections are **Add new user** and **Unlock Request functionality**.  For more information, see [Nemesida WAF Cabinet](https://nemesida-waf.com/manuals/1612#personal).

# ModSecurity

The following link provides an easy way to set up the allowlist based on IP addresses: [How to whitelist an IP address in ModSecurity](https://support.cpanel.net/hc/en-us/articles/360058157433-How-to-whitelist-an-IP-address-in-ModSecurity).

# Gocache WAF

You need to add the BrightSec IP address to ACL. For documentation, see [Customização do WAF](https://docs.gocache.com.br/waf_custom/regras/gocache-v1/).

> 📘 Note
> 
> The original documentation is in Portuguese. Please use Goolge translate to translate the page.

# Imperva, Incapsula

For setting up Imperva Web Protection (Security Settings and ACL for Brightsec), see the documentation below.

- [Web Protection - Security Settings](https://docs.imperva.com/bundle/cloud-application-security/page/settings/security-settings.htm)
- [Security Rule Use Case Examples](https://docs.imperva.com/bundle/cloud-application-security/page/rules/security-rule-examples.htm)
- [Create and Manage Policies](https://docs.imperva.com/bundle/cloud-application-security/page/policies.htm#WAF)
- [ACL Section](https://docs.imperva.com/bundle/cloud-application-security/page/settings/security-settings.htm#WhitelistspecificIPsources)

# F5 ASM – BIG IP

APM® access control lists (ACLs) restrict user access to host and port combinations that are specified in access control entries (ACEs). An ACE can apply to Layer 4 (the protocol layer), Layer 7 (the application layer), or both. Layer 4 or Layer 7 ACL is used with network access, application access, or web access connections. For details, see [Configuring Access Control Lists](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-network-access-13-0-0/3.html).

# AWS WAF

For instructions on adding Bright to the AWS WAF allowlist, see [AWS CloudFront](https://docs.twingate.com/docs/aws-cloudfront).