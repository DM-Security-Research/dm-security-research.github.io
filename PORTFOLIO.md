# Research portfolio — selected technical work

**David Menendez · DM Security Research · Argentina**

This document describes areas of hands-on research and laboratory practice. It is a **research portfolio, not a list of confirmed vulnerabilities, assigned CVEs, accepted disclosures, or paid bug-bounty findings**. Work in private repositories is described only at a high level. No vendor relationship or endorsement is implied.

## 1. Browser security and isolation

**Technical themes:** WebKit, JavaScriptCore, JavaScript runtime behavior, origin boundaries, Content Security Policy (CSP), sandboxing, and message passing.

**Research approach:** examine source code and behavior in isolated local test pages, using explicit expected-versus-observed outcomes. Distinguish standards-compliant behavior from security-relevant deviations.

**Disclosure status:** no public vulnerability claim is made by this portfolio.

## 2. Protocols, cryptographic signing, and authorization boundaries

**Technical themes:** transaction-signing authorization, cryptographic proof validation, message integrity, replay protection, and protocol security invariants.

**Research approach:** analyze open-source implementations and construct controlled local verification cases. Record rejected hypotheses as rigorously as successful reproductions.

**Disclosure status:** examples are methodological only; this page does not assert exploitable impact.

## 3. Source-code auditing and reproducible testing

**Technical themes:** C/C++, Rust, JavaScript, static analysis, security-oriented code review, and regression-test design.

**Research approach:** maintain isolated workspaces; use version-pinned source material where possible; test suspected conditions with minimized, reproducible cases; and preserve evidence of negative results.

**Disclosure status:** no previously private source or test artifact is published here.

## 4. Reverse engineering and experimental laboratories

**Technical themes:** binary inspection, protocol behavior, format validation, test harnesses, and firmware-adjacent research in controlled environments.

**Research approach:** prefer non-destructive and offline validation, protect user data, and separate analysis from deployment or changes to real devices.

**Disclosure status:** no assertion of unauthorized device access or bypass capability is made.

## Validation standard

Each potential finding is documented internally with:
- Scope and authorization basis
- Target component and version
- Technical hypothesis and threat model
- Test setup, inputs, and expected behavior
- Actual observations and reproducibility
- Potential security impact and material limitations
- Disclosure decision and status

**Evidence policy:** only independently reviewable and disclosure-safe material will be linked publicly. Private lab code, ongoing vulnerability hypotheses, exploit details, and sensitive third-party data stay private.

## Public research principles

See [Research methodology](./RESEARCH.md) and [Responsible disclosure](./DISCLOSURE.md).

**Contact:** security.research.dm@gmail.com
