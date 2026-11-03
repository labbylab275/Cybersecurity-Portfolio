# Cross-Site Scripting (XSS) Fundamentals

**Platform:** TryHackMe  
**Module:** Intro to Cross-site Scripting  
**Category:** Web Application Security  
**Type:** Guided Learning / Technical Notes  
**Career Focus:** Junior Security Analyst / SOC Analyst

## Overview

As part of my cybersecurity learning, I completed TryHackMe's *Intro to Cross-site Scripting* module to better understand XSS vulnerabilities, their different forms, and the security risks associated with executing untrusted JavaScript in web applications.

The module introduced reflected, stored, DOM-based, and blind XSS, along with the role of JavaScript payloads in demonstrating web application vulnerabilities.

## What Is Cross-Site Scripting (XSS)?

Cross-site scripting is a web application injection vulnerability that occurs when untrusted input is handled in a way that allows attacker-controlled JavaScript or other active content to execute in a user's browser.

An attacker may exploit XSS to manipulate webpage content, impersonate application interactions, or access information available to scripts within the affected application's security context.

### Types of XSS

**1. Reflected XSS**

Occurs when user-controlled input is included in a web application's response without appropriate output encoding or other safe handling.

- Often involves URL parameters or form submissions.
- The malicious input is not necessarily stored.
- Execution typically requires a user to visit a crafted link or submit manipulated data.

**2. Stored XSS**

Occurs when malicious input is saved by an application and subsequently displayed in an unsafe context.

- May appear in comments, profiles, or other stored user content.
- Can affect multiple users viewing the compromised content.
- May execute repeatedly until the underlying issue or stored content is removed.

**3. DOM-Based XSS**

Occurs when client-side JavaScript processes untrusted input and inserts it into the Document Object Model (DOM) in an unsafe way.

- The vulnerability exists in client-side processing.
- Common risks include unsafe DOM manipulation and dynamic script execution.
- Dangerous functions such as `eval()` can introduce injection vulnerabilities when used with untrusted data.

**4. Blind XSS**

Occurs when an injected script executes in a location the tester cannot directly observe.

- May affect administrative dashboards or internal support interfaces.
- Execution can sometimes be detected through callbacks to an authorized monitoring endpoint.
- Demonstrates how vulnerabilities in user-facing inputs can affect privileged interfaces.

## Proof of Concept (PoC)

A proof of concept is a controlled demonstration showing that a vulnerability exists.

For basic XSS testing, an alert dialog can demonstrate that injected JavaScript executes in the browser.

A successful alert does not automatically establish that an attacker can steal session information or perform more serious actions. Those consequences depend on the application's security configuration and the execution context.

## Security Implications

XSS vulnerabilities may allow attackers to:

- Modify webpage content and mislead users.
- Perform unauthorized actions in a user's authenticated browser context.
- Access information exposed to client-side scripts.
- Redirect users to malicious content.
- Compromise the confidentiality or integrity of web application interactions.

The impact depends on the affected application, available permissions, and security controls.

## Defensive Considerations

Understanding XSS helps security analysts identify potential web application threats.

Important preventive controls include:

- Context-appropriate output encoding.
- Safe DOM manipulation.
- Input validation where appropriate.
- Avoidance of unsafe JavaScript execution functions.
- Content Security Policy (CSP) as an additional protective layer.
- Secure session-cookie configurations, including HttpOnly where appropriate.

## Relevance to Security Operations

From a defensive perspective, an analyst should understand how suspicious requests, unusual script-containing parameters, unexpected outbound browser connections, and web application alerts may relate to XSS attempts.

Potential investigation steps include:

1. Reviewing relevant web server and WAF logs.
2. Examining suspicious request parameters.
3. Determining whether the application reflected or stored untrusted content.
4. Correlating alerts with browser or application behavior when evidence is available.
5. Escalating confirmed vulnerabilities to the appropriate remediation team.

An XSS-like string in a request does not prove successful exploitation.

## Key Takeaways

This module helped me develop a foundational understanding of XSS vulnerabilities and the differences between reflected, stored, DOM-based, and blind XSS.

My primary takeaway is that web application security depends on how untrusted data is processed and displayed, and that understanding these vulnerabilities is important for recognizing application-layer threats.

## Reference

TryHackMe — Intro to Cross-site Scripting  
https://tryhackme.com/room/xss
