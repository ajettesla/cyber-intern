🔍 How VirusTotal Scans Files
1️⃣ File Upload & Hash Check

When you upload a file (like eicar.txt), VirusTotal first checks its hash (SHA-256, MD5, etc.).

If the file has been scanned before, VirusTotal retrieves the previous results instead of rescanning.

2️⃣ Multi-Engine Analysis

VirusTotal runs the file through 97+ antivirus engines (such as Microsoft Defender, Kaspersky, McAfee, etc.).

Each engine applies its own signature-based detection, heuristic analysis, and behavioral analysis.

3️⃣ Behavioral & Static Analysis

Static Analysis: Examines the file’s structure, metadata, and embedded code.

Behavioral Analysis: Runs the file in a sandbox environment to observe its actions (e.g., modifying registry keys, network activity).

4️⃣ Threat Intelligence & Community Feedback

VirusTotal integrates threat intelligence from cybersecurity researchers.

Users can comment on scan results, providing additional insights.

🔎 Understanding Your Score (8/97)
8/97 means 8 antivirus engines flagged the file as malicious, while 89 engines did not.

Since eicar.txt is a test file, some engines detect it as a false positive.

You can check which engines flagged it and their reasoning.


![Screenshot (10)](https://github.com/user-attachments/assets/38918705-741d-44b9-bf6f-4c6ff549348e)


🔍 Registry-Related Event Codes in Windows
1️⃣ Event ID 4656 – A Handle to an Object Was Requested
This logs when a process requests access to a registry key.

It records who (user), what process, and which registry key was accessed.

Commonly used for tracking unauthorized registry access.

2️⃣ Event ID 4657 – A Registry Value Was Modified
This occurs when a registry value is changed.

It records before-and-after values, showing exactly what changed.

Useful for detecting malicious persistence mechanisms (e.g., malware adding itself to startup).

3️⃣ Event ID 4663 – An Attempt Was Made to Access an Object
This logs actual registry accesses (read, write, delete).

It confirms whether access was granted or denied.

Often useful for monitoring registry permissions.

4️⃣ Event ID 4660 – An Object Was Deleted
Triggers when a registry key or value is deleted.

Critical for detecting unwanted configuration removals.

![image](https://github.com/user-attachments/assets/f882805e-174d-4d01-ad54-03e34336b1cc)

