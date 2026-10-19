# The Clinejection incident — February 2026

The Clinejection incident was a real-world cybersecurity event that demonstrated how a prompt injection vulnerability in an AI coding assistant could lead to a software supply-chain attack. It involved Cline, an open-source AI coding assistant, and showed how malicious instructions could exploit an automated AI workflow and ultimately affect software distributed to developers. 

## What happened?
1. A malicious prompt targeted an AI agent. Cline used an AI-powered bot to help review and triage GitHub issues. A security researcher discovered that a specially crafted issue title could manipulate the bot into executing unintended commands. This vulnerability was publicly disclosed on February 9, 2026. 
   
2. The vulnerability exposed software publishing credentials. The attack path involved weaknesses in the automated GitHub Actions workflows, including cache poisoning, which could allow an attacker to access credentials used to publish software releases. 

3. An unauthorized software update was published. On February 17, an attacker used a publishing token that had not been properly revoked to release Cline CLI version 2.3.0. The package included an additional installation script that installed OpenClaw, another AI agent, without users' authorization. The compromised version was available for approximately eight hours and was downloaded around 4,000 times. 
   
## Why is this incident important?

The incident demonstrates three major security risks associated with autonomous AI agents:
- Prompt injection: An AI agent can be manipulated by malicious instructions in content it processes.
- Excessive permissions: An AI agent with access to powerful tools and credentials can unintentionally become a pathway to sensitive systems.
- Software supply-chain compromise: A vulnerability in an automated development workflow can affect thousands of people who install a compromised software package.

## What was the outcome?
Cline deprecated version 2.3.0, revoked the compromised publishing token, released version 2.4.0, and made changes to its publishing process. Although the incident caused widespread concern, OpenClaw itself was not identified as malicious, and the reported impact was considered limited. 


**The key lesson:** The Clinejection incident shows that prompt injection is not just a problem with AI generating incorrect answers. When an AI agent has access to development tools, automated workflows, and sensitive credentials, a manipulated agent can become a security risk to the entire software development process.

## Official report additions
Report published: February 24, 2026

### Confirmed Scope
Cline says only its CLI npm package was affected. Its VS Code/OpenVSX and JetBrains extensions and source code remained uncompromised. The CLI binary was unchanged. Cline reported no uder-data access or exfiltration and no malicious-code delivery.

### Why the exposure continued
During remediation, the team deleted the wrong npm token, leaving the exposed token usable.

### Response timeline
| Date and Time | Event |
|---------------|-------|
| January 1, 2026 | Private vulnerability report |
| February 9, 2026 | Public disclosure and workflow removal |
| February 17, 2026, 03:26 PT | Unauthorized publication |
| February 17, 2026, 11:23 PT | Corrected release and token revocation complete |

### Security changes
Cline removed AI triage and caches from publishing workflows, revoked old credentials, and switched npm publishing to OpenID Connect (OIDC) with release provenance. It also began verifying that revoked credentials actually fail.

**Source:** Cline's official incident report, linked below.

### Sources
- [Cline: Security Incident Report](https://cline.bot/blog/post-mortem-unauthorized-cline-cli-npm) - Saoud Rizwan, February 24, 2026
- [Adnan Khan: Clinejection](https://adnanthekhan.com/posts/clinejection/) - Original security research and incident timeline
- [The Hacker News: Report on the Cline CLI supply-chain attack](https://thehackernews.com/2026/02/cline-cli-230-supply-chain-attack.html)
- [Cloud Security Alliance: Security analysis of Clinejection and CI/CD risks](https://labs.cloudsecurityalliance.org/research/csa-research-note-clinejection-prompt-injection-cicd-cache-p/)
