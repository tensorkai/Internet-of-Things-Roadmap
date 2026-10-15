# 05 · Trust and lifecycle

[← Requirements and tradeoffs](04-requirements-and-tradeoffs.md) · **Lesson 5 of 6** · [Next: Design studio →](06-design-studio.md)

> **Learning goal:** identify what needs protection, who can act, and who supports the device after installation.

## Start with assets and boundaries

A threat model is a structured way to ask what could go wrong and what you will do about it. For this introductory exercise, use four questions:

1. **What matters?** Measurements, device credentials, configuration, output control, and service availability.
2. **Who should have access?** The device, the owner, a viewer, and an administrator may need different permissions.
3. **Where does trust change?** Across device-to-service and browser-to-service connections, and when someone physically handles a board.
4. **How will you notice a problem?** Logs, rejected requests, device health, and missing data.

Security must be part of product planning, not only a last-minute transport setting. NIST's revised manufacturer guidance addresses foundational cybersecurity activities for IoT products ([Fagan et al., 2026](../references.md#ref-lifecycle)).

## Map capabilities to concrete questions

NIST's device baseline identifies six capability areas ([Fagan et al., 2020](../references.md#ref-security)). Here is how to ask about them in our room-monitor design:

| Capability | Question for this project |
| --- | --- |
| Device identification | Can the service distinguish room-01 from room-02? |
| Device configuration | Who can change the sampling interval? |
| Data protection | How are credentials and readings protected? |
| Logical access to interfaces | Which messages may each identity send or receive? |
| Software update | Who may install firmware, and how is it validated? |
| Cybersecurity state awareness | How can the owner learn about a security-relevant condition? |

These are planning questions, not a claim that our paper design implements the baseline.

## Identity is not permission

**Authentication** asks who a participant is. **Authorization** asks what that participant may do.

In our example policy, room-01 can publish its own measurements and receive commands addressed to it. It cannot publish as room-02. A viewer can read the room's history but cannot change settings. An administrator can change settings and revoke a device credential.

Encrypting a connection does not decide these permissions. A system needs explicit rules, and later tests must show that disallowed actions are rejected. Keep real credentials out of the workbook and repository.

## Make a small risk register

The following risks and controls are original examples for this project.

| Risk | Consequence | Proposed control | Evidence needed later |
| --- | --- | --- | --- |
| Device credential is copied | Someone submits false readings | Separate credentials and a revocation process | Revoke one test device and confirm rejection |
| Viewer can send commands | Unauthorized output changes | Separate view and control permissions | Viewer command is denied |
| Old value appears current | User trusts an outdated condition | Visible age and stale/invalid status | Stop samples and observe status |
| Someone accesses a debug connector | Firmware or secrets may be exposed | Assess physical access and debug configuration | Document exposed interfaces and protections |
| Update is interrupted | Device may stop operating | Select a supported recovery design | Later perform an authorized recovery test |

A proposed control is not evidence that the risk is gone. Keep the residual risk and verification status visible.

## Privacy is about the data's purpose

A room identifier, detailed timestamps, and temperature patterns may reveal information about a space's use. That is a possible inference in this scenario, not proof that temperature alone reliably identifies occupancy.

Ask whether you need each field, who can see it, and when it is deleted. The NIST Privacy Framework treats privacy risk as a design and data-processing concern, distinct from simply securing access ([National Institute of Standards and Technology, 2020](../references.md#ref-privacy)).

For our learning design, collect a pseudonymous device ID, temperature, status, and timing information. Do not add occupant names, audio, or precise location unless a justified use case requires them.

| Data | Purpose | Example access | Example retention |
| --- | --- | --- | --- |
| Temperature and timestamps | Recent room history | Authorized owner/viewer | Seven days, then daily cleanup |
| Device configuration | Operate the monitor | Owner/admin; device reads its settings | Until changed or retired |
| Credentials | Authenticate the device | Restricted provisioning/service components | Until rotation or revocation |
| Diagnostic logs | Diagnose failures | Maintainer | Choose a bounded period; omit secrets |

## Plan the end of the story

Write a lifecycle sequence: **provision → operate → update → recover → transfer or retire**.

Who installs the device? Who replaces a failed power supply? Who answers when the dashboard stops updating? How long are updates planned? What happens when the owner changes? When retiring a device, revoke its access and apply the data-deletion policy.

For now, record these responsibilities and unanswered questions. The [deployment module](../../13-deployment-and-device-lifecycle/README.md) later turns them into implementation work.

## Try it yourself

Complete workbook section E with three risks, one role-permission table, and a data inventory. Add support ownership, a proposed support lifetime, and retirement steps. Include at least one physical-access risk.

## Check your reasoning

**Question:** Every device uses an encrypted connection and the same password. What problem remains?

<details>
<summary>Reveal the explanation</summary>

If that shared credential is exposed, multiple devices may be impersonated. Revoking it can disrupt all devices using it. Separate credentials make selective revocation possible, provided the service enforces the associated permissions.

Encryption also does not prevent an authorized viewer from seeing data you unnecessarily collected. Data minimization and access control answer different questions.

</details>

**Keep:** a risk register, data inventory, permission policy, and lifecycle notes.  
[Next: Design studio →](06-design-studio.md)
