---
title: Configure the Application Identity service
description: This topic for IT professionals shows how to configure the Application Identity service to start automatically or manually.
ms.reviewer: 
ms.author: vinpa
ms.prod: windows-client
ms.localizationpriority: medium
author: vinaypamnani-msft
manager: aaroncz
ms.topic: conceptual
ms.date: 07/01/2021
ms.technology: itpro-security
---

# Configure the Application Identity service

>[!NOTE]
>Some capabilities of Windows Defender Application Control are only available on specific Windows versions. Learn more about the [Windows Defender Application Control feature availability](/windows/security/threat-protection/windows-defender-application-control/feature-availability).

This topic for IT professionals shows how to configure the Application Identity service to start automatically or manually.

The Application Identity service determines and verifies the identity of an app. Stopping this service will prevent AppLocker policies from being enforced.

>**Important:**  When using Group Policy, you must configure it to start automatically in at least one Group Policy Object (GPO) that applies AppLocker rules. This is because AppLocker uses this service to verify the attributes of a file.
 
**To start the Application Identity service automatically using Group Policy**

1.  On the **Start** screen, type **gpmc.msc** to open the Group Policy Management Console (GPMC).
2.  Locate the GPO to edit, right-click the GPO, and then click **Edit**.
3.  In the console tree under **Computer Configuration\\Windows Settings\\Security Settings**, click **System Services**.
4.  In the details pane, double-click **Application Identity**.
5.  In **Application Identity Properties**, configure the service to start automatically.

Membership in the local **Administrators** group, or equivalent, is the minimum access required to complete this procedure.

**To start the Application Identity service manually**

1.  Right-click the taskbar, and click **Task Manager**.
2.  Click the **Services** tab, right-click **AppIDSvc**, and then click **Start Service**.
3.  Verify that the status for the Application Identity service is **Running**.

Starting with Windows 10, the Application Identity service is now a protected process. Because of this, you can no longer manually set the service **Startup type** to **Automatic** by using the Services snap-in. Try either of these methods instead:

- Open an elevated command prompt or PowerShell session and type:

   ```powershell
   sc.exe config appidsvc start= auto
   ```

- Create a security template that configures appidsvc to be automatic start, and apply it using secedit.exe or LGPO.exe.
