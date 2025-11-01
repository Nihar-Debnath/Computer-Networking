# Physical Layer — full detailed explainer (beginner → advanced)

The **Physical Layer** is **Layer 1** of the OSI model. It’s the most “concrete” layer: it defines how **raw bits (0s and 1s)** are physically transmitted over a medium (copper, fiber, air). Everything below the higher-level protocols starts here — electrical/optical/radio signals, connectors, cables, and hardware.

I’ll walk you through **what it is, what it does, how it works, real examples, devices & media, problems that occur at this layer, and practical tips**.

---

## 1) Purpose & core responsibilities *

* **Bit transmission:** Transmit and receive raw bit streams between physically connected devices.
* **Signalling:** Convert digital bits to physical signals (electrical voltages, light pulses, radio waves) and back.
* **Media and connectors:** Specify physical media (cable/fiber/air) and connectors (RJ45, LC, etc.).
* **Bit rate & timing:** Define data rate (bits per second), bit timing, synchronization (when each bit starts/ends).
* **Physical topology:** Support for wiring topologies (bus, star, ring).
* **Line configuration:** Simplex, half-duplex, full-duplex modes.
* **Physical network devices:** Repeaters, hubs, transceivers, network interface cards (NICs), modems.

---

## 2) Basic concepts and terminology *

* **Bit vs Baud**

  * **Bit rate (bps):** Number of bits transmitted per second.
  * **Baud:** Number of signal changes (symbols) per second. One symbol may represent multiple bits (e.g., using QAM).
* **Channel bandwidth:** Frequency range that the medium supports (Hz). Larger bandwidth → potential for higher data rates.
* **Throughput vs Bandwidth:** Bandwidth is maximum possible; throughput is what you actually get (affected by errors, overhead).
* **Attenuation:** Reduction in signal strength with distance.
* **Noise:** Unwanted electrical/optical/radio interference that corrupts signals.
* **SNR (Signal-to-Noise Ratio):** Higher SNR → cleaner signal, higher possible rates.
* **BER (Bit Error Rate):** Fraction of bits received incorrectly.

---

## 3) Signal types: analog vs digital

* **Digital signals:** Discrete levels (e.g., 0 V = 0, +5 V = 1). Used on short copper links, TTL logic, etc.
* **Analog signals:** Continuous waveforms. Used where modulation is applied (e.g., radio, modem tones).
* **Often:** Digital data is **modulated** onto an analog carrier for long-distance or wireless transmission.

---

## 4) Encoding (line coding) — representing bits on the medium *

How to map bits → signals on wire:

* **NRZ (Non-Return to Zero):** Level = 1 or 0. Simple but DC bias and clock recovery problems.
* **NRZI (NRZ Inverted):** Transition = 1, no transition = 0 (or vice-versa).
* **Manchester encoding:** Bit value encoded by mid-bit transition (good for clock recovery). Used in older Ethernet (10BASE-T).
* **Bipolar-AMI:** 0 = zero-level, 1 = alternate positive/negative pulses. Helps detect DC bias.
* **4B/5B, 8B/10B:** Map groups of bits to balanced symbols for clocking and DC balance (used in Gigabit Ethernet, Fibre Channel).

**Why encoding matters:** it affects error detection, required bandwidth, ability to recover clock, DC balance, and spectral content.

---

## 5) Modulation — putting digital data on analog carriers

Used for long-distance and wireless. Common schemes:

* **ASK (Amplitude Shift Keying)** — change amplitude.
* **FSK (Frequency Shift Keying)** — change frequency (used in low-speed modems and some radio).
* **PSK (Phase Shift Keying)** — change phase (BPSK, QPSK).
* **QAM (Quadrature Amplitude Modulation)** — changes amplitude and phase (used in cable modems, Wi-Fi, LTE).
* **OFDM (Orthogonal Frequency Division Multiplexing)** — many subcarriers (used in Wi-Fi, LTE, DSL).

Modulation decisions trade off spectral efficiency vs robustness to noise.

