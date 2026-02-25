# 🛡 Digital Forensics Core Concepts – Theory + Tools + Application

This document consolidates foundational DFIR concepts along with practical command-line usage and real investigative scenarios.

The goal is to bridge:
Theory → Tools → Investigation → Evidence

---

# 1️⃣ Metadata Analysis

## 📖 Concept Overview

Metadata is structured information embedded within files that describes properties such as:

- Author
- Creation timestamp
- Modification timestamp
- Software used
- Embedded comments
- Device or system information

Metadata often persists even when visible content is redacted or modified.

In forensic investigations, metadata can reveal:
- Origin of a document
- Timeline inconsistencies
- Evidence of tampering
- Hidden encoded artifacts

---

## 🔎 Investigative Importance

Metadata is critical in:

- Insider threat cases
- Document forgery investigations
- Intellectual property theft
- Leak attribution
- Timeline reconstruction

Attackers may overlook metadata, making it a valuable artifact source.

---

## 🛠 Tools & Commands

### View Metadata (Linux)

```bash
exiftool file.pdf
```

OR

```bash
pdfinfo file.pdf
```

### Extract and Decode Base64 (Linux)

```bash
echo "encoded_string_here" | base64 -d
```

---

## 🧪 Practical Application

In a forensic challenge:

- A PDF contained redacted visible content.
- Metadata inspection revealed a Base64 string in the Author field.
- Decoding the string exposed the hidden flag.

This demonstrated that hidden artifacts may exist outside visible file content.

---

# 2️⃣ Encoding & Binary Reconstruction

## 📖 Concept Overview

Encoding transforms data into another representation format for:

- Safe transmission
- Obfuscation
- Storage compatibility

Common encodings:
- Base64
- Hexadecimal
- URL encoding

Encoded log artifacts may represent:
- Embedded payloads
- Extracted binary files
- Hidden exfiltrated data

---

## 🔎 Investigative Importance

In DFIR, decoding is used for:

- Malware payload extraction
- Suspicious log artifact recovery
- Reconstructing transmitted files
- Identifying obfuscation techniques

Recognizing encoding patterns is a core analyst skill.

---

## 🛠 Tools & Commands

### Decode Base64

```bash
echo "encoded_string" | base64 -d
```

### Save Decoded Output

```bash
echo "decoded_binary_data" > output.png
```

### Identify File Type

```bash
file output.png
```

---

## 🧪 Practical Application

- Log file contained encoded content.
- After decoding, output resembled binary data.
- File signature matched PNG format.
- Saving as `.png` restored the image.
- Flag was recovered from reconstructed file.

This reinforced artifact reconstruction from encoded logs.

---

# 3️⃣ File Signatures (Magic Bytes)

## 📖 Concept Overview

Magic bytes are unique hexadecimal sequences at the beginning of files that identify file type.

They serve as a validation mechanism independent of file extension.

Common signatures:

- JPG → FF D8 FF E0
- PNG → 89 50 4E 47
- PDF → 25 50 44 46
- ZIP → 50 4B 03 04

Operating systems rely on these signatures to interpret file structure.

---

## 🔎 Investigative Importance

Magic byte analysis helps detect:

- File spoofing (e.g., .jpg renamed to .exe)
- Corrupted files
- Malicious payload masking
- Evidence tampering
- File carving from raw disk images

---

## 🛠 Tools & Commands

### Identify File Type

```bash
file image.jpg
```

### Inspect Header Bytes

```bash
xxd image.jpg | head
```

---

## 🧪 Practical Application

- A JPG file failed to open.
- Hex inspection showed incorrect header bytes.
- Replacing header with correct JPG magic bytes restored functionality.
- Repaired image contained the flag.

This demonstrated how file integrity validation can restore corrupted evidence.

---

# 4️⃣ Log Analysis & Pattern Searching

## 📖 Concept Overview

Logs record structured system events such as:

- Authentication attempts
- Service restarts
- Errors and warnings
- Debug information
- Application activity

Logs are primary evidence sources in incident response.

They are often noisy and require filtering.

---

## 🔎 Investigative Importance

Log analysis is used for:

- Detecting suspicious activity
- Reconstructing attack timelines
- Identifying data leakage
- Correlating multi-event patterns
- SIEM alert investigation

Pattern recognition is critical in filtering relevant evidence.

---

## 🛠 Tools & Commands

### PowerShell Pattern Search

```powershell
Select-String -Path log.txt -Pattern "FLAGPART"
```

### Linux Equivalent

```bash
grep "FLAGPART" log.txt
```

---

## 🧪 Practical Application

- Server logs contained repeated entries.
- Relevant entries labeled with "FLAGPART".
- Pattern filtering extracted fragments.
- Combining fragments reconstructed the complete flag.

This simulated real-world log correlation and data reconstruction.

---

# 5️⃣ Structured Investigation Methodology

Across all exercises, the following forensic workflow was applied:

1. Identify anomaly or clue
2. Form hypothesis
3. Select appropriate tool
4. Validate output
5. Confirm evidence integrity
6. Document findings

This structured methodology is foundational in professional DFIR operations.

---

# 🔐 Tools Utilized So Far

Linux:
- exiftool
- pdfinfo
- base64
- file
- xxd
- grep

Windows:
- PowerShell (Select-String)

Online:
- CyberChef
- Encoding detection platforms

---

# 📈 Core Competencies Strengthened

- Metadata artifact analysis
- Encoding detection and decoding
- Binary file reconstruction
- File signature validation
- Log filtering & event correlation
- Command-line forensic investigation
- Hypothesis-driven analytical thinking
