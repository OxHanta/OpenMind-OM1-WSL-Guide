# Deploy Your First Robot on FABRIC Portal | WSL Guide

<img width="1200" height="732" alt="Image" src="https://github.com/user-attachments/assets/f0f0ddb8-d64a-40da-b065-49fedf504fc7" />

## Installation

### Step 1: Update System and Install Dependencies

Run the following command to update your system and install all required dependencies:

```bash
sudo apt update -y && sudo apt upgrade -y && \
sudo apt install -y portaudio19-dev python3-all-dev ffmpeg alsa-utils curl libasound2-plugins pulseaudio-utils && \
curl -LsSf https://astral.sh/uv/install.sh | sh && \
export PATH="$HOME/.local/bin:$PATH"
```

### Step 2: Clone the Repository

Clone the OM1 repository and navigate into the project directory:

```bash
git clone https://github.com/OpenMind/OM1.git
cd OM1
```

### Step 3: Initialize Submodules

Update and initialize the git submodules:

```bash
git submodule update --init
```

### Step 4: Create Virtual Environment

Create a virtual environment using `uv`:

```bash
uv venv
```

## API Key Configuration

### Obtaining Your OM1 API Key

1. Go to the [OpenMind Fabric Portal](https://portal.openmind.org/)
2. Register with OpenMind or log in if you already have an account
3. Click on **"Purchase Credits"** in the upper right menu
4. Add **5 USDC or any amount** to your balance via the Base network 
5. Click the **"Create API Key"** button to generate a new API key
6. **Important:** Copy the generated key immediately, as you won't be able to see it again after closing the window
<img width="1200" height="732" alt="Image" src="https://github.com/user-attachments/assets/b990788f-a5ff-4fb0-adb4-e94a4a000fde" />


### Adding Your API Key

1. Locate the `config` folder in your project directory
2. Open `/config/spot.json` (or your preferred config file) using your text editor
3. Add your OpenMind API key to the configuration
<img width="1200" height="732" alt="Image" src="https://github.com/user-attachments/assets/77df1e80-733f-490a-9c67-99dabb16d135" />

> **Note:** Using the placeholder key `openmind_free` will generate errors. Always use your actual API key.

## Mint Your Agent

Before running your agent, you need to mint it on the blockchain.

1. Go to the [My Devices Page](https://fabric.openmind.org/my-devices)
2. Click on **"Mint Your Agent"**
3. Choose any machine of your choice
4. **Requirement:** You must have at least **0.001 ETH on mainnet** to be eligible for minting
5. Complete the minting process
<img width="1200" height="732" alt="Image" src="https://github.com/user-attachments/assets/6c34daec-2b91-4b32-9053-50fda0de0453" />

## Running Your Agent

Run the following command to start the Spot Agent:

```bash
uv run src/run.py spot
```
Monitor your agent's output in real-time using the WebSim interface.

```
http://localhost:8000
```
### Stopping the Agent

To stop a running agent session, press:

```
Ctrl + C
```

This will gracefully terminate the agent process.

### Switching Agent Configurations

To run a different agent (for example, the conversation agent), specify the configuration name explicitly:

```bash
uv run src/run.py conversation
```
<img width="1200" height="732" alt="Image" src="https://github.com/user-attachments/assets/cd9ffd5e-b697-40e6-a685-f27beb52decc" />

## Bonus Features

### Interactive Agent with ASR and TTS

If you want to interact with the agent using voice input and output, configure ASR (Automatic Speech Recognition) and TTS (Text-to-Speech) in your `spot.json5` file.

#### ASR Configuration

Add the following to the `agent_inputs` section:

```json
{
  "type": "GoogleASRInput"
}
```

#### TTS Configuration

Add the following to the `agent_actions` section:

```json
{
  "name": "speak",
  "llm_label": "speak",
  "connector": "elevenlabs_tts",
  "config": {
    "voice_id": "i4CzbCVWoqvD0P1QJCUL",
    "silence_rate": 20
  }
}
```

### WebSim - Real-Time Monitoring

Monitor your agent's input and output in real-time using the WebSim interface.

1. Start your agent
2. Open your browser and navigate to:

```
http://localhost:8000
```

3. View real-time logs along with input and output in the terminal

#### Debug Mode

For additional logging information and easier debugging, add the `--debug` flag when running your agent:

```bash
python main.py --debug
```


### Getting Help

If you encounter issues not covered in this guide, please:
- Check the [official documentation](https://docs.openmind.org/developing/0_introduction)
- Open an issue on the [GitHub repository](https://github.com/OpenMind/OM1)
