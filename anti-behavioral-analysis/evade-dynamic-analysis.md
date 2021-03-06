|||
|---|---|
|**ID**|**B0003**|
|**Objective(s)**|[Anti-Behavioral Analysis](../anti-behavioral-analysis)|
|**Related ATT&CK Technique**|[Virtualization/Sandbox Evasion](https://attack.mitre.org/techniques/T1497/)|


Dynamic Analysis Evasion
========================
Malware may obstruct dynamic analysis in a sandbox, emulator, or virtual machine. 

See [Emulator Evasion](../anti-behavioral-analysis/evade-emulator.md) for an  emulator-specific evasion behavior, and see [Execution Guardrails](../anti-behavioral-analysis/execution-guardrails.md) for a behavior that constrains dynamic execution based on environmental conditions. 

Methods
-------
|Name|ID|Description|
|---|---|---|
|**Alternative ntdll.dll**|B0003.001|A copy of ntdll.dll is dropped to the filesystem and then loaded. This alternative DLL is used to execute function calls to evade sandboxes which use hooking in the operating system's ntdll.dll.|
|**Data Flood**|B0003.002|Overloads a sandbox by generating a flood of meaningless behavioral data. [[1]](#1)|
|**Delayed Execution**|B0003.003|Stalling code is typically executed before any malicious behavior. The malware's aim is to delay the execution of the malicious activity long enough so that an automated dynamic analysis system fails to extract the interesting malicious behavior. This method is very similar to ATT&CK's [Virtualization/Sandbox Evasion: Time Based Evasion](https://attack.mitre.org/techniques/T1497/003/) sub-technique.|
|**Demo Mode**|B0003.004|Inclusion of a demo binary/mode that is executed when token is absent or not privileged enough.|
|**Drop Code**|B0003.005|Original file is written to disk then executed. May confuse some sandboxes, especially if the dropped executable must be provided specific arguments and the original dropper is not associated with the drop file(s).|
|**Encode File**|B0003.006|Encode a file on disk, such as an implant's config file.|
|**Hook File System**|B0003.007|Execution happens when a particular file or directory is accessed, often through hooking certain API calls such as CreateFileA and CreateFileW.|
|**Hook Interrupt**|B0003.008|Modification of interrupt vector or descriptor tables.|
|**Illusion**|B0003.009|Creates an illusion; makes the analyst think something happened when it didn't.|
|**Restart**|B0003.010|Restarts or shuts down system to bypass sandboxing.|


Malware Examples
----------------
|Name|Date|Description|
|---|---|---|
|[**Ursnif**](../xample-malware/ursnif.md)|May 2016|Ursnif uses malware macros to evade sandbox detection. [[2]](#2)|
|[**Terminator**](../xample-malware/terminator.md)|October 2013|The Terminator rat evades a sandbox by not executing until after a reboot. Most sandboxes don't reboot during an analysis. [[3]](#3)|
|**Nap**|2013|Trojan Nap (tied to the Kelihos Botnet) uses extended sleep calls to evade sandbox analysis. [[3]](#3)|
|**Smokeloader**|2019|Smokeloader drops a copy of ntdll.dll to %APPDATA%\Local\Temp\ [[4]](#4)|
|[**WebCobra**](../xample-malware/webcobra.md)|2018|Evades dynamic analysis.)|

References
----------
<a name="1">[1]</a> http://joe4security.blogspot.com/2013/06/overloading-sandboxes-new-generic.html

<a name="2">[2]</a> https://www.cyber.nj.gov/threat-profiles/trojan-variants/ursnif

<a name="3">[3]</a> https://www.fireeye.com/content/dam/fireeye-www/current-threats/pdfs/pf/file/fireeye-hot-knives-through-butter.pdf

<a name="4">[4]</a> https://research.checkpoint.com/2019-resurgence-of-smokeloader/
