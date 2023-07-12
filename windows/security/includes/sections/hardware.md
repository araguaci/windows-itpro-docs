---
author: paolomatarazzo
ms.author: paoloma
ms.date: 06/06/2023
ms.topic: include
---

## Hardware Root-Of-Trust

| Security Measures | Features & Capabilities |
|:---|:---|
| **[Windows Defender System Guard](../../hardware-security/how-hardware-based-root-of-trust-helps-protect-windows.md)** | In Secured-core PCs, Windows Defender System Guard Secure Launch protects bootup with a technology known as the Dynamic Root of Trust for Measurement (DRTM). With DRTM, the system initially follows the normal UEFI Secure Boot process. However, before launching, the system enters a hardware-controlled trusted state that forces the CPU(s) down a hardware-secured code path. If a malware rootkit/bootkit has bypassed UEFI Secure Boot and resides in memory, DRTM will prevent it from accessing secrets and critical code protected by the virtualization-based security environment. Firmware Attack Surface Reduction technology can be used instead of DRTM on supporting devices such as Microsoft Surface. |
| **[Trusted Platform Module (TPM) 2.0](/windows/security/information-protection/tpm/trusted-platform-module-overview)** | TPMs provide security and privacy benefits for system hardware, platform owners, and users. Windows Hello, BitLocker, Windows Defender System Guard, and other Windows features rely on the TPM for capabilities such as key generation, secure storage, encryption, boot integrity measurements, and attestation. The 2.0 version of the specification includes support for newer algorithms, which can improve driver signing and key generation performance.<br><br>Starting with Windows 10, Microsoft's hardware certification requires all new Windows PCs to include TPM 2.0 built in and enabled by default. With Windows 11, both new and upgraded devices must have TPM 2.0. |
| **[Microsoft Pluton security processor](/windows/security/information-protection/pluton/microsoft-pluton-security-processor)** | Microsoft Pluton security processors are designed by Microsoft in partnership with silicon partners. Pluton enhances the protection of Windows devices with a hardware root-of-trust that provides additional protection for cryptographic keys and other secrets. Pluton is designed to reduce the attack surface as it integrates the security chip directly into the processor. It can be used with a discreet TPM 2.0, or as a standalone security processor. When root of trust is located on a separate, discrete chip on the motherboard, the communication path between the root-of-trust and the CPU can be vulnerable to physical attack. Pluton supports the TPM 2.0 industry standard, allowing customers to immediately benefit from the enhanced security in Windows features that rely on TPMs including BitLocker, Windows Hello, and Windows Defender System Guard.<br><br>In addition to providing root-of trust, Pluton also supports other security functionality beyond what is possible with the TPM 2.0 specification, and this extensibility allows for additional Pluton firmware and OS features to be delivered over time via Windows Update. Pluton-enabled Windows 11 devices are available and the selection of options with Pluton is growing. |

## Silicon Assisted Security (Secured Kernel)

| Security Measures | Features & Capabilities |
|:---|:---|
| **[Virtualization-based security (VBS)](/windows-hardware/design/device-experiences/oem-vbs)** | In addition to a modern hardware root-of-trust, there are numerous other capabilities in the latest chips that harden the operating system against threats, such as by protecting the boot process, safeguarding the integrity of memory, isolating security sensitive compute logic, and more. Two examples include Virtualization-based security (VBS) and Hypervisor-protected code integrity (HVCI). Virtualization-based security (VBS), also known as core isolation, is a critical building block in a secure system. VBS uses hardware virtualization features to host a secure kernel separated from the operating system. This means that even if the operating system is compromised, the secure kernel remains protected.<br><br>Starting with Windows 10, all new devices are required to ship with firmware support for VBS and HCVI enabled by default in the BIOS. Customers can then enable the OS support in Windows.<br>With new installs of Windows 11, OS support for VBS and HVCI is turned on by default for all devices that meet prerequisites. |
| **[Hypervisor-protected Code Integrity (HVCI)](/windows-hardware/design/device-experiences/oem-hvci-enablement)** | Hypervisor-protected code integrity (HVCI), also called memory integrity, uses VBS to run Kernel Mode Code Integrity (KMCI) inside the secure VBS environment instead of the main Windows kernel. This helps to prevent attacks that attempt to modify kernel mode code, such as drivers. The KMCI role is to check that all kernel code is properly signed and hasn't been tampered with before it is allowed to run. HVCI helps to ensure that only validated code can be executed in kernel-mode.<br><br>Starting with Windows 10, all new devices are required to ship with firmware support for VBS and HCVI enabled by default in the BIOS. Customers can then enable the OS support in Windows.<br>With new installs of Windows 11, OS support for VBS and HVCI is turned on by default for all devices that meet prerequisites. |
| **[Hardware-enforced stack protection](https://techcommunity.microsoft.com/t5/windows-os-platform-blog/understanding-hardware-enforced-stack-protection/ba-p/1247815)** | Hardware-enforced stack protection integrates software and hardware for a modern defense against cyberthreats such as memory corruption and zero-day exploits. Based on Control-flow Enforcement Technology (CET) from Intel and AMD Shadow Stacks, hardware-enforced stack protection is designed to protect against exploit techniques that try to hijack return addresses on the stack. |
| **[Secured-core PC](/windows-hardware/design/device-experiences/oem-highly-secure-11)** | Microsoft has worked with OEM partners to offer a special category of devices called Secured-core PCs. The devices ship with additional security measures enabled at the firmware layer, or device core, that underpins Windows. Secured-core PCs help prevent malware attacks and minimize firmware vulnerabilities by launching into a clean and trusted state at startup with a hardware-enforced root of trust. Virtualization-based security comes enabled by default. And with built-in hypervisor protected code integrity (HVCI) shielding system memory, Secured-core PCs ensure that all executables are signed by known and approved authorities only. Secured-core PCs also protect against physical threats such as drive-by Direct Memory Access (DMA) attacks. |
| **[Kernel Direct Memory Access (DMA) protection](../../hardware-security/kernel-dma-protection-for-thunderbolt.md)** | Kernel DMA Protection protects against external peripherals from gaining unauthorized access to memory. Physical threats such as drive-by Direct Memory Access (DMA) attacks typically happen quickly while the system owner isn't present. PCIe hot plug devices such as Thunderbolt, USB4, and CFexpress allow users to attach new classes of external peripherals, including graphics cards or other PCI devices, to their PCs with the plug-and-play ease of USB. Because PCI hot plug ports are external and easily accessible, devices are susceptible to drive-by DMA attacks. |