The Android and Google Devices Security Reward Program is a collaborative
initiative designed to secure the Android ecosystem and Google hardware. We
partner with the global security research community to identify, responsibly
disclose, and effectively remediate high-impact vulnerabilities.

To adapt to the evolving vulnerability landscape, this program is structured
around user impact. We are revising our program scope to emphasize categories
that represent the highest risk to our users, and we are also prioritizing
categories that remain more challenging for automated AI tooling, to ensure we
reward researchers for their unique skills and talents.

We require submissions to demonstrate clear user risk and include a functional
Proof of Concept (PoC). We also offer significant incentives for reports that
provide concrete patch suggestions. By focusing our rewards on high-impact
vulnerabilities, we can quickly direct our engineering teams to fix the issues
that matter most to our users' safety.

## Scope and Eligibility

The scope of this program is strictly limited to the devices and software
platforms listed below.

**Active Hardware Targets** – To be eligible for evaluation, vulnerabilities
must reproduce on the latest publicly available build of the following supported
devices:

**Pixel Families**

*   Pixel phones, Pixel Tablets, and Pixel Watches

**Smart Home and Google Nest**

*   Nest Cameras, Speakers, Displays, Thermostats, and Routers

**Fitbit**

*   Fitbit Trackers and Smartwatches

*(Note: Devices that will reach the end of their guaranteed security update
window within 90 days are out of scope).*

**Platform and Software Scope** – The program covers vulnerabilities within the
device software stack, including but not limited to:

*   Android Open Source Project (AOSP) code
*   Android TV, WearOS, Android Automotive OS (AAOS), and GooglebookOS
*   OEM proprietary code and drivers shipped on eligible devices
*   The Trusted Execution Environment (TEE), Secure Elements (e.g., Titan M2),
    bootloaders, and device firmware (including SoC, MCU, and radio units)

**Out-of-Scope Components**

*   **Generic Linux Vulnerabilities:** Vulnerabilities in the upstream Linux
    kernel or generic Linux components are out of scope unless the reporter
    provides a functional Proof of Concept demonstrating a direct, exploitable
    impact specifically on Android or Pixel-maintained modules.
