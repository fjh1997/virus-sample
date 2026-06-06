# Tencent Cloud JDWP JNI Sample - 2026-06-06

## Safety

This directory contains a live malicious Linux ELF shared object sample. Do not execute or load it on a host system. Analyze only in an isolated malware lab or sandbox.

## Summary

- Alert source: Tencent Cloud Host Security
- Alert time: 2026-06-06 10:36:29 GMT+8
- Affected host: `150.158.101.65` / `10.0.0.6`
- Original alert path: `/tmp/3676292`
- Local archive path: `3676292.elf.sample`
- Threat level: severe
- Assessed infection path: exposed Tomcat JDWP debug port `0.0.0.0:5005`

The sample was mapped into the Tomcat JVM process (`java`, PID `35661`) as a native library. The file exports `JNI_OnLoad`, which is consistent with a malicious JNI shared object loaded through `System.load(...)` or an equivalent JVM native-loading path.

## Timeline

| Time (GMT+8) | Event |
|---|---|
| 2026-06-05 21:27:14 | Same hash written as `/tmp/2637334` |
| 2026-06-06 01:28:18 | Same hash written as `/tmp/7991403` |
| 2026-06-06 06:35:37 | Same hash written as `/tmp/2930230` |
| 2026-06-06 10:36:28 | Same hash written as `/tmp/3676292` |
| 2026-06-06 10:36:29 | Tencent Cloud Host Security reported `/tmp/3676292` |

## Indicators

| Type | Value |
|---|---|
| MD5 | `3003c0187f2e69d269c39d189663381b` |
| SHA256 | `326e698a2084a4a6ff9b90a4f88d0e7b6178102605c3c146b000f892537dd865` |
| File type | ELF 64-bit LSB shared object, x86-64, dynamically linked, stripped |
| Export | `JNI_OnLoad` |
| Original path | `/tmp/3676292` |
| Duplicate paths | `/tmp/2637334`, `/tmp/7991403`, `/tmp/2930230`, `/tmp/3676292` |
| Tencent Cloud trace ID | `2d30e561401a4ecea20aad5176086ce2` |

## Notes

The host did not have `auditd` or process accounting enabled at the time of collection, so the exact JDWP method calls and payload code were not available from local logs. Local evidence supports that the attacker used the exposed JDWP debug listener to write and load the JNI library in the Tomcat JVM.
