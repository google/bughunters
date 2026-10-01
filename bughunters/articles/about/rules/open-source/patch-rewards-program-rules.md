Welcome to the Patch Rewards Program rules page. The Patch Rewards Program
incentivizes developers to make proactive improvements to security in open
source projects, especially those that are important dependencies for Google and
the wider open source community. On this page, you can quickly and easily get
answers to any questions you may have about earning rewards by patching security
vulnerabilities in in-scope open source projects.

Looking for information on patch rewards for contributing to Tsunami? See the
[Tsunami Patch Rewards Program Rules](https://bughunters.google.com/about/rules/open-source/5067456626688000/tsunami-patch-rewards-program-rules)
for details.

### The projects in scope

Currently, the projects in-scope are as follows:

*   **Tier 1**: Please see the full list on
    [https://github.com/google/bughunters/blob/main/patch-rewards-program/scope.md](https://github.com/google/bughunters/blob/main/patch-rewards-program/scope.md)

*   **Tier 1**: Any **open source** project that receives a security
    vulnerability report from Google (such as from
    [Project Zero](https://googleprojectzero.blogspot.com/)) is eligible for
    **patches which contribute towards fixing the vulnerability**. Please
    include a link or reference ID for the vulnerability report.

*   **Tier 2**:
    [Projects integrated into OSS-Fuzz](https://github.com/google/oss-fuzz/tree/master/projects)
    *(Note: Rewards apply to qualifying patches within integrated projects; new
    project integrations and fuzz harnesses are not eligible).*

### Qualifying submissions

Patches that can be demonstrated and that improve the security of an in-scope
project, will be considered for a reward. Examples include:

-   Improvements to privilege separation or sandboxing
-   Memory allocator hardening
-   Cleanups of integer arithmetics
-   Systematic fixes for various types of race conditions
-   Elimination of error-prone design patterns or library calls
-   Implementation of contextual auto escaping in templates
-   Secure-by-design memory safety improvements such as:
    -   Adopting the
        [Safe Buffers Programming Model](https://clang.llvm.org/docs/SafeBuffers.html)
        to migrate from C-style buffers to C++ containers, including the use of
        `-Wunsafe-buffer-usage` to prevent backsliding
    -   Replacing C++ dependencies processing potentially untrusted inputs with
        equivalent Rust dependencies
    -   Building the scaffolding to enable writing new components in Rust, and
        demonstrating this capability by adding one feature in Rust
    -   Elimination of error-prone design patterns or library calls
    -   Rust <> C++ Bindings through the use of manual bindings or interop
        tooling such as [bindgen](https://rust-lang.github.io/rust-bindgen/),
        [cbindgen](https://github.com/mozilla/cbindgen), and
        [cxx](https://cxx.rs/); with accurate safety comments
    -   Refactoring Rust crates to minimize or eliminate unsafe code
    -   Improving the auditability and verifiability of Rust crates that use
        unsafe code, such as by encapsulating unsafe blocks within
        self-contained, safe abstractions
-   Changes to support nonce-based Content Security Policy adoption in web
    applications
    ([details](https://csp.withgoogle.com/docs/faq.html#csp-patches))
-   Refactorings that make it easier to reason about the security properties of
    the code
-   Reactive patches that merely address a single vulnerability may qualify, but
    will be reviewed on a case-by-case basis

Note: In general, we will not reward one-liner patches that fix non-exploitable
crashes. This includes crashes that can result from resource exhaustion/DOS.

> Tip: At the end of 2024, we started publishing
> [rewarded submissions to GitHub](https://github.com/google/bughunters/tree/main/patch-rewards-program/rewarded-patches).
> Check them out for further inspiration!

### Submitting to the program

To qualify, your patch should be submitted directly to the maintainers of the
project first, and you should work with them to get it accepted into their
repository without reverts for one month (please also note our other
[reward limitations](/about/rules/open-source/4928084514701312/patch-rewards-program-rules#reward-limitations)).
Once you've done this, please submit your report via our simple form.

[Submit your patch](/report/patch_rewards)

Please respect the time of your fellow volunteers, and stick closely to the
coding, testing, and submission standards for each project. Submissions made
before the patch has been accepted (without reverts for one month) will not be
considered for a reward.

When submitting your patch, please include links to all the relevant code
locations and diffs. And be sure to explain project-specific benefits offered by
your patch.

### Reward amounts

Qualifying submission rewards range from $100 to $15,000. The final amount is
always at the discretion of the Rewards Panel, and is based on their judgment of
the complexity and impact of the patch, as well as the
[project tier](https://github.com/google/bughunters/blob/main/patch-rewards-program/scope.md).
The reward amounts are:

<table border="2" bordercolor="#ffffff">
  <tr>
   <th>Category
   </th>
   <th width = "10%">Tier 1
   </th>
   <th width = "10%">Tier 2
   </th>
  </tr>
  <tr>
   <td>(S0) Complicated, high-impact improvements that almost certainly prevent major vulnerabilities in the affected code.
   </td>
   <td>$15,000
   </td>
   <td>$5,000
   </td>
  </tr>
  <tr>
   <td>(S1) Moderately complex patches that offer compelling security benefits.
   </td>
   <td>$7,500
   </td>
   <td>$1,337
   </td>
  </tr>
  <tr>
   <td>(S2) Submissions of modest complexity, or for ones that offer fairly speculative gains.
   </td>
   <td>$2,000
   </td>
   <td>$500
   </td>
  </tr>
    <tr>
   <td>(S3) "One-liner special" for smaller improvements that still have merit from a security standpoint.
   </td>
   <td>$500
   </td>
   <td>$100
   </td>
  </tr>
</table>

> We currently offer reward multipliers for memory-safety changes, excluding the
> "one-liner special" category, until the end of 2026:
>
> *   2x for secure-by-design memory safety improvements for
>     [tier 1 projects](https://github.com/google/bughunters/blob/main/patch-rewards-program/scope.md)
> *   3x for secure-by-design memory safety improvements done on
>     [tier 1 projects](https://github.com/google/bughunters/blob/main/patch-rewards-program/scope.md)
>     scoped as "Core infrastructure data parsers" (*not* cumulative with the 2x
>     multiplier)

The panel may split this reward between the submitter and the project
maintainers, though this is more likely if the patch requires a substantial
amount of effort on behalf of the dev team.

We also offer the option to donate rewards to charity. Rewards unclaimed after
12 months will be donated to a charity of our choice.

#### Reward Limitations

Before submitting, be aware of the following limitations applied to the Patch
Rewards Program:

-   Do not submit more than **3 submissions per month per person** (we encourage
    batched submissions)
-   Only submit patches that are **at least one month old** so that we know that
    maintainers haven't reverted the patch
-   Do not submit patches that are **more than 12 months old** as these are not
    eligible for a reward

We encourage you to combine your commits into a single Patch Rewards Program
submission to seek fewer larger rewards instead of many small rewards.

These limitations are applied at the panel's discretion.

## Code of conduct

To ensure a healthy and productive relationship between participants and the
Google teams interacting with them, we have defined a
[Code of Conduct](/about/rules/other/6009584292331520/code-of-conduct-for-our-vulnerability-reward-programs)
laying out the expected behaviors from both sides.

Thank you in advance for familiarizing yourself with this code and adhering to
its provisions!

### Frequently asked questions

*Q: The maintainers don't want my patch. Can you help me with this?*

A: Nope! It is up to the maintainers to decide whether or not to accept your
patch. Given the nature of the program we do not wish to second-guess the
decisions of project maintainers.

*Q: I'm a core developer working on one of the in-scope projects. Do my own
patches qualify?*

A: They most certainly do.

*Q: Why is there so little emphasis on fixing individual bugs?*

A: Quite a few vulnerabilities trace back to preventable coding mistakes, or are
made easier to exploit due to the absence of simple mitigation techniques. We're
aiming to address this :)

*Q: Can I make a submission privately? My hamster/partner/boss doesn't agree
with my security reports...*

A: Sure. However, if you receive and accept a reward we'll need your contact
details to process the payment. You can request not to be listed on our public
credits page.

## Tsunami patch rewards

See the standalone
[Tsunami Patch Rewards Program Rules](https://bughunters.google.com/about/rules/open-source/5067456626688000/tsunami-patch-rewards-program-rules)
for details.

## Legal

We are unable to receive reports and/or issue rewards to individuals or entities
that are on sanctions lists, or who are in territories subject to sanctions
(e.g., Cuba, Iran, North Korea, Syria, Crimea, and the so-called Donetsk
People's Republic and Luhansk People's Republic). Additionally, due to
administrative difficulties, we no longer issue rewards to individuals or
entities located in Russia or Belarus.

Unless otherwise authorized in advance, in order to qualify for a reward,
patches submitted to the reward program at any period of time may not utilize
Alphabet proprietary, confidential, or need-to-know information. We will
evaluate every submission on a case-by-case basis.

Participation in the program is restricted to individuals aged 18 and older. To
enable us to formally evaluate (and, if applicable, reward) your patch, if
you're under 18 years of age, please have a parent, guardian, or other trusted
adult submit the patch on your behalf.

You are responsible for any tax implications depending on your country of
residency and citizenship. There may be additional restrictions on your ability
to enter depending upon your local law.

If Google Payments is your selected payment option and you're not a US resident
for income tax purposes, you confirm that any services you provide to Google
won't be performed in the US. If you ever plan to provide services in the US,
please let us know in writing at least 90 days beforehand by emailing
STCnotices@google.com.

This is not a competition, it is an experimental and discretionary rewards
program. We reserve the right to cancel the program at any time. Paying rewards
is entirely at our discretion.

Please make sure your work does not violate any law(s) and does not disrupt or
compromise any data that does not belong to you.