*   **Backend Services:** Vulnerabilities affecting Google infrastructure,
    backend APIs, or server-side services interacting with these devices are out
    of scope for this program. These must be reported to the broader
    [Google and Alphabet Vulnerability Reward Program](https://bughunters.google.com/about/rules/google-friends/google-and-alphabet-vulnerability-reward-program-vrp-rules).

## Qualifying Vulnerabilities

To help us focus on the most critical threats, we evaluate submissions based on
their realistic impact to users. To qualify for standard financial rewards, your
report must demonstrate significant risk by achieving one of the designated
impact categories below. Reports that rely on highly improbable preconditions or
unrealistic user interaction generally do not qualify.

However, submissions that fall below these impact thresholds can still be
valuable. While they might not qualify for top-tier rewards, we review them on a
case-by-case basis and may issue discretionary bounties if they lead to a
meaningful security improvement.

### In-Scope Impact

To provide clarity on what constitutes "significant, realistic user risk," and
to qualify for financial rewards, submissions must demonstrate substantial
impact. We explicitly accept and reward vulnerabilities that achieve the
following outcomes:

**Code Execution, Memory Safety & Virtualization**

*   **Arbitrary Code Execution:** Remote or local code execution across
    privileged, unprivileged, or constrained contexts, including TEE, Secure
    Elements, and hypervisors.
*   **pKVM Boundary Defeats:** Code execution or information disclosure across
    pKVM boundaries (e.g., Host to Hypervisor/pVM, or pVM to Host).
*   **Deserialization & Gadget Chains:** Viable gadget chains (e.g., Parcel
    Mismatch) within the Android Framework leading to code execution or
    significant side-effects.
*   **Data Leakage:** Unsafe memory reads leaking sensitive PII.
*   **Exploited in the Wild:** Any vulnerability serving as a critical foothold
    for an exploit chain, or demonstrating active exploitation in the wild
    (ITW).

**Privilege Escalation & Permissions**

*   **Permission Bypasses:** Bypassing system, signature, or dangerous
    permissions to obtain sensitive user data from the device, or preventing the
    revocation of sensitive permissions.
*   **Special App Access:** Unauthorized acquisition/prevention of revocation of
    privileged Special App Access.
*   **While-In-Use (WIU) Abuse:** Retaining sensitive WIU/One-Time permissions
    past process death or reboot, or launching services from background with
    undesired access to sensitive WIU permissions.

**UI, Activity, & Multi-User Security**

*   **Activity & Intent Spoofing:** Arbitrary launch of non-exported sensitive
    activities, unprivileged background Foreground Service (FGS) launches to
    gain while-in-use permissions, or valid bypasses of Intent Redirect
    hardening.
*   **UI Obfuscation & Tapjacking:** Tapjacking or overlaying
    privacy/security-sensitive screens, deceptive rendering to misrepresent UI
    authenticity, hiding privacy-sensitive system indicators (e.g., toasts), or
    bypassing `FLAG_SECURE`.
*   **Multi-User & Private Space:** Cross-user sensitive data access, or
    unlocking Private Space without the designated lock factor.

**Device Management & Denial of Service**

*   **Enterprise Bypasses:** Unauthorized removal of the Device Policy
    Controller (DPC).
*   **Destructive Remote DoS:** Remote persistent/permanent Denial of Service
    requiring a factory reset, permanent deletion of User/Profile state,
    uninstalling apps without interaction, or causing an app to repeatedly
    call/prevent calling emergency services.

### Published Threat Models and Non-Bugs

To help you focus your research on actionable, high-impact areas, we publish a
comprehensive list of accepted
[architectural risks, expected behaviors](https://source.android.com/docs/security/overview/updates-resources)
(e.g., actions permitted under the Android user consent model), and
[known non-bugs](https://bughunters.google.com/learn/invalid-reports/about-this-section)
(e.g., phishing).

Please review these published threat models prior to submission. Reports
identifying issues already classified on this list will be closed as
unactionable and are not eligible for a reward. To help us keep the triage queue
moving quickly for the whole community, accounts that repeatedly submit known
non-bugs or out-of-scope reports may experience automated rate limiting or
slower response times.

## Submission & PoC Guidelines

To ensure we can quickly verify and remediate vulnerabilities, we require all
submissions to be actionable from the moment they are filed. Reports that do not
meet these requirements will be closed.

**Proof of Concept (PoC) Requirements** – A functional Proof of Concept (PoC)
must be included with your initial report. To help us reproduce the issue
quickly, please provide the PoC as a machine-readable attachment (e.g., .zip,
.md, or executable scripts).

Reports consisting solely of theoretical attack paths, speculative assumptions,
or raw, un-minimized fuzzer crashes are not actionable and will be closed.
Similarly, incomplete "shell" reports filed simply to secure a timestamp will be
superseded by the first complete, actionable submission.

*(Note: For vulnerabilities strictly relying on UI-based interactions, a
high-quality video demonstration with step-by-step instructions is acceptable in
place of a code-based PoC).*

**Patch and Remediation Guidelines** – Providing a functional code fix or
concrete patch suggestion directly impacts your reward evaluation.

*   **Memory Corruption:** A proposed patch or root-cause code fix is mandatory
    for all memory safety vulnerabilities.
*   **Framework / Logic Flaws:** Patch suggestions are highly encouraged, though
    not strictly required, for complex Android framework issues.

Reports that lack a proposed fix for mandatory categories risk being deemed
ineligible for financial reward or will result in a drastically reduced payout.

## Reward Amounts & Payout Structure

We compensate researchers based on the demonstrable impact, reliability, and
completeness of their submissions. Our payout structure is designed to heavily
reward exceptional, novel exploit chains while utilizing a dynamic,
market-adjusted model for standard vulnerability classes.

### Top-Tier Exploit Chains

For exceptional vulnerabilities that demonstrate a severe, systemic compromise
of our most secure environments, we offer our highest reward ceilings. To
qualify, these exploits must be novel, highly reliable, and achieve specific
outcomes (such as zero-click remote code execution or data exfiltration from
isolated elements). The reward ceilings listed below represent the absolute
maximum payouts achievable, which include bonuses for successfully demonstrating
your exploit chain against specific developer preview versions of Android.

<table border="2" bordercolor="#ffffff">
        <tr>
          <th>
            Description
          </th>
          <th>
            Maximum Reward
          </th>
        </tr>
        <tr>
          <td>
            Titan M2 with Persistence
          </td>
          <td>
            Up to $1,500,000
          </td>
        </tr>
        <tr>
          <td>
            Titan M2 without Persistence
          </td>
          <td>
            Up to $750,000
          </td>
        </tr>
        <tr>
          <td>
            Secure Element Data Exfiltration
          </td>
          <td>
            Up to $375,000
          </td>
        </tr>
        <tr>
          <td>
            Software-Based Lockscreen Bypass
          </td>
          <td>
            Up to $150,000
          </td>
        </tr>
</table>

<p></p>

### Standard Bounty Ranges and Multipliers

While we reserve our highest reward ceilings for full, end-to-end exploit
chains, we still heavily value high-impact individual vulnerabilities. To adapt
to the rapid pace of automated vulnerability discovery, we have shifted to a
dynamic reward structure for these standalone submissions.

Rather than publishing static price sheets for single vulnerabilities, we
evaluate each report dynamically. Your final reward is a multiplier of an
adjustable baseline, assessed based on the specific risk impact, actionability,
and quality of your report. Under this dynamic structure, exceptional standalone
submissions—such as those detailing genuinely novel research or previously
undiscovered primitives—can reach up to $25,000.

### Evaluation Criteria for Maximum Payouts

To achieve the maximum multiplier within a given tier, your report must excel in
the following areas:

*   **Actionability (Proposed Fix):** You provide a functional code fix or a
    concrete, viable patch suggestion that directly addresses the root cause.
*   **Reliability:** Your PoC functions reliably against the latest builds on
    supported hardware without requiring complex manual environment
    manipulation.
*   **Impact:** The vulnerability demonstrates clear, realistic user risk that
    actively bypasses existing modern mitigations.
*   **Timing (Developer Previews):** Catching bugs before they ship is
    incredibly valuable to us. Successfully demonstrating your full exploit
    chain against specific developer preview versions of Android is the key to
    unlocking the absolute highest reward ceilings listed above.

### The Exceptional Research Bonus

We actively seek out research that breaks new ground. If a submission reveals a
genuinely novel attack primitive or targets an undocumented architectural
oversight, the VRP panel reserves the right to apply a Novelty Bonus. This bonus
can elevate the final payout, regardless of the initial categorization.

### Reward Adjustments for Known and Trending Issues

Reports that lack a proposed fix or fail to reproduce reliably will result in a
drastically reduced reward multiplier, potentially resulting in a strictly
nominal payout.

Additionally, we actively track trending vulnerability classes and exploit
methodologies. We reserve the right to freeze or enforce strict payout caps for
specific exploit chains or vulnerability types if the underlying root cause is
already known and under active, comprehensive remediation by our engineering
teams.

## How We Handle Duplicate Reports

To disincentivize the submission of incomplete "shell" reports, the date and
time a report is created is not the sole factor in determining the canonical
submission for a security issue.

**The First Actionable Report** – The first actionable submission is considered
the canonical report. A report becomes actionable only when it meets all
baseline requirements, including a functional Proof of Concept (PoC) and
sufficient technical detail for immediate triage.

**Shell Reports and Internal Discovery** – Reports submitted prematurely without
a PoC, simply to secure a timestamp in the bug tracker, will be superseded. If a
later external submission—or an internal discovery by Google's automated
systems—provides the functional PoC and root-cause analysis before the initial
reporter updates their submission, the incomplete report will be marked as a
duplicate and will not qualify for a reward.

**Collaborative Triage and Shared Credit –** While the earliest actionable
report generally receives the full reward, we recognize that exceptional
subsequent submissions can drastically accelerate our remediation efforts. If a
later report, initially flagged as a duplicate, provides a technically superior
PoC, a more comprehensive root-cause analysis, or a viable patch that
engineering actively uses to resolve the vulnerability, the VRP panel reserves
the right to split the final financial reward between the canonical reporter and
the subsequent reporter.

Additionally, researchers who provide substantial, actionable intelligence on a
duplicated vulnerability may be granted shared acknowledgment on the resulting
CVE, ensuring their contributions to the ecosystem are officially recognized.

## Legal and Policy Guidelines

To protect both the research community and our users, all participation in the
Android and Google Devices Security Reward Program must adhere to the following
guidelines. Failure to comply with these terms may result in disqualification.

**Authorized Testing** Research must be conducted exclusively on devices you own
or have explicit permission to test. You must not attempt to exploit or
compromise the devices, accounts, or data of other users. Testing must not
negatively impact the availability or integrity of Google’s services or
infrastructure. If your research inadvertently accesses sensitive user data or
proprietary infrastructure, you must halt testing immediately, delete any local
copies of such data, and report the incident to Google.

**Responsible Disclosure** Researchers must provide Google with a reasonable
period of time to remediate a vulnerability before publishing technical details
or releasing exploit code publicly. Coordinated disclosure ensures that our
mutual priority remains the security of the end user. Publicly disclosing a
vulnerability before a patch is available, or without prior written agreement
with Google, will result in immediate disqualification from financial reward and
potential removal from the program.

**Code of Conduct and Account Reputation (SNR)** To ensure our engineering
resources remain dedicated to genuine threats, we actively monitor the
Signal-to-Noise Ratio (SNR) of all participating researchers. Submitting
frivolous "shell" reports, submitting unverified, automated, or AI-generated
"hallucinated" findings, or repeatedly ignoring the Published Threat Models are
considered violations of our
[Code of Conduct](https://bughunters.google.com/about/rules/other/code-of-conduct-for-our-vulnerability-reward-programs).
Accounts demonstrating a low SNR will be subject to automated rate limiting
(e.g., a strict cap on active reports) and may face permanent removal from the
program.

**Program Eligibility** To receive a financial reward, you must be eligible
under applicable laws.

We cannot issue rewards to individuals on sanctions lists or residing in
countries under current comprehensive United States embargoes (including but not
limited to Cuba, Iran, North Korea, Syria, Crimea, and the Luhansk/Donetsk
regions). Due to administrative and banking restrictions, we also cannot issue
rewards to individuals in Russia or Belarus.

Unless otherwise authorized in advance, in order to qualify for a reward,
reports submitted to the VRP at any period of time may not utilize Alphabet
proprietary, confidential, or need-to-know information. We will evaluate every
submission on a case-by-case basis.

Participation in the program is restricted to individuals aged 18 and older. To
enable us to formally evaluate (and, if applicable, reward) your report, if
you're under 18 years of age, please have a parent, guardian, or other trusted
adult submit the report on your behalf.

If you are employed by a hardware or software vendor partnered with Google, you
are ineligible for rewards for vulnerabilities found in products, code, or
services related to your employer’s partnership with Google.

**Taxes and Financial Liability** All reward amounts are considered taxable
income in most jurisdictions. You are solely responsible for any tax
implications and reporting requirements associated with your payout. This
program is discretionary; Google reserves the unilateral right to cancel or
modify the program at any time, and the decision to pay a reward is entirely at
our discretion. All reward amounts and eligibility determinations are final.

If Google Payments is your selected payment option and you're not a US resident
for income tax purposes, you confirm that any services you provide to Google
won't be performed in the US. If you ever plan to provide services in the US,
please let us know in writing at least 90 days beforehand by emailing
STCnotices@google.com.

Participation in this Program does not create an employment, partnership, or
agency relationship.

To avoid potential conflicts of interest, we will not grant rewards to people
employed by Google or Google Partner companies who develop code for devices
covered by this program.

*Last Updated: October 2026*