---

## 6) Multiplexing — sharing a physical medium *

Ways to carry multiple signals over same channel:

* **FDM (Frequency Division Multiplexing):** Different frequency bands (radio, cable TV).
* **TDM (Time Division Multiplexing):** Time slots for multiple data streams (T1 lines).
* **WDM (Wavelength Division Multiplexing):** Multiple light wavelengths in one fiber (DWDM for long-haul fiber).

---

## 7) Transmission modes *

* **Simplex:** One-way only (e.g., keyboard → PC).
* **Half-duplex:** Both directions but not simultaneously (walkie-talkie).
* **Full-duplex:** Both directions simultaneously (phone call, modern Ethernet with switches).

Full-duplex often requires separate channels or echo cancellation techniques.

---

## 8) Physical media (guided vs unguided) *

### Guided media (wired)

* **Twisted Pair (TP)**

  * **Unshielded Twisted Pair (UTP)**: Cat5e, Cat6, Cat6a — common for Ethernet.
  * **Shielded Twisted Pair (STP)**: adds shielding for less EMI.
  * **Use:** 10/100/1000/10G Ethernet (depending on category & distance).
  * **Connector:** RJ-45.
* **Coaxial Cable**

  * Older LANs and cable TV networks (eg 10BASE2, DOCSIS for cable internet).
  * Connector types: BNC, F-type.
* **Optical Fiber**

  * **Single-mode (SMF):** long distance, high bandwidth (lasers).
  * **Multi-mode (MMF):** shorter distance (LED or VCSEL).
  * **Connectors:** LC, SC, ST.
  * **Used for:** Long-haul backbones, data center interconnects, gigabit+ links.

### Unguided media (wireless)

* **Radio waves, Microwaves, Infrared**

  * **Wi-Fi (2.4 GHz, 5 GHz, 6 GHz)** — local wireless LANs.
  * **Cellular (LTE/5G)** — wide area mobile networks.
  * **Satellite** — global coverage; high latency.
  * **Bluetooth** — PAN short-range.

---

## 9) Common physical layer devices *

* **Transceiver (PHY):** Converts digital bits to physical signals and vice versa; often on NICs.
* **Network Interface Card (NIC):** Hardware on host; implements physical & data link functions.
* **Hub / Repeater:** Layer-1 devices that regenerate and forward electrical signals (no frame inspection). Hubs are largely obsolete (replaced by switches).
* **Media converters:** Convert between media types (e.g., copper ↔ fiber).
* **Modem (modulator-demodulator):** Modulates digital signals for analog media (e.g., ADSL).
* **Line driver / Optical transceiver modules (SFP/SFP+)** for fiber links.

---

## 10) Physical layer standards & real examples

* **Ethernet family**

  * **10BASE-T:** 10 Mbps over UTP (Cat3+, RJ45).
  * **100BASE-TX:** 100 Mbps over Cat5.
  * **1000BASE-T:** 1 Gbps over Cat5e/Cat6.
  * **10GBASE-T:** 10 Gbps over Cat6a/Cat7 (shorter distances).
  * **1000BASE-SX/LX, 10GBASE-SR/LR** for fiber.
* **Wi-Fi (IEEE 802.11)**

  * PHY specs define radio bands, channel widths, modulation (11n, 11ac/ax).
* **DSL (ADSL/VDSL):** uses telephone copper for broadband with modulation.
* **DOCSIS:** cable modem standard for cable TV infrastructure.

---

## 11) Noise, impairments & limits

* **Attenuation:** signal weaker with distance — solved with repeaters, amplifiers.
* **Thermal noise, EMI (electromagnetic interference):** sources: motors, fluorescent lights, nearby radio transmitters.
* **Crosstalk:** interference from adjacent wire pairs (NEXT, FEXT in twisted pair).
* **Dispersion (fiber):** pulse spreading, limits gigabit distances.
* **Delay & Latency:** propagation delay (speed of light / medium), processing delay.
* **Jitter:** variation in packet arrival time — critical for real-time apps.
* **Error rates increase** with noise; physical layer cannot correct many errors (higher layers detect/retransmit).

