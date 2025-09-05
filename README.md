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
- 5V DC power supply (≥1A recommended)
- 2–5A fuse (fast/slow depending on motor spec)
- RC snubber or MOV surge protection across relays
- Proper cabling (1–1.5 mm² for mains)

---

## ⚙️ Wiring

- **Neutral (N)** → directly to motor (Blue wire).
- **Earth (PE)** → directly to motor (Green/Yellow).
- **Live (L)** → from mains → fuse → relay commons.
  - Relay 1 → Grey (Low)
  - Relay 2 → Medium circuit (Brown through capacitor/derivation, same as original PCB)
  - Relay 3 → Brown direct (High)

> Never enable more than one speed at the same time!  
> The YAML enforces an **interlock** to avoid that.

---

## 📑 Software

ESPHome config file: [`firmware/ac400.yaml`](firmware/ac400.yaml)

Flash it with ESPHome and add the device to Home Assistant.

---

## 📷 Wiring diagram

See [hardware/wiring-diagram.png](hardware/wiring-diagram.png)

---

## 📜 License

MIT License

