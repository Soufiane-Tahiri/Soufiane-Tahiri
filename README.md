# Soufiane Tahiri

**M1 ISOC** — IoT Security & Embedded Systems  
Université Moulay Ismail, Faculté des Sciences, Meknès

---

I work at the hardware-software boundary — firmware security, bare-metal ML inference, and low-level exploitation on ARM. The problems I find interesting are the ones where the security model breaks down at the register level.

---

## Active Projects

**[tinyinfer](https://github.com/Soufiane-Tahiri/tinyinfer)** — C99 neural network inference engine for ESP32 and resource-constrained MCUs. No heap allocation, no external dependencies. Forward pass, tensor ops, and weight loading within fixed SRAM budgets. Targets PyTorch-exported models.

**embsecfirm** *(private)* — Security-hardened firmware stack for ESP32. Full threat model, verified secure boot chain, encrypted OTA pipeline, MPU isolation regions, hardware-backed key management. Complete architecture documented before a line of application code is written.

**IoT IDS** *(private)* — ML-based intrusion detection for MQTT-connected IoT devices. Building the dataset by running 8+ attack scripts (spoofing, flooding, injection) against a real ESP32 target over HiveMQ. Custom dataset generation before model training.

---

## Completed Work

**[Audio Spoofing Detection](https://soufianetahiri.me/projects/voice-detection.html)** — Voice manipulation detection trained on ASVspoof2019 LA (71,237-sample eval set). Three architectures compared — BiLSTM (~656K params), CNN (~360K), Transformer (~282K) — using LFCC feature extraction (60 coeff, 512-pt FFT). Transformer selected based on generalization gap analysis (val EER 0.0466 vs test 0.3496, 7.5× gap vs CNN's 54×), then retrained on full dataset. Final: 87.11% accuracy, EER 26.76%, F1 0.926. Desktop inference app with mic input, ~200ms CPU latency. *(Academic — team)*

**[Mbed OS 5 HAL + Modbus RTU on ESP32](https://soufianetahiri.me/projects/mbed-modbus.html)** — Partial Mbed OS 5 API compatibility layer on top of ESP-IDF/FreeRTOS. Mbed threading primitives mapped to FreeRTOS tasks and semaphores; Ticker via `esp_timer` in task mode (not ISR); DHT11 1-wire driver using timer-based pulse measurement with `portENTER_CRITICAL` for 40-bit decode (2.8ms critical section). 7-task concurrent system: producer/consumer with semaphore sync, Modbus RTU FC03 frames with CRC-16 (0xA001), relay hysteresis, real-time FreeRTOS metrics. Validated: 100% CRC integrity over 180 frames, 19.3% heap usage stable throughout run.

**[ARMv7 Low-Level Security](https://soufianetahiri.me/projects/shellcode.html)** — Position-independent shellcode in Thumb mode. ARM→Thumb state switch via BX to odd address; stack-based `//bin/sh` construction via MOV+LSL+ADD sequences (no data section, no literal pool); null-byte avoidance through encoding constraints; direct `execve` syscall via SVC #0 with R7=11. Phase 1 complete and validated under QEMU + GDB.

**[SmartTrackerAI](https://github.com/si-labs-org/Expenses_Management)** — Android expense tracker with ML Kit OCR pipeline, LLaMA 3.3 70B (Groq API) for structured receipt parsing, and offline Trie + Levenshtein distance ≤2 fallback classifier. MVVM, Room ORM, WorkManager. *(Academic — team)*

---

## Stack

```
Languages     C (systems/embedded), Python (ML/automation), Java (Android), ARMv7 ASM
Embedded      ESP32 / ESP-IDF, FreeRTOS, Mbed OS 5, Zephyr RTOS, Modbus RTU
ML            PyTorch, BiLSTM / CNN / Transformer, LFCC feature engineering
Security      ARMv7 exploitation, firmware security, IoT protocol analysis, IDS development
Tools         GDB, QEMU, Wireshark, PlatformIO, Ghidra, x32dbg
```

---

[soufianetahiri.me](https://soufianetahiri.me) · [linkedin](https://www.linkedin.com/in/soufiane-tahiri23/) · tahirisoufiane.406@gmail.com
