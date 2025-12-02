# Better Logger

> **The modern iOS log viewer with AI integration and lane-based organization**

Better Logger is a powerful macOS application for viewing, organizing, and analyzing iOS device logs. With unique lane-based categorization, MCP (Model Context Protocol) integration for AI assistants, and a beautiful grid view, it transforms how developers debug iOS applications.

![macOS](https://img.shields.io/badge/platform-macOS-blue)

## ✨ Features

### 🎯 Core Features

- **Real-Time Log Streaming** - Stream logs from iOS simulators and physical devices with live updates
- **Lane-Based Organization** - Automatically categorize logs into color-coded lanes for easy navigation
- **Lanes Grid View** - Visual side-by-side comparison of logs organized by lanes with resizable columns
- **Custom Format Parsing** - Configure regex patterns to parse any log format with built-in presets
- **MCP Integration** - Full Model Context Protocol support for AI assistants like Cursor
- **Session Management** - Save, load, and export log sessions for later analysis
- **Advanced Search & Filtering** - Search by text, filter by level, lane, process, or subsystem
- **Source Location Extraction** - Automatically parse file, line number, and method from logs
- **Device Management** - Support for iOS Simulators

### 🚀 Unique Selling Points

- **First iOS Logger with MCP Support** - Integrate with AI assistants for intelligent log analysis
- **Visual Grid View** - See all log lanes side-by-side in a beautiful grid layout
- **One-Time Purchase** - $9.99 lifetime license, no subscriptions
- **Memory Optimized** - Smart memory management for handling large log streams
- **Native macOS App** - Built with SwiftUI for a native, responsive experience

## 📸 Screenshots

> _Screenshots coming soon_

## 🚀 Installation

### Requirements

- macOS 13.0 (Ventura) or later
- Xcode (for iOS Simulator support)

### Download

1. Download the latest release from [Releases](https://github.com/nedimf/betterloggermcp/releases)
2. Open the `.dmg` file
3. Drag Better Logger to Applications
4. Launch Better Logger

## 📖 Usage

### Getting Started

1. **Select a Device**
   - Choose an iOS Simulator or physical device from the sidebar
   - Booted simulators appear at the top

2. **Select an App**
   - Click the app picker button or enter a Bundle ID manually
   - Choose "All Apps" to stream all logs

3. **Start Streaming**
   - Click the "Start" button to begin streaming logs
   - Logs will appear in real-time with automatic lane discovery

4. **Organize with Lanes**
   - Lanes are automatically discovered from formatted logs
   - Toggle lanes on/off to focus on specific categories
   - Use the Lanes Grid View (⌘G) for side-by-side comparison

### Lane Format

Better Logger automatically discovers lanes from logs formatted like:

```
[CATEGORY](level) [File.swift:42 method()] Your log message
```

Example:
```
[NETWORK](info) [APIService.swift:150 fetchUsers()] GET /api/users - 200 OK
[UI](debug) [LoginView.swift:25 viewDidLoad()] Login screen appeared
[AUTH](warning) [AuthManager.swift:80 validateToken()] Token expiring soon
```

### Keyboard Shortcuts

- `⌘S` - Save current session
- `⌘G` - Open Lanes Grid View
- `⇧⌘H` - Open Saved Sessions
- `⇧⌘M` - Toggle MCP Server
- `⌘,` - Open Settings

### Custom Log Format

1. Open Format Settings (gear icon)
2. Choose a preset or create custom patterns
3. Configure Lane Pattern (regex) to extract category and level
4. Configure Source Pattern (regex) to extract file, line, and method
5. Test your patterns with sample log messages

## 🤖 MCP Integration

Better Logger includes a full MCP (Model Context Protocol) server, enabling integration with AI assistants like Cursor.

### Setup for Cursor

1. Start the MCP Server in Better Logger (View → Start MCP Server)
2. Click the MCP status indicator in the toolbar
3. Click "Install Bridge" - this installs the bridge to `~/.better-logger/mcp-bridge`
4. Copy the generated Cursor config
5. Add it to `~/.cursor/mcp.json`
6. Restart Cursor

### Available MCP Tools

- `list_devices` - List available iOS simulators and physical devices
- `list_sessions` - List saved log sessions
- `list_lanes` - List discovered log lanes
- `get_logs` - Get current live logs (with filters: lane, level, search, limit)
- `get_session_logs` - Get logs from a saved session
- `start_log_stream` - Start streaming logs from a device
- `stop_log_stream` - Stop the current log stream

### Example: Using with Cursor AI

```
You: "Show me all network errors from the current log stream"

Cursor: [Uses get_logs tool with level=error and lane=NETWORK]
```

## 📝 Log Format Examples

### Default Format
```
[GENERAL](debug) [AppDelegate.swift:20 applicationDidFinishLaunching()] App launched
```

### Custom Format Example
If your logs use a different format, configure custom patterns:

**Input:** `[2024-01-15 10:30:45] [ERROR] [AuthService] Login failed`

**Lane Pattern:** `\[(\w+)\]` (captures "AuthService")
**Source Pattern:** (optional, if you include file:line in logs)

## 🔧 Troubleshooting

### MCP Server Not Starting

1. Check if port 8765 is already in use
2. Ensure firewall allows local connections
3. Check MCP debug logs in the status popover

### Logs Not Appearing

1. Verify the simulator is selected
2. Check that the app is running on the device
3. Try "All Apps" instead of a specific bundle ID
4. Ensure logs are using a supported format

## 🙏 Acknowledgments

- Built with SwiftUI
- MCP protocol implementation based on [Model Context Protocol specification](https://modelcontextprotocol.io)
---

Made with ❤️ for iOS developers

