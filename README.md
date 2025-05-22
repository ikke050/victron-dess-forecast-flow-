
# Victron Dynamic ESS Forecast & Grid Control (Node-RED on Cerbo GX)

This project provides a complete Node-RED implementation for enhancing Victron's Dynamic ESS (DESS) behavior using local control logic and improved PV forecast data. It is designed to run entirely on a Victron Cerbo GX with Venus OS Large.

## 🔧 Features

- 📡 **Hourly PV Forecast from PVGIS** (North, East, West orientations)
- 🌦 **Seasonal correction** based on month
- ☁️ **Realtime cloud cover adjustment** using Open-Meteo
- 🔋 **Dynamic Min SOC control** based on expected solar generation
- ⚡ **Price-based solar control**:
  - If electricity price < **–0.14 €/kWh** → disable Fronius and SmartSolar, charge from grid
  - If price ≥ **–0.14 €/kWh** → enable all solar output for self-consumption or export
- 🔌 Works via **MQTT** (local broker on Cerbo GX)
- 🧠 All logic runs **locally** without cloud dependencies

## 📁 Included in the JSON Flow

- Node-RED nodes for forecast pulling, adjustments, and DESS interfacing
- Configurable topics and MQTT messages for Victron GX
- Placeholder values such as:
  - `TIBBER_TOKEN_HERE` for your Tibber API token
  - `LATITUDE`, `LONGITUDE` for PVGIS location
  - `DEVICE_ID` for Victron MQTT base topic
  - `FRONIUS_IP_1/2/3` for Fronius inverters (Modbus TCP)

## 🛠 Requirements

- Cerbo GX with **Venus OS Large**
- Node-RED installed and running
- MQTT enabled on Cerbo GX (Local or LAN)
- Optional: Tibber API access for realtime pricing
- Optional: dbus-mqtt bridge for advanced Victron control via MQTT

## 🔽 How to Use

1. Import `dess_forecast_control_anonymized.json` into Node-RED.
2. Update:
   - MQTT topics with your actual Victron device ID
   - Fronius IP addresses
   - Tibber token (if used)
   - GPS coordinates for your solar system
3. Deploy and monitor flows via debug nodes
4. Optional: connect to Victron VRM or external dashboard

## 📢 Notes

This solution was developed in response to inaccurate or erratic energy forecasts within DESS. By taking full control of the forecast input and combining it with dynamic rules based on weather and price, you gain much better control over battery usage and grid interaction.

Tested on real-world systems with oversized PV, multiple orientations, and dynamic tariffs.

## 📫 Questions?

Feel free to reply to this post or tag @ikke050 on the Victron Community Forum.
