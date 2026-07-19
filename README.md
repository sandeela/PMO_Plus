# PMO+ Light Edition

**Talk to your project. Review evidence. Generate decision-ready reports.**

PMO+ is a lightweight Windows project companion that reviews supported project documents, answers natural-language questions, connects with approved project sources, and generates structured status reports.

> **Version:** 1.0.0 Light  
> **Platform:** Windows 10/11, 64-bit

## Download

[**Download PMO+ v1.0.0 for Windows**](https://github.com/sandeela/PMO_Plus/releases/download/v1.0.0/pmo_app.dist.zip)

The download is approximately 169 MB and includes the PMO+ application and its required runtime files.

## What you need before starting

### Required

#### 1. A project-artifacts folder

Create a separate local folder containing the project evidence that PMO+ may review, for example:

```text
C:\Users\YourName\Documents\My Project Artifacts
```

Add only documents that you are authorised to process. PMO+ needs at least one supported file in this folder.

#### 2. OpenAI API access for PMO+ v1.0 Light

The current public desktop build requires:

- Your own OpenAI API key
- An API account with available billing or credits
- Internet connectivity

A ChatGPT subscription and OpenAI API billing are separate. A ChatGPT Plus subscription by itself does not automatically provide API credits.

PMO+ stores the entered OpenAI key through the Windows credential store. Never place your key inside the project-artifacts folder or share it with another user.

### Optional: Azure DevOps connection

To synchronise Azure DevOps work items, prepare:

- Azure DevOps organisation name or URL, for example `https://dev.azure.com/your-organisation`
- Exact Azure DevOps project name
- Your own Personal Access Token (PAT)
- Permission to read the project and its work items

Use the minimum read-only permissions required. Do not create a full-access PAT for PMO+.

### Optional: SharePoint connection

To synchronise authorised SharePoint documents, prepare:

- Microsoft Entra tenant ID
- Entra application/client ID
- Complete SharePoint site URL
- Document-library name, or leave it blank to use the default Documents library
- Optional folder path inside the library

The Entra application must be configured as a public client with delegated Microsoft Graph `Sites.Read.All` permission and administrator consent. Most corporate users will need their Microsoft 365 or Entra administrator to provide or approve this configuration.

### About Microsoft Copilot connectivity

The PMO+ architecture can support different approved AI platforms, including Microsoft Copilot. However, Copilot connectivity is **not a plug-and-play public connection in PMO+ v1.0 Light**. It requires appropriate organisational licensing, Copilot or Work IQ API access, Microsoft Entra configuration and administrator approval.

For the current public release, use the OpenAI API unless you have a separately configured organisational PMO+ build.

## Installation

PMO+ does not require a conventional installer.

### 1. Download PMO+

Open the [PMO+ v1.0.0 release](https://github.com/sandeela/PMO_Plus/releases/tag/v1.0.0) and download:

```text
pmo_app.dist.zip
```

Do not download GitHub's automatically generated **Source code** files. They do not contain the runnable Windows application.

### 2. Unblock the downloaded ZIP

PMO+ is currently an unsigned Light Edition, so Windows may mark the downloaded ZIP as originating from the internet.

Before extracting it:

1. Open your **Downloads** folder.
2. Right-click `pmo_app.dist.zip`.
3. Select **Properties**.
4. On the **General** tab, select **Unblock** if that option is displayed.
5. Select **Apply**, then **OK**.

Unblocking the ZIP before extraction helps prevent Windows from separately blocking the application's supporting files.

### 3. Extract the complete application

1. Right-click `pmo_app.dist.zip`.
2. Select **Extract All**.
3. Choose a permanent location, for example:

```text
C:\Users\YourName\Documents\PMOPlus
```

4. Keep the complete extracted folder together.

**Do not move or copy only the EXE.** PMO+ requires the DLLs and supporting files included in the extracted folder.

## Create your project-artifacts folder

Create a separate folder for the project information you want PMO+ to review, for example:

```text
C:\Users\YourName\Documents\My Project Artifacts
```

Copy your approved project documents into this folder. Supported formats may include:

- PDF
- Word
- Excel
- PowerPoint
- Text, Markdown and CSV
- Microsoft Project MPP or XML plans

Microsoft Project may need to be installed locally for native `.mpp` extraction.

Do not place your project documents inside the PMO+ application folder.

## Start PMO+

1. Open the extracted `pmo_app.dist` folder.
2. Double-click `PMO-Plus.exe`.
3. If the executable is named `pmo_app.exe` in your download, run that file instead.
4. Select the floating PMO+ companion to open the project discussion.

On first use, PMO+ will ask you to:

1. Select your project-artifacts folder.
2. Choose whether to configure Azure DevOps.
3. Enter your own OpenAI API key.
4. Optionally configure or synchronise Azure DevOps and SharePoint through Settings.

Connection availability depends on your credentials, licensing, permissions and organisational configuration.

## Ask your project

Example questions:

- Which critical risks remain open?
- Which actions are overdue, and who owns them?
- What is the documented project budget?
- What could affect the next milestone?
- Which decisions remain outstanding?
- What information is missing from the reviewed evidence?
- Generate a current project status report.

PMO+ can generate lightweight text reports and formatted Word reports.

## Voice commands

Begin commands with **“PMO plus”**. Speak clearly and allow a brief pause after the wake phrase.

### Open and control PMO+

```text
PMO plus open
PMO plus start
PMO plus minimize
PMO plus maximise
PMO plus restore
PMO plus settings
PMO plus close settings
```

Both `minimize`/`minimise` and `maximize`/`maximise` are supported.

### Project connections

```text
PMO plus connect to ADO
PMO plus connect to Azure DevOps
PMO plus sync ADO
PMO plus sync Azure DevOps
PMO plus connect to SharePoint
PMO plus sync SharePoint
```

### Knowledge and reporting

```text
PMO plus generate report
PMO plus refresh knowledge
```

### Audio controls

```text
PMO plus mute microphone
PMO plus mute voice
PMO plus mute speaker
```

`Mute voice` or `mute speaker` stops audible PMO+ responses while voice-command listening remains active. `Mute microphone` disables listening completely; use the microphone button in the interface to enable it again.

### Close PMO+

```text
PMO plus exit
PMO plus quit
PMO plus close
PMO plus close everything
```

These commands close the application rather than merely minimising it.

### Dictate a project question

The continuous listener recognises the configured PMO+ commands above. To speak a free-form project question, select the microphone button beside the question field, wait for the listening indicator, then dictate the question. PMO+ places the recognised text into the project discussion for processing.

Voice functionality requires Windows microphone permission and Windows speech components. If voice commands do not start, open **Windows Settings → Privacy & security → Microphone**, allow desktop applications to access the microphone, and restart PMO+.

## If Windows still blocks the application

First confirm that the ZIP was unblocked **before** extraction.

If it was already extracted, open PowerShell inside the extracted PMO+ folder and run:

```powershell
Get-ChildItem -Recurse -File | Unblock-File
```

Then try launching PMO+ again.

Some managed corporate computers block unsigned applications through organisational security policies. In that situation, contact your IT administrator. Do not disable company security controls.

## Security and privacy

- PMO+ does not include an AI key for public use. Use your own authorised credentials.
- Never share your API key, Azure DevOps PAT, tenant secret or access token.
- Use read-only and minimum-required permissions wherever possible.
- Project content may be sent to the AI platform you select for processing.
- Do not use confidential, personal or client information unless your organisation permits that platform and processing method.
- Review AI-generated answers and reports before using or distributing them.

## Light Edition limitations

- The Windows application is currently unsigned and may trigger a Windows warning.
- The current public v1.0 Light desktop build uses the OpenAI API for its AI responses.
- Copilot connectivity requires a separately approved and configured organisational environment.
- Azure DevOps and SharePoint availability depends on credentials and organisational access.
- Native MPP extraction may require Microsoft Project.
- AI output can contain errors and must be professionally reviewed.
- PMO+ supports project analysis and reporting; it does not replace accountable project leadership.

## Important disclaimer

PMO+ is an independent Light Edition project and is not endorsed by Microsoft, OpenAI, Azure DevOps or SharePoint. It is provided for evaluation and demonstration without warranty. Users remain responsible for data protection, security approval, source validation and decisions made using its output.

---

**Designed and developed by Sandeela Waseem**  
Transformation Delivery · AI-Enabled Project Management
