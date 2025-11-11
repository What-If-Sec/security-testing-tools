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

### Basic Operators

| Operator | Description | Example |
|-----------|-------------|----------|
| `site:` | Restrict search to a specific domain or host | `site:example.com` |
| `filetype:` | Limit results to a specific file extension | `site:example.com filetype:pdf` |
| `inurl:` | Find pages with a keyword in the URL | `site:example.com inurl:admin` |
| `intitle:` | Find pages with a keyword in the title | `site:example.com intitle:"login"` |
| `intext:` | Search for a keyword within the page body | `site:example.com intext:"confidential"` |
| `cache:` | View Google’s cached version of a page | `cache:example.com/page` |
| `related:` | Find sites similar to a target site | `related:example.com` |
| `info:` | Display information Google has about a site | `info:example.com` |
| `allinurl:` | Search for multiple keywords in URLs | `allinurl: docs user guide` |
| `allintitle:` | Search for multiple keywords in titles | `allintitle: password policy` |
| `"` (quotes) | Exact phrase match | `"internal procedure manual"` |
| `OR` | Find results containing one term or another | `"report" OR "summary"` |
| `AROUND(n)` | Find terms within *n* words of each other | `"user data" AROUND(5) breach` |
| `-` | Exclude a keyword from search results | `site:example.com -test` |

---

### Common  Queries

| Goal | Query Example |
|------|----------------|
| Find public PDFs | `site:example.com filetype:pdf` |
| Find Office documents | `site:example.com (filetype:xls OR filetype:docx)` |
| Search for the word “confidential” | `site:example.com intext:"confidential"` |
| Find login or admin panels | `site:example.com (inurl:admin OR inurl:login OR inurl:wp-admin)` |
| Discover config or backup files | `site:example.com (inurl:config OR inurl:backup OR filetype:sql)` |
| Find text files with passwords | `site:example.com intext:password (filetype:txt OR filetype:env)` |
| Check for AWS keys or secrets | `site:example.com ("aws_access_key_id" OR "AWS_SECRET_ACCESS_KEY")` |
| Find payroll or finance spreadsheets | `site:example.com filetype:xls (intext:"payroll" OR intext:"salary")` |
| View cached page after removal | `cache:example.com/path/to/page` |
| Find similar or impersonating domains | `related:example.com` |

---

### Defensive Use Cases

| Use Case | How It Helps |
|-----------|--------------|
| **Inventory public assets** | Find forgotten subdomains, old portals, or documentation pages using `site:` and `inurl:` |
| **Detect data leaks** | Locate files or pages containing “confidential,” “password,” or “internal” |
| **Verify content removal** | Check `cache:` versions to confirm sensitive data was fully removed |
| **Monitor brand exposure** | Use `related:` or domain searches to find fake or copycat sites |

