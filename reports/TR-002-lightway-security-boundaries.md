# Technical Report 002
## Security Boundary Review of a Rust VPN Protocol and Cryptographic Dependencies
### A scoped research summary of ExpressVPN Lightway and wolfssl-rs

**Author:** David Menendez — DM Security Research  
**Publication date:** 2026-11-15  
**Study:** Independent authorized source-code review  
**Source references studied:** Lightway `6f037963fb3b52fd678ba4338e5e5a1dca64a08e`; wolfssl-rs `f020d776bd4c948766c390b6bfd29e11f4eb824c`  
**Public conclusion:** No remotely exploitable vulnerability in Lightway was demonstrated by the documented scoped review.

> **Disclosure boundary:** This is a deliberately limited, non-exploit research summary. It does not publish active vulnerability hypotheses, proof-of-concept material, affected code locations, issue-trigger conditions, or sensitive laboratory evidence. It is not a vendor-endorsed audit or a representation of overall system security.

## 1. Objective

Study security-relevant trust boundaries across a VPN protocol implemented in Rust, its network input handling, and cryptographic dependencies. Assess whether a theoretical concern in a lower-level component is actually reachable from an externally supplied protocol message, rather than assuming that every library-level property has protocol-level impact.

## 2. Scope and environment

The documented research involved source-code review of open-source ExpressVPN Lightway and the related Rust wrapper for wolfSSL, in a local research workspace. The versions above identify the reference snapshots reported by the lab; conclusions should not be generalized to other releases or configurations without revalidation.

No production infrastructure or customer traffic is represented as having been tested for this report. It does not reproduce proprietary integrations.

## 3. Methodology

The review followed the flow of untrusted data through publicly documented protocol handling, size and state checks, cryptographic interfaces, and error-handling boundaries. Candidate concerns were evaluated against upstream input constraints and the distinction between public library APIs and actual protocol call paths.

Research records differentiated:
- source-level observations;
- conditions required for a theoretical issue;
- reachability from network inputs;
- controls already present in the protocol;
- missing integration evidence and untested hypotheses.

This process aims to reduce false positives and avoid attributing protocol-level security impact to a condition that cannot be reached through the reviewed call path.

## 4. Non-sensitive observations

The reviewed implementation applies constraints on network data before it reaches some lower-level cryptographic processing paths. Those constraints materially affect which lower-level behaviors can be reached from protocol packets.

The scoped analysis did **not** establish a remotely exploitable vulnerability in the reviewed Lightway packet-processing path. This is a result of the examined path only, not a security guarantee for the protocol, dependency, or any production deployment.

Other questions involving separate integration components and backend-specific runtime semantics remained outside the evidence available for the particular review. They must not be described as confirmed exploits.

## 5. Evidence and limitations

The local investigation recorded source revisions, reasoning about input reachability, and limitations. The full private research archive is not part of this public report.

**Limitations:**
- No claim of a successful remote exploit or real-world compromise.
- No claim that all wolfSSL or wolfssl-rs call paths are safe.
- No publication of unresolved security hypotheses or PoC artifacts.
- The analysis does not establish behavior of proprietary or external integrators.
- Findings are scoped to the cited snapshots and the reviewed paths.
- No vendor acceptance, paid bounty, CVE, or coordinated public disclosure is claimed.

## 6. Responsible disclosure

Any non-public candidate security issue is reserved for the appropriate private vendor/program disclosure workflow. Technical reproduction details are intentionally omitted pending authorization or coordination.

**Public references:**
- [ExpressVPN Lightway source](https://github.com/expressvpn/lightway)
- [ExpressVPN wolfssl-rs source](https://github.com/expressvpn/wolfssl-rs)
- [ExpressVPN YesWeHack program](https://yeswehack.com/programs/expressvpn-bug-bounty-program)
- [Lightway repository security policy](https://github.com/expressvpn/lightway/blob/main/SECURITY.adoc)

**Independence:** DM Security Research is not affiliated with or endorsed by ExpressVPN, wolfSSL, or YesWeHack.

**Contact:** security.research.dm@gmail.com
