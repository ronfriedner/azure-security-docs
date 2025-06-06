---
title: Overview of improving operating system baseline configurations in Microsoft Defender for Cloud
description: Learn how to improve operating system baseline configurations in Microsoft Defender for Cloud
ms.topic: how-to
ms.author: dacurwin
author: dcurwin
ms.date: 03/10/2025
---

# Operating system misconfigurations

Microsoft Defender for Cloud provides security recommendations to improve organizational security posture and reduce risk. An important element in risk reduction is to harden machines across your business environment.

## Assessment (Azure Machine Configuration extension)

Defender for Cloud assesses and enforces best-practice security configurations using [built-in Azure policy initiatives](policy-reference.md). The [Microsoft Cloud Security Benchmark (MCSB)](/security/benchmark/azure/introduction) is Defender for Cloud's default initiative.

MCSB includes compute security baselines for [Windows](/azure/governance/policy/samples/guest-configuration-baseline-windows) and [Linux](/azure/governance/policy/samples/guest-configuration-baseline-linux) operating systems.

Operating system recommendations based on these MCSB compute security baselines aren't included as part of Defender for Cloud's [free foundational security posture capabilities](concept-cloud-security-posture-management.md#cspm-plans)

- The recommendations are available when Defender for Servers Plan 2 is enabled.
- When Defender for Servers Plan 2 is enabled, relevant Azure policies are enabled on the subscription:

  - "Windows machines should meet requirements of the Azure compute security baseline"
  - "Linux machines should meet requirements for the Azure compute security baseline"

- Make sure you don't remove these policies or you won't be able to leverage the machine configuration extension that's used to collect machine data.

### Data collection

Machine information is gathered for assessment using the Azure machine configuration extension (formerly known as the Azure Policy guest configuration) running on the machine.

### Installing the machine configuration extension

The machine configuration extension is installed as follows:

- **Azure**: On Azure machines, install by remediating the recommendation [Guest Configuration extension should be installed on machines](https://portal.azure.com/#blade/Microsoft_Azure_Security/RecommendationsBlade/assessmentKey/6c99f570-2ce7-46bc-8175-cde013df43bc).
- **AWS/GCP**: On AWS and GCP machines, the machine configuration is installed by default when you select Arc provisioning in the [AWS](quickstart-onboard-aws.md) or [GCP](quickstart-onboard-gcp.md) connector.
- **On-premises**: For on-premises machines, the machine configuration is enabled by default when you [onboard on-premises VMs as Azure Arc-enabled VMs](/azure/azure-arc/servers/learn/quick-enable-hybrid-vm).
- **Azure VMs**: On Azure VMs only (not Arc-enabled VMs) you must assign a managed identity to the machine by remediating recommendation [Virtual machines Guest Configuration extension should be deployed with system-assigned managed identity](https://portal.azure.com/#blade/Microsoft_Azure_Security/RecommendationsBlade/assessmentKey/69133b6b-695a-43eb-a763-221e19556755).

### What's not included

Additional features provided by the extension machine outside Defender for Cloud aren't included, and are subject to Azure Policy machine configuration pricing.

- For example, [remediation](/azure/governance/machine-configuration/concepts/remediation-options) and [custom policies](/azure/governance/machine-configuration/how-to/create-policy-definition).
- [Review details](https://azure.microsoft.com/pricing/details/azure-policy/?msockid=06fc23a2aac2601229353214abbf61f1) on the Azure Policy machine configuration pricing page.

## Assessment (Defender Vulnerability Management)

Microsoft Defender for Cloud integrates natively with Microsoft Defender for Endpoint and Microsoft Defender Vulnerability Management to provide machines with vulnerability protection, and endpoint detection and response (EDR) capabilities.

As part of that integration, [security baselines assessment](/defender-vulnerability-management/tvm-security-baselines) is provided by Defender Vulnerability Management.

- Security baselines assessment uses customized security baseline profiles.
- Profiles are basically a template that consists of device configuration settings, and benchmarks against which to compare them.

### Support

- Assessing devices against the Defender Vulnerability Management security baselines assessment profiles is currently available in public preview.
- Defender for Servers Plan 2 must be enabled, and the Defender for Endpoint agent must be running on machines you want to assess.
- Assessment is supported for machines running security baseline profiles:

  - windows_server_2008_r2
  - windows_server_2016
  - windows_server_2019
  - windows_server_2022

### Reviewing recommendations

To review recommendations made by security baseline assessments, search for the recommendation **Machines should be configured securely (powered by MDVM)", and view the recommendation for all resources.

## Next steps

- [Install the Azure Policy machine configuration](security-baseline-guest-configuration.md).
- [Remediate](apply-security-baseline.md) OS baseline misconfigurations.
