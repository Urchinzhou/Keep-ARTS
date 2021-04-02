# [Find Your First Bug — #3 CVE’s](https://github.com/Urchinzhou/Keep-ARTS/issues/3)

[Find Your First Bug — #3 CVE’s](https://safaras.medium.com/find-your-first-bug-3-cves-4abfb4341a88)
This is an artical about finding bugs by CVE. The author was new about hacking tech, but got a small bounty by report critical bug. The following steps are summed up by him:
1. Find the Technologies used by Target
- When we visit a website use wappalyzer extension to look for different technologies used by the website.
- Look carefully on the responses on burpsuite, they sometimes show the version of services used by the app
- use cve’s templates on nuclei
- Use technologies templates on nuclei
2. Search for it’s CVE’s and Exploits
- Google technology cves (eg:- jira cves) or technology exploits (eg:- jira exploits) and now we have the cve number ( eg: CVE-2020-1122)
- Search for the exploits ( CVE-2020–1122 exploit) on Google, twitter, exploit-db, Github, Youtube etc.
- Exploit it and report it! Enjoy $$
