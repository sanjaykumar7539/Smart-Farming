Smart Farming System
An IoT-based agricultural monitoring system designed for real-time sensor data ingestion, processing, and visualization. The project integrates edge hardware (ESP32) with a Python-based backend (Flask) to track environmental state and agricultural metrics.

🏗️ System Architecture
Hardware & Data Collection: Physical ESP32 microcontrollers or software simulators generate real-time agricultural telemetry (e.g., soil moisture, temperature, humidity).

Data Ingestion & Validation: A serial bridge continuously listens for data payloads, validating them against strict data contracts before processing.

System State Management: Validated readings update a central system memory state, tracking current environmental conditions in real-time.

Web Interface & API: A Flask backend queries the system state and serves the data to a frontend dashboard for visual monitoring.

📁 Project Structure
main.py: Primary entry point for launching the backend and background services.

app/: Contains the Flask web application, routing (routes.py), and frontend interfaces (templates/index.html).

core/: Houses the data pipeline logic, including ingestion (ingest.py), payload validation (validator.py), and system state tracking (state.py).

services/: Runs background operations like the hardware serial bridge (serial_bridge.py) and state updates (state_updater.py).

simulation/: Provides mock hardware environments (mock_esp32.py, sensors.py) to test the system without physical microcontrollers.

esp32_firmware/: Contains the C++/Arduino firmware (esp32_firmware.ino) to be flashed onto physical ESP32 devices.

contract/: Defines the data schemas (data_contract.py) for standardizing incoming sensor payloads.

tests/: Contains the pytest suite for validating state logic and API routing.

logs/: Directory for application monitoring outputs (e.g., ingest.log).

🚀 Getting Started
Prerequisites
Python 3.7+

Arduino IDE (only required if flashing a physical ESP32)

Setup & Execution
Activate the Virtual Environment:
The project relies on a pre-configured venv containing required dependencies like Flask, pyserial, and pytest.

Bash
source venv/bin/activate  # On Linux/macOS
Choose Data Source:

Physical: Flash esp32_firmware/esp32_firmware.ino to your ESP32 board and connect it via serial.

Simulation: Run simulation/mock_esp32.py to generate synthetic real-time sensor telemetry.

Start the Application:

Bash
python main.py
This initializes the web interface, state updaters, and the serial bridge.

🧪 Testing
The project utilizes pytest for automated testing. Run the test suite using:

Bash
pytest
