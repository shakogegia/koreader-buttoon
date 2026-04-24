# KOReader Button

A tiny wireless page turner for [KOReader](https://koreader.rocks/). Short press for next page, long press for previous page.

Built with a Seeed XIAO ESP32-C6 running [ESPHome](https://esphome.io/), housed in a 3D-printed case.

![KOReader Button](picture.jpeg)

## How It Works

The button connects to your Wi-Fi and sends HTTP requests to KOReader's built-in web server:

- **Short press** - next page
- **Long press** (800ms+) - previous page

KOReader host and port are configurable through a built-in web UI (port 80).

## Parts

| Part | Description |
|------|-------------|
| ![ESP32-C6](images/parts/esp32%20c6.jpg) | **Seeed Studio XIAO ESP32-C6** |
| ![Push button](images/parts/push%20button.jpg) | **Momentary pushbutton switch** (12x12x7.3mm) |
| ![Battery](images/parts/battery.jpg) | **680mAh LiPo battery** (802530) |
| ![On/off switch](images/parts/on-off%20switch.jpg) | **Slide switch** SS12D00G4 (on/off) |
| ![Screw](images/parts/screw.png) | **M1.7x8 screw** (to close the case) |

## Circuit

![Circuit diagram](images/Circuit.png)

- **Push button** connects to **GND** and **GPIO2 (D0)**
- **Slide switch** goes between the **battery** and the ESP32 power input
- **Battery** plugs into the XIAO's built-in JST connector

## Assembly

The 3D-printed case holds everything snugly. The lid has a hole for the on/off switch.

| | |
|---|---|
| ![Inside view](images/disassembled/IMG_5668.jpeg) | ![Open case](images/disassembled/IMG_5666.jpeg) |
| ![Assembly](images/disassembled/IMG_5667.jpeg) | ![Full view](images/disassembled/IMG_5669.jpeg) |

## Setup

### 1. KOReader

Enable the HTTP server in KOReader:

**Menu > Network > HTTP server > Start**

Note the IP address and port shown.

### 2. ESPHome

Create a `secrets.yaml` next to the config file:

```yaml
wifi_ssid: "YOUR_WIFI_SSID"
wifi_password: "YOUR_WIFI_PASSWORD"
ota_password: "pick-a-password"
ap_password: "pick-a-password"
```

Flash with ESPHome:

```bash
esphome run koreader-button.yaml
```

### 3. Configure

After flashing, open the device's web UI at its IP address (port 80) and set the KOReader host and port.

## 3D Model

Printable case files are in the [`3d-model/`](3d-model/) folder (STL and 3MF). No supports needed, printed in PLA. Case dimensions: 54x29x16 mm.

Also available on [MakerWorld](https://makerworld.com/en/models/2712283-koreader-button).

## License

MIT
