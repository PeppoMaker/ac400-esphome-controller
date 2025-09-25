# AC400 ESPHome Controller

Replacement of the original **Record Power AC400** controller with a **LilyGo T-Relay ESP32** board, fully integrated with **ESPHome + Home Assistant**.

## ⚠️ Disclaimer

- This project involves working with **230V AC mains voltage** ⚡.  
- Proceed only if you have electrical safety knowledge and experience.  
- The author takes no responsibility for damage to equipment or injury.

---

## ✨ Features

- Control the AC400 air filter directly from Home Assistant.
- 3 fan speeds: **Low / Medium / High**.
- Automatic shutdown timer.
- Exposed as a `fan` entity in Home Assistant.

---

## 🔧 Hardware required

- [LilyGo T-Relay ESP32 5V](https://lilygo.cc/products/t-relay)
  <img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/ef0c713e-f844-42cb-9574-a5446ba7de8e" />
- [LILYGO TTGO T-U2T USB to TTL](https://lilygo.cc/products/t-u2t)
- 5V DC power supply (≥1A recommended)
- 2–5A fuse (fast/slow depending on motor spec)
- RC snubber or MOV surge protection across relays
- Proper cabling (1–1.5 mm² for mains)

---

## 📑 Software

ESPHome config file: [`firmware/ac400.yaml`](firmware/AC400.yaml)

Flash it with ESPHome and add the device to Home Assistant.

---

## 📷 Wiring diagram

> Never enable more than one speed at the same time!  
> The YAML enforces an **interlock** to avoid that.

See [hardware/wiring-diagram.png](hardware/wiring-diagram.png)

🔌 Typical connections
On the LilyGo T-Relay each relay has 3 pins: COM, NO (Normally Open), NC (Normally Closed). You will use COM + NO.
1. Relay 1 (GPIO21 → rel_low)
    * COM → one side of the Low button contact
    * NO → the other side of the Low button contact
2. Relay 2 (GPIO19 → rel_med)
    * COM → one side of the Medium button contact
    * NO → the other side of the Medium button contact
3. Relay 3 (GPIO18 → rel_high)
    * COM → one side of the High button contact
    * NO → the other side of the High button contact
4. Relay 4 (optional, GPIO5)
    * Can be used for Master Power (same principle: in parallel with ON/OFF button)

⚠️ Do not connect mains power directly to the ESP32 board — the relays must always be wired to the low-voltage control side of the AC400 buttons, never to the motor supply lines.


---

## 📜 License

MIT License

