---
title: Packaged apps and packaged app installer rules in AppLocker
description: This topic explains the AppLocker rule collection for packaged app installers and packaged apps.
ms.reviewer: 
ms.author: vinpa
ms.prod: windows-client
ms.localizationpriority: medium
author: vinaypamnani-msft
manager: aaroncz
ms.topic: conceptual
ms.date: 10/13/2017
ms.technology: itpro-security
---

# Packaged apps and packaged app installer rules in AppLocker

>[!NOTE]
>Some capabilities of Windows Defender Application Control are only available on specific Windows versions. Learn more about the [Windows Defender Application Control feature availability](/windows/security/threat-protection/windows-defender-application-control/feature-availability).

This topic explains the AppLocker rule collection for packaged app installers and packaged apps.

Universal Windows apps can be installed through the Microsoft Store or can be sideloaded using the Windows PowerShell cmdlets. Universal Windows apps can be installed by a standard user unlike some Classic Windows applications that sometimes require administrative privileges for installation.
Typically, an app consists of multiple components - the installer used to install the app and one or more exes, dlls or scripts. With Classic Windows applications, not all those components always share common attributes such as the publisher name, product name and product version. Therefore, AppLocker has to control each of these components separately through different rule collections - exe, dll, script and Windows Installers. In contrast, all the components of a Universal Windows app share the same attributes: Publisher name, Package name and Package version. It's therefore possible to control an entire app with a single rule.

AppLocker enforces rules for Universal Windows apps separately from Classic Windows applications. A single AppLocker rule for a Universal Windows app can control both the installation and the running of an app. Because all Universal Windows apps are signed, AppLocker supports only publisher rules for Universal Windows apps. A publisher rule for a Universal Windows app is based on the following attributes of the app:

-   Publisher name
-   Package name
-   Package version

In summary, including AppLocker rules for Universal Windows apps in your policy design provides:

-   The ability to control the installation and running of the app
-   The ability to control all the components of the app with a single rule rather than controlling individual binaries within the app
-   The ability to create application control policies that survive app updates
-   Management of Universal Windows apps through Group Policy.
