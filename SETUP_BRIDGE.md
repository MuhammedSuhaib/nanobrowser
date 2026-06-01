# Setup Guide: Gemini CLI Bridge Integration

This guide documents how to set up and run the Gemini CLI integration with the Nanobrowser extension within a GitHub Codespaces environment.

## 1. Prerequisites
- You are working in the `feature/gemini-cli-integration` branch.
- You have the `gemini` CLI installed in your Linux container environment.

## 2. Server Setup (Bridge)

The bridge server facilitates communication between the browser extension and the local Gemini CLI.

1.  **Install dependencies**:
    ```bash
    pip3 install websockets
    ```
2.  **Start the bridge server**:
    ```bash
    python3 chrome-extension/bridge/bridge.py
    ```
    *Keep this terminal window running.*

## 3. Configure Codespaces Port Forwarding

Since the extension runs in your local browser and the container runs in Codespaces, you must expose the port:

1.  In the Codespaces UI, go to the **Ports** tab.
2.  Add port `8080` if it is not listed.
3.  Right-click the port -> **Port Visibility** -> **Public**.
4.  Copy the forwarded URL (e.g., `https://your-codespace-name-8080.app.github.dev`).

## 4. Update the Side Panel Configuration

You must ensure the extension connects to your specific forwarded URL.

1.  Open `pages/side-panel/src/SidePanel.tsx`.
2.  Locate the `setupBridge` function.
3.  Update the WebSocket URL:
    ```typescript
    // Replace the URL with your actual public Codespace URL
    wsRef.current = new WebSocket('wss://your-codespace-name-8080.app.github.dev');
    ```

## 5. Build and Load Extension

1.  **Build the project**:
    ```bash
    pnpm build
    ```
2.  **Local Installation**:
    - Download the `dist/` directory from Codespaces to your local machine.
    - Go to `chrome://extensions/` in your local browser.
    - Enable **Developer Mode**.
    - Click **Load Unpacked** and select your local `dist/` folder.

## 6. Verification
- Open the extension side panel.
- Check the terminal where `bridge.py` is running—it should show "Browser connected."
- Submit a task; you should see command output streaming in the browser UI.
