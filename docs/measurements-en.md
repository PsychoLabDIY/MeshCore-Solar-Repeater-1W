# Test log — MeshCore Solar Repeater 1W

Times are local to Poland (CET), 16 November 2026.

| Time | Battery voltage | App charge estimate | 0-hop ping | SNR outbound / return | Notes |
|---|---:|---:|---:|---|---|
| 22:19 | 4.17 V | 97% | 125 ms | 12.5 / 12.0 dB | First runtime test after Balanced flash, app admin access OK; RX 10, TX 9, RX errors 3 |
| **22:58** | **3.85 V** | **70%** | **1044 ms** | **11.75 / 12.0 dB** | Battery-powered reference snapshot; uptime 2m09s; RX 15, TX 7, RX errors 1, queue 0 |

The 22:58 reading is the **overnight discharge baseline**. The earlier 4.17 V was obtained under different supply conditions and should not be interpreted as a 0.32 V discharge in 39 minutes. App battery percentage is an estimate, not a cell-capacity test. Reboot resets all uptime and packet counters; radio receive errors are not necessarily lost valid messages. The repeater RTC was showing 1 March 2026, so the table uses the observer's phone time.

Next check: 17 November 2026 morning, log voltage, uptime, RX/TX, errors and ping. No remote battery telemetry is available while disconnected from MSI unless a separate gateway is configured.
