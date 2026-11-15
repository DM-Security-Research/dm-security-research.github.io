# Technical Report 001
## Cryptographic Context Validation in Electronic Voting Systems
### A scoped source-code security review of Swiss Post E-Voting

**Author:** David Menendez — DM Security Research  
**Research reference:** SWISS-001  
**Study type:** Defensive source-code review and threat-model analysis  
**Repository revision reviewed:** `095a02f870b787d8b034c9fa3819f7b329354f68`  
**Result:** No reportable vulnerability confirmed by the documented static review.

> **Evidence boundary:** This report summarizes a documented local research review. It is **not** an independent certification, an accepted bug-bounty report, a demonstration of a bypass, or a claim of exploitation. The original laboratory, detailed notes, and any follow-up test logs are not published here. Later JUnit execution evidence has not been independently re-inspected for this publication and therefore no numeric test-pass claim is made.

### 1. Research objective

Investigate how an electronic voting implementation binds cryptographic proof material, encrypted selections, card and election context, and subsequent vote-processing validation. The objective was to evaluate candidate trust-boundary weaknesses without affecting production systems or voters.

### 2. Scope

The documented review centered on Swiss Post E-Voting's `VerifyBallotCCR` processing path and related components, including:

- `VerifyBallotCCRAlgorithm`, its input and context structures;
- creation and verification of encrypted vote and choice-return-code material;
- downstream validation of partial choice return codes;
- relevant server processing and offline-verification paths.

The research was tied to the source revision above. Findings must not be generalized to newer versions without retesting.

### 3. Method

The review traced data and authorization context across related source files and documented how cryptographic proof checks interact with later safeguards. Particular attention was paid to whether acceptance at one stage could imply acceptance of a modified voting context end-to-end.

The evidence archive describes a completed **static review**. In that run, execution of Maven tests was blocked because the local Maven version was 3.8.7 while the project required 3.9.11 or newer. Accordingly, this publication does not imply that the static-review environment successfully executed its test suite. Separate subsequent testing has been discussed in the private laboratory, but its original logs are not reproduced or independently inspected in this public report.

### 4. Observations

The reviewed design uses multiple validation stages, rather than treating a single cryptographic check as sufficient evidence of valid vote processing. The static analysis examined the distinction between an aggregate plaintext-equality relation and per-position context validation. It also traced downstream constraints on recovered choice-return-code values, including distinctness and contextual/positional allow-list checks.

The documented review did not establish a path by which the candidate inconsistency would produce an undetected manipulation of the election outcome. The analysis also considered later state transitions and offline verification as relevant safeguards. These are **observations about the reviewed code and model**, not proof of end-to-end security.

### 5. Result and limitations

**Result:** The documented SWISS-001 static audit concluded that no reportable vulnerability had been confirmed for the reviewed revision.

**Limitations:**
- The review was scoped, not a complete security assessment of the voting platform.
- The static-review environment did not execute tests because of a Maven version mismatch.
- Follow-up runtime evidence has not been included or independently verified for this report.
- No live election system was tested for this publication.
- No claim of a successful exploit, a discovered zero-day, an assigned CVE, or a vendor-accepted report is made.

### 6. Reproducibility and evidence policy

The private research archive retains source references and investigation notes. A public reproduction package can be considered separately after checking the applicable disclosure rules and validating that it contains no sensitive or unapproved material.

This report is a **research summary**; it does not provide a runnable test suite or imply reproducibility without the underlying source revision and local laboratory setup.

### 7. Responsible disclosure and attribution

Swiss Post E-Voting is a project of Swiss Post. **DM Security Research is independent and is not affiliated with, endorsed by, or acting on behalf of Swiss Post or YesWeHack.**

The official public program describes authorization, testing scope, and coordinated disclosure requirements. Research that identifies a qualifying vulnerability should follow those channels before public disclosure.

**Official sources:**
- [Swiss Post E-Voting bug bounty program and policy](https://yeswehack.com/programs/swiss-post-evoting)
- [Swiss Post E-Voting community — code of conduct](https://swisspost-digital.ch/en/evoting-community/code-of-conduct)
- [Swiss Post E-Voting community — FAQ](https://swisspost-digital.ch/en/evoting-community/help-and-contact/faq)

**Contact:** security.research.dm@gmail.com