---

## 12) Channel capacity — Shannon’s idea (short)

Shannon’s formula (conceptual) gives maximum achievable data rate for a noisy channel:

> Capacity ( C = B \log_2(1 + \text{SNR}) ) bits/sec
> where (B) is channel bandwidth (Hz) and SNR is signal-to-noise ratio.

Meaning: with more bandwidth and higher SNR you can send more bits per second — but physical limits exist.

---

## 13) Security implications at physical layer

* **Tapping / wiretapping:** physical access to cable allows eavesdropping (fiber is harder but still possible).
* **Jamming:** wireless networks can be jammed by noise sources or deliberate attackers.
* **Physical access controls** are essential: locked server rooms, sealed fiber conduits.
* **Layered security:** physical security + encryption at higher layers (TLS/IPsec) to protect data.

---

## 14) Troubleshooting & practical tests

* **Cable testers** (continuity, wire mapping, split pairs).
* **Time Domain Reflectometer (TDR):** finds breaks and distance to faults in cable.
* **Optical Power Meter / Light Source:** for fiber testing.
* **Loopback tests** on NICs to test transmit/receive function.
* **Oscilloscope / Spectrum analyzer:** visualize signals, measure noise and jitter.
* **Ping / traceroute** are higher-level but help infer physical problems (packet loss, latency spikes).
* **Common symptoms of layer-1 faults:** link light off, continuous CRC errors, intermittent connectivity, very low throughput.

---

## 15) Example walkthrough: HTTP request across physical layer

1. Browser forms HTTP request (application).
2. Data is broken into TCP segments (transport) and IP packets (internet).
3. **Physical layer** (on sender NIC): encodes bits, uses PHY to convert to electrical/optical pulses.
4. Signal travels over cable/fiber/wireless.
5. Receiver PHY converts pulses → bits and provides them to data link layer for frame reassembly.

---

## 16) Practical lab exercises (great for beginners)

* Use **Ethernet cables**: build straight vs crossover cables; test with cable tester.
* Set up a **simple serial link** between two microcontrollers (TTL levels) to see bits on an oscilloscope.
* Use **Wi-Fi analyzer app** to see channels, signal strength, interference.
* Try **modem tones** with an old dial-up modem to hear FSK/PSK.
* Measure **ping times** over Wi-Fi vs wired to observe latency/jitter differences.

---

## 17) Quick reference: connectors & common usages

* **RJ-45** — Ethernet twisted pair (Cat5e/Cat6).
* **BNC / F-type** — coax (legacy Ethernet, cable TV).
* **LC / SC / ST** — fiber optic connectors.
* **SFP / SFP+ modules** — pluggable transceivers for fiber/copper on switches.
* **DB-9 / DB-25** — old serial connectors used for console/serial links.

---

## 18) Common interview questions (and short answers)

* **Q: What is the difference between bit rate and baud?**
  A: Bit rate = bits/sec. Baud = symbols/sec. A symbol can encode multiple bits.
* **Q: Why use twisted pair cables?**
  A: Twisting reduces electromagnetic interference and crosstalk.
* **Q: What device operates at Layer 1?**
  A: Repeaters and hubs (they regenerate/transmit signals only).
* **Q: Why use fiber instead of copper?**
  A: Higher bandwidth, longer distances, immune to EMI.
* **Q: What is Manchester encoding good for?**
  A: Clock recovery — each bit has a transition enabling synchronization.

---

## 19) Summary — the essential takeaways

* The **Physical Layer** is responsible for the **physical transmission of raw bits** across a medium.
* It covers **media**, **connectors**, **signaling**, **encoding**, **modulation**, **multiplexing**, and **devices** like NICs and repeaters.
* Physical layer design choices determine throughput limits, distance, and robustness to noise.
* While higher layers handle reliability and applications, **if Layer 1 fails — nothing above it will work**.
