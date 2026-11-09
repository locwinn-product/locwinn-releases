# Locwinn for Windows

This is where the Locwinn installer is published. Locwinn blocks adult sites on Windows 10 and 11,
and is deliberately hard to switch off in a weak moment.

Buy it, manage your PCs and get help at **[locwinn.com](https://locwinn.com)**.

## Download

Get `locwinn-installer.exe` from the
**[latest release](https://github.com/locwinn-product/locwinn-releases/releases/latest)**.

- To finish installing you need the license key from your purchase email. It is also on your
  dashboard at [locwinn.com/account](https://locwinn.com/account).
- Every click, with pictures: the [install guide](https://locwinn.com/install-guide.html).
- Before you install, read [how uninstalling works](https://locwinn.com/uninstall.html). The choice
  you make at install (Lite or Nuclear) decides how slow removal is.

## Check that the file is ours

### The signature

The installer is signed by **Bamahut LLC**, the company that makes Locwinn.

- Right-click `locwinn-installer.exe` > **Properties** > **Digital Signatures**. The signer is
  **Bamahut LLC** and there is a timestamp. Select it > **Details**: it says "This digital
  signature is OK."
- Or in PowerShell, in the folder you saved it to:

  ```powershell
  $sig = Get-AuthenticodeSignature .\locwinn-installer.exe
  $sig.Status                     # must be: Valid
  $sig.SignerCertificate.Subject  # must start with: CN=Bamahut LLC
  ```

When you run it, Windows asks "Do you want to allow this app to make changes to your device?" It
should say **Verified publisher: Bamahut LLC**. If it says **Unknown publisher**, click **No** and
download the installer again from [locwinn.com](https://locwinn.com/download.html).

### The checksum

Each release lists the SHA-256 checksum of its files, in its notes and in `SHA256SUMS.txt`.

```powershell
(Get-FileHash .\locwinn-installer.exe -Algorithm SHA256).Hash.ToLower()
```

The result must match the `locwinn-installer.exe` line. If it does not, do not run the file:
download it again, and if it still does not match, write to support@locwinn.com.

## If Windows warns you

A new release has few downloads yet, so Edge may say the file "isn't commonly downloaded", or
Windows may show "Windows protected your PC". Check that the publisher is Bamahut LLC, then choose
**Keep** (Edge) or **More info** > **Run anyway** (Windows). The
[install guide](https://locwinn.com/install-guide.html) shows each of these screens.

## What you need

- Windows 10 or 11, 64-bit
- An administrator account (the installer asks for permission)
- An internet connection while installing, to check your license key
- Microsoft Edge WebView2 Runtime. Almost every up-to-date PC already has it; if yours does not,
  the installer offers Microsoft's download link.

## Help

Write to **support@locwinn.com**, or see [locwinn.com/support](https://locwinn.com/support.html).

This repository holds release files only. There is no source code here.

© 2026 Bamahut LLC
