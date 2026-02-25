# 🧪 PicoCTF Digital Forensics – Writeups

## 📌 Context

These challenges were completed as part of structured digital forensics practice using picoCTF.  
The objective was to strengthen practical skills in metadata analysis, log investigation, file reconstruction, encoding detection, and forensic reasoning.

---

# 🔎 Challenge 1 – Hidden Data in PDF Metadata

## 🎯 Objective
Identify hidden information inside a redacted PDF document.

## 👀 Initial Observations
- The PDF contained redacted content.
- No visible flag inside the document.
- Suspicion that hidden information might exist in metadata.

## 🧠 Hypothesis
The flag may be stored inside document metadata fields such as Author, Creator, or Comments.

## 🛠 Tools Used
- exiftool (Linux)
- pdfinfo (Linux)
- CyberChef
- base64 (Linux CLI)

## 🔬 Investigation Steps

Check metadata using Linux:

```bash
exiftool file.pdf
```

OR

```bash
pdfinfo file.pdf
```

A suspicious Base64-encoded string was found in the Author field.

Decode Base64:

```bash
echo "encoded_string_here" | base64 -d
```

The decoded output revealed the flag.

## 🧾 Evidence
- Encoded string discovered in metadata.
- Decoded result matched picoCTF flag format.

## 🧩 Skills Practiced
- Metadata analysis
- Encoding identification
- Base64 decoding
- Linux CLI usage

## 🌍 Real-World Relevance
Metadata analysis is used in:
- Document attribution investigations
- Insider threat cases
- Tracking document leaks
- Digital evidence examination

---

# 🔎 Challenge 2 – Encoded Logs → PNG Reconstruction

## 🎯 Objective
Analyze encoded log data and reconstruct hidden file.

## 👀 Initial Observations
- Log file contained encoded text.
- Decoded output appeared to be binary data.
- Logs hinted that the content was a PNG file.

## 🧠 Hypothesis
The encoded data represents the binary content of an image file.

## 🛠 Tools Used
- dcode.fr (encoding identification)
- CyberChef (decoding)
- file (Linux)
- echo (Linux)
- Text editor

## 🔬 Investigation Steps

Identify encoding type using dcode.

Decode using CyberChef.

Save decoded output as image:

```bash
echo "decoded_binary_data" > output.png
```

Verify file type:

```bash
file output.png
```

Open image → Flag found.

## 🧾 Evidence
- Decoded content matched PNG file signature.
- Image opened successfully and revealed flag.

## 🧩 Skills Practiced
- Log file analysis
- Encoding detection
- File reconstruction
- Understanding file signatures

## 🌍 Real-World Relevance
Useful in:
- Malware payload extraction
- Log-based data exfiltration detection
- Incident response investigations
- Forensic artifact recovery

---

# 🔎 Challenge 3 – Corrupted JPG File Repair (Hex Analysis)

## 🎯 Objective
Repair a corrupted JPG file by correcting header bytes.

## 👀 Initial Observations
- The file would not open.
- Challenge hint indicated broken bytes.
- Suspicion of incorrect file signature (magic bytes).

## 🧠 Hypothesis
The file header does not match the standard JPG magic bytes.

## 🛠 Tools Used
- Hex editor
- xxd (Linux)
- file (Linux)

## 🔬 Investigation Steps

Check file type:

```bash
file image.jpg
```

Inspect header in hex:

```bash
xxd image.jpg | head
```

Standard JPG header:

```
FF D8 FF E0
```

Incorrect bytes were identified and corrected in the hex editor.

After saving changes, the image opened successfully and revealed the flag.

## 🧾 Evidence
- Magic bytes did not match standard JPG signature.
- Correcting header restored file functionality.

## 🧩 Skills Practiced
- File signature verification
- Hex-level file inspection
- Manual file repair
- Understanding file structure

## 🌍 Real-World Relevance
Used in:
- File carving during forensic analysis
- Recovering corrupted evidence
- Validating file integrity
- Detecting file spoofing

---

# 🔎 Challenge 4 – Log File Flag Reconstruction

## 🎯 Objective
Extract scattered flag fragments from server logs.

## 👀 Initial Observations
- Logs contained multiple repeated entries.
- Keyword identified: FLAGPART.
- Fragments appeared scattered throughout logs.

## 🧠 Hypothesis
The full flag is split across multiple log entries and must be reconstructed.

## 🛠 Tools Used
- PowerShell (Select-String)
- grep (Linux alternative)

## 🔬 Investigation Steps

PowerShell:

```powershell
Select-String -Path log.txt -Pattern "FLAGPART"
```

Linux equivalent:

```bash
grep "FLAGPART" log.txt
```

Extracted fragments were collected and combined in chronological order to reconstruct the full flag.

## 🧾 Evidence
- Multiple FLAGPART entries found.
- Reassembled fragments formed valid picoCTF flag.

## 🧩 Skills Practiced
- Log filtering
- Pattern searching
- Data reconstruction
- CLI-based investigation

## 🌍 Real-World Relevance
Relevant in:
- Incident response investigations
- SIEM event correlation
- Log-based data leakage detection
- Security monitoring operations

---

# 📈 Weekly Reflection

## What I Learned
- Metadata often contains hidden investigative clues.
- Encoded log data can represent binary artifacts.
- Magic bytes define file identity.
- Log filtering is powerful for reconstructing secrets.

## What I Will Improve
- Faster encoding identification without external tools.
- Stronger familiarity with file signatures.
- More structured hypothesis formation before testing.

---

# 🚀 Skill Areas Strengthened This Week
- Digital Forensics Fundamentals
- Log Analysis
- Encoding & Decoding Techniques
- File Signature Verification
- Linux & PowerShell Command Usage
