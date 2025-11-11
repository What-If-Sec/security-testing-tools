## Google Dork Cheat Sheet

#### Quick disclaimer:
Always get explicit permission before searching or testing domains you do not own. Google dorking can reveal sensitive information that organizations did not intend to expose. Use these queries only on domains and assets you control or where you have written authorization. If you find sensitive data owned by others report it responsibly and do not exploit it.

---

### Best Practices
* Start with passive searches to avoid triggering alerts or alarms
* Use exact phrase quotes to reduce noise and improve precision
* Document findings with URLs timestamps and notes for remediation
* Automate safe periodic checks against domains you control
* Combine dorking with other discovery tools for complete coverage

---

### Dorks

## Basic Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `site:` | Restrict search to a single domain or host | `site:example.com` |
| `filetype:` | Limit results to a specific file extension | `site:example.com filetype:pdf` |
| `inurl:` | Find pages with a keyword in the url path | `site:example.com inurl:admin` |
| `intitle:` | Find pages with a keyword in the page title | `site:example.com intitle:"login"` |
| `intext:` | Search for a keyword within the page body | `site:example.com intext:"confidential"` |
| `cache:` | View Google’s cached version of a page | `cache:example.com/page` |
| `related:` | Find sites similar to a target site | `related:example.com` |
| `info:` | Show Google information about a url | `info:example.com` |
| `allinurl:` | All specified words must appear in the url | `allinurl: docs user guide` |
| `allintitle:` | All specified words must appear in the page title | `allintitle: password policy` |
| `"` (quotes) | Exact phrase match | `"internal procedure manual"` |
| `OR` | Logical OR between terms | `site:example.com "report" OR "summary"` |
| `AROUND(n)` | Find terms within n words of each other | `"user data" AROUND(5) breach` |
| `-` | Exclude a keyword from search results | `site:example.com -test` |
| `link:` | Find pages that link to a specific URL (Results can be hit or miss depending on how Google indexes backlinks) | `link:example.com` |
| `define:` | Show dictionary style definitions for a term | `define:repudiation` |
| `phonebook:` | Search old public phonebook listings (largely deprecated) | `phonebook:John Doe New York` |
| `map:` | Shortcut for map related queries; modern usage usually via Google Maps UI | `map: coffee shop near me` |
| `before:` | Restrict results to pages published before a date (YYYY-MM-DD) | `security breach before:2022-01-01` |
| `start..end` | Search for results that contain a number in a specified range | `camera $250..$1000` |
| `inanchor:` | Find pages that are linked to with specific anchor text (Results can be hit or miss depending on how Google indexes anchor text) | `inanchor:"download manual" example.com` |


---

### Common Defensive Use Cases and Query Examples

| **Use Case** | **Example Query** |
|---------------|-------------------|
| **Find publicly accessible documents (PDFs, DOCX, XLSX)** | `site:example.com (filetype:pdf OR filetype:docx OR filetype:xlsx)` |
| **Locate exposed login or admin panels** | `site:example.com (inurl:admin OR inurl:login OR inurl:wp-admin)` |
| **Identify configuration or backup files accidentally exposed** | `site:example.com (inurl:config OR inurl:backup OR filetype:sql OR filetype:bak)` |
| **Detect files containing credentials or secrets** | `site:example.com intext:password (filetype:txt OR filetype:env OR filetype:ini)` |
| **Find public repositories of internal code or comments** | `site:github.com "example.com" password OR api_key` |
| **Search for exposed API endpoints** | `site:example.com inurl:api OR inurl:endpoint` |
| **Check for public directory listings or unprotected folders** | `site:example.com intitle:"index of /"` |
| **Identify pages referencing internal IP addresses** | `site:example.com "10.0.0." OR "192.168."` |
| **Locate pages mentioning confidential or internal data** | `site:example.com intext:"confidential" OR intext:"internal use only"` |
| **Check for cloud storage leaks (AWS, GCP, Azure)** | `site:example.com ("aws_access_key_id" OR "storage.googleapis.com" OR "blob.core.windows.net")` |
| **Find old versions of pages still cached by Google** | `cache:example.com/path/to/page` |
| **Detect subdomains or forgotten assets** | `site:*.example.com -www` |
| **Monitor for brand impersonation or phishing pages** | `related:example.com` |
| **Track public financial or HR documents** | `site:example.com filetype:xls (intext:"salary" OR intext:"payroll")` |
| **Find pages referencing CVEs or vulnerabilities** | `site:example.com intext:"CVE-"` |
| **Check exposure of internal project names or codenames** | `site:example.com intext:"Project Falcon"` |
| **Search for unprotected database dumps** | `site:example.com (filetype:sql OR filetype:db)` |
| **Look for public staging or development environments** | `site:example.com (inurl:staging OR inurl:dev OR inurl:test)` |
| **Detect contact info or employee listings** | `site:example.com intext:"@example.com" OR intext:"employee directory"` |
| **Review cached or indexed sensitive reports** | `site:example.com filetype:pdf intext:"confidential" before:2024-01-01` |

---

### Notes
- Replace `example.com` with your organization’s domain when performing authorized searches.  
- These queries are for **defensive security testing** — identifying exposed assets and sensitive data leaks in your own environment.  
- Combine operators (e.g., `site:` + `filetype:` + `intext:`) to refine searches and reduce noise.  
- Always document findings with the date, query used, and remediation status.  

