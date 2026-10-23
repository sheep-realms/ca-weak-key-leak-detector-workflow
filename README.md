# CA Weak-Key Leak Detector 🔐🤡

**Enterprise-grade numerical paranoia for your Pull Requests.**

A highly sophisticated GitHub Actions workflow that scans newly added code for suspicious numerical artifacts allegedly associated with certificate authority (CA) weak-key incidents.

Because apparently, eight numbers are all it takes to bring cryptographic security to its knees.

> ⚠️ **This is a joke.** This workflow is a satirical security check, not a real cryptographic scanner, certificate validator, or secret detection tool. It does not detect actual private keys or verify any real-world CA vulnerability.

## Features

- **Automatic PR scanning** — Runs when a pull request is opened, reopened, or updated with new commits.
- **Eight highly suspicious numbers** — Scans added lines for the following numerical artifacts:
  - `156`
  - `155`
  - `115`
  - `66`
  - `230`
  - `4`
  - `56`
  - `237`
- **Strict security enforcement** — Any added line containing at least one of these numbers causes the check to fail.
- **Automated incident reporting** — Posts a dramatic security alert directly to the pull request when suspicious material is detected.
- **Comment deduplication** — Updates its existing report instead of flooding the discussion with duplicate alerts.
- **Automatic recovery** — If a subsequent commit removes all suspicious patterns, the check passes and the previous report is updated accordingly.

## How It Works

The workflow compares the pull request's head commit with its base commit and examines newly added lines in the resulting Git diff.

Each added line is checked for the presence of any of the eight designated numbers. If a match is found, the workflow reports the affected file, line number, and detected patterns.

| Condition | Result |
| --- | --- |
| No suspicious numbers found | ✅ Check passed |
| At least one suspicious number found | ❌ Check failed |
| A previously flagged PR is fixed | ✅ Check passed; report updated |

Deleted lines and unchanged context lines are ignored. By default, all file types are scanned.

### Matching Rules

The detector uses literal substring matching rather than numerical parsing or regular expressions.

For example:

| Added content | Result |
| --- | --- |
| `const value = 156;` | 🚨 Detected |
| `const value = 1156;` | 🚨 Detected (`156`) |
| `const value = 44;` | 🚨 Detected (`4`) |
| `const value = 999;` | ✅ Not detected |
| `// Nothing suspicious here` | ✅ Not detected |

The detector does not understand what the numbers mean. It simply believes that certain sequences of digits are inherently dangerous.

## Installation

1. Create the following file in your repository:

   `.github/workflows/weak-key-leak-detector.yml`

2. Copy the workflow configuration into that file.

3. Ensure GitHub Actions is enabled for the repository.

4. Allow the workflow to write pull request comments. The workflow requests the following permissions:

   - `contents: read`
   - `pull-requests: write`
   - `issues: write`

5. Open a pull request or push a new commit to an existing pull request to trigger the scan.

If you want this check to block merging, configure a branch protection rule or repository ruleset that requires the workflow's status check to pass.

## Example Alert

When suspicious numerical artifacts are found, the workflow posts a report similar to this:

> 🚨 **Weak-Key Material Detected!**
>
> **CRITICAL SECURITY ALERT:** This PR contains suspicious numerical artifacts associated with our extremely sophisticated CA weak-key detection system.
>
> **Required action:** Remove the offending numbers immediately. Our cryptographic experts (a very concerned hamster) insist that these values must never see the light of day.
>
> 🤡 **Scan result: FAILED.** The number police have been notified.

The report also includes a disclaimer explaining that the scanner is a joke and that its findings do not establish an actual security vulnerability.

## Limitations

This workflow is deliberately simplistic.

- It does not inspect X.509 certificates, public keys, private keys, or cryptographic parameters.
- It does not verify whether any CA incident actually occurred.
- It may produce false positives whenever one of the designated numbers appears in ordinary code, comments, documentation, or data.
- It may miss actual secrets and vulnerabilities that do not contain the designated patterns.
- It does not replace tools such as dedicated secret scanners, certificate validators, or static analysis tools.

**Do not rely on this workflow for security decisions.**

## Frequently Asked Questions

### Does this detect actual weak RSA keys?

No. It detects eight hard-coded numerical substrings. Cryptographic security is substantially more complicated than that.

### Why does the check fail when an innocent number appears?

The number police do not recognize innocence as a valid cryptographic property.

### Can I remove one of the suspicious numbers?

Technically, yes. However, the cryptographic hamster may request a formal incident review.

### Is this related to a real CA vulnerability?

The workflow is intended as satire inspired by discussions of CA weak-key incidents. Its matching rules are fictional and should not be interpreted as a representation of any actual vulnerability, affected certificate, or exposed key.

## License

Use, modify, and redistribute this workflow according to the license of the repository in which it is included.

No hamsters were consulted during the implementation of this security system.

---

*Security level: Numerically concerned.*

*Confidence level: Unreasonably high.*

*Actual cryptographic value: Approximately zero.*
