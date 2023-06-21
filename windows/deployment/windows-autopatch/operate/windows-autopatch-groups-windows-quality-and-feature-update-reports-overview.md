---
title: Windows quality and feature update reports overview with Windows Autopatch Groups experience
description: This article details the types of reports available and info about update device eligibility, device update health, device update trends in Windows Autopatch groups
ms.date: 05/01/2023
ms.prod: windows-client
ms.technology: itpro-updates
ms.topic: conceptual
ms.localizationpriority: medium
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.reviewer: adnich
ms.collection:
  - highpri
  - tier1
---

# Windows quality and feature update reports overview: Windows Autopatch groups experience (public preview)

> [!IMPORTANT]
> Windows Autopatch groups is in **public preview**. This feature is being actively developed and might not be complete. You can test and use these features in production environments and provide feedback.<p>The Windows Autopatch group experience only applies if you’ve opted-in to use Windows Autopatch groups.</p><br>**To opt-in to use Windows Autopatch groups:**<ol><li>Go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and select **Devices** from the left navigation menu.</li><li>Under **Windows Autopatch**, select **Release Management**, then select **Autopatch groups (preview)**.</li><li>Review the **[Microsoft Privacy Statement](../overview/windows-autopatch-privacy.md)** and the **[Autopatch groups Public Preview Addendum](../references/windows-autopatch-groups-public-preview-addendum.md)**. If you agree, select the **I have reviewed and agree to the Autopatch groups Public Preview Addendum** checkbox. Then, select **Use preview** to test out Windows Autopatch groups and its bundled feature set. If the **Use preview** option is greyed out, ensure you meet all the [Autopatch group prerequisites](../deploy/windows-autopatch-groups-manage-autopatch-groups.md#autopatch-groups-prerequisites).</li></ol>

## Windows quality reports

The Windows quality reports provide you with information about:

Quality update device readiness
Device update health
Device update alerts
Together, these reports provide insight into the quality update state and compliance of Windows devices that are enrolled into Windows Autopatch.

The Windows quality report types are organized into the following focus areas:

| Focus area | Description |
| ----- | ----- |
| Organizational | The [Summary dashboard](../operate/windows-autopatch-groups-windows-quality-update-summary-dashboard.md) provide the current update status summary for all devices.<p>The [Quality update status report](../operate/windows-autopatch-groups-windows-quality-update-status-report.md) provides the current update status of all devices at the device level. |
| Device trends | The [Quality update trending report](../operate/windows-autopatch-groups-windows-quality-update-trending-report.md) provides the update status trend of all devices over the last 90 days. |

## Windows feature update reports

The Windows feature update reports monitor the health and activity of your deployments and help you understand if your devices are maintaining update compliance targets.  

If update deployments aren’t successful, Windows Autopatch provides information on update deployment failures and who needs to remediate. Certain update deployment failures might require either Windows Autopatch to act on your behalf or you to fix the issue.

The Windows feature update report types are organized into the following focus areas:

| Focus area | Description |
| ----- | ----- |
| Organizational | The [Summary dashboard](../operate/windows-autopatch-groups-windows-feature-update-summary-dashboard.md) provides a broader view of the current Windows OS upgrade status for all devices registered with Windows Autopatch. |
| Operational | The [Feature update status report](../operate/windows-autopatch-groups-windows-feature-update-status-report.md) provides a per device view of the current Windows OS update status for all devices registered with Windows Autopatch. |
| Device trends | The [Quality update trending report](../operate/windows-autopatch-groups-windows-feature-update-trending-report.md) provides a visual representation of Windows OS upgrade trends for all devices over the last 90 days. |

## Who can access the reports?

Users with the following permissions can access the reports:

- Global Administrator
- Intune Service Administrator
- Global Reader
- Services Support Administrator

## About data latency

The data source for these reports is Windows [diagnostic data](../overview/windows-autopatch-privacy.md#microsoft-windows-1011-diagnostic-data). The data typically uploads from enrolled devices once per day. Then, the data is processed in batches before being made available in Windows Autopatch. The maximum end-to-end latency is approximately 48 hours.

## Windows quality and feature update statuses

The following statuses are used throughout the Windows Autopatch reporting suite to describe the quality update status for devices:

- [Up to Date devices](#up-to-date-devices)
- [Not up to Date devices](#not-up-to-date-devices)
- [Not Ready devices](#not-ready-devices)

Each status has its own set of sub statuses to further describe the status.

### Up to Date devices

Up to date devices are devices that meet all of the following prerequisites:

- [Prerequisites](../prepare/windows-autopatch-prerequisites.md)
- [Prerequisites for device registration](../deploy/windows-autopatch-register-devices.md#prerequisites-for-device-registration)
- [Windows quality and feature update device readiness](../deploy/windows-autopatch-post-reg-readiness-checks.md)
- [Post-device readiness checks](../deploy/windows-autopatch-post-reg-readiness-checks.md)
- Have applied the current monthly cumulative updates

> [!NOTE]
> [Up to Date devices](#up-to-date-devices) will remain with the **In Progress** status for the 21-day service level objective period until the device either applies the current monthly cumulative update or receives an [alert](../operate/windows-autopatch-device-alerts.md). If the device receives an alert, the device’s status will change to [Not up to Date](#not-up-to-date-devices).

#### Up to Date sub statuses

| Sub status | Description |
| ----- | ----- |
| In Progress | Devices are currently installing the latest [quality update](../operate/windows-autopatch-groups-windows-quality-update-overview.md#release-schedule) or [feature update](../operate/windows-autopatch-groups-windows-feature-update-overview.md#default-release) deployed through the Windows Autopatch release schedule. |
| Paused | Devices that are currently paused due to a Windows Autopatch or customer-initiated Release management pause. For more information, see pausing and resuming a [Windows quality update](../operate/windows-autopatch-groups-windows-quality-update-overview.md#pause-and-resume-a-release) or [Windows feature update](../operate/windows-autopatch-groups-manage-windows-feature-update-release.md#pause-and-resume-a-release). |

### Not up to Date devices

Not Up to Date means a device isn’t up to date when the:

- Quality or feature update is out of date, or the device is on the previous update.
- Device is more than 21 days overdue from the last release.
- Device has an [alert](../operate/windows-autopatch-device-alerts.md) resulting in an error and action must be taken.

### Not Ready devices

Not Ready refers to the responsibility of the designated IT administrator to carry out the appropriate action to resolve the reported device sub status.

Within each 24-hour reporting period, devices that are Not Ready are reevaluated using the [Autopatch post-device registration readiness checks](../deploy/windows-autopatch-post-reg-readiness-checks.md).

## Data export

Select **Export devices** to export data for each report type. Only selected columns will be exported.
