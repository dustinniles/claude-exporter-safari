# Claude Exporter for Safari

A Safari extension that allows you to export your Claude.ai conversations and artifacts in various formats with support for bulk exports, artifact extraction, and conversation browsing.

This is a **Safari port** of the excellent [Claude Exporter](https://github.com/agoramachina/claude-exporter) Chrome/Firefox extension by agoramachina.

## Features

- 📥 **Export Individual Conversations** - Export any conversation directly from Claude.ai
- 📚 **Bulk Export** - Export all or filtered conversations as a ZIP file
- 🔍 **Browse & Search** - View all your conversations in a searchable table
- 🔀 **Sort Conversations** - Sort by name, date, project, model, and more
- 🌳 **Branch-Aware Export** - Correctly handles conversation branches
- 📝 **Multiple Formats** - JSON (full data), Markdown, or Plain Text
- 📦 **Artifact Export** - Extract artifacts (code, documents, etc.) as separate files
- 🎯 **Flexible Export Options** - Include/exclude metadata, timestamps, and model information
- 🗂️ **ZIP Archives** - Bulk exports create organized ZIP files
- 🤖 **Complete Model Information** - Preserves and displays model information for all conversations

## Safari-Specific Notes

This Safari version works identically to the Chrome/Firefox versions with a few platform-specific considerations:

- Built as a Safari App Extension (requires macOS 11.0+)
- Requires "Allow Unsigned Extensions" for development use
- Uses Safari's WebExtensions API (Manifest V3)

## Installation

### Requirements
- macOS 11.0 or later
- Safari 15.4 or later
- Xcode (for building from source)

### Building from Source

1. **Clone this repository:**
```bash
git clone https://github.com/YOUR-USERNAME/claude-exporter-safari.git
cd claude-exporter-safari
```

2. **Open the Xcode project:**
```bash
open "Claude Exporter.xcodeproj"
```

3. **Build and run:**
   - Select "My Mac" as the destination
   - Click the Play button (▶) or press Cmd+R
   - Safari will launch with the extension

4. **Enable the extension:**
   - Safari → Settings → Advanced → Check "Show Develop menu in menu bar"
   - Develop → Allow Unsigned Extensions
   - Restart Safari
   - Safari → Settings → Extensions → Enable "Claude Exporter"

### Alternative: Using the Converter Tool

If you have the extension source files from the original Chrome version:

```bash
xcrun safari-web-extension-converter /path/to/chrome/folder \
  --app-name "Claude Exporter" \
  --bundle-identifier "com.yourname.claude-exporter"
```

## Configuration

1. Click the extension icon in Safari's toolbar
2. Click "Click here to set it up"
3. Navigate to https://claude.ai/settings/account
4. Copy your Organization ID from the URL or page
5. Paste it into the extension options and click Save
6. Click "Test Connection" to verify

**Note:** The Test Connection button may show an error even when the extension is working properly. If it fails, try exporting a conversation anyway - it will likely work!

## Usage

### Export Current Conversation
1. Navigate to any conversation on claude.ai
2. Click the extension icon
3. Choose your export format and options
4. Click "Export Current Conversation"

### Export All Conversations
1. Click the extension icon
2. Click "Export All Conversations"
3. Select format and options
4. A ZIP file will download with all conversations

### Browse Conversations
**Note:** The Browse feature may have compatibility issues in Safari. Use the direct export buttons instead.

## Export Formats

### Markdown (Recommended for Apple Notes)
- Human-readable format with formatting preserved
- Optional metadata (creation date, model, timestamps)
- Compatible with Apple Notes' "Import Markdown" feature
- Shows only the current conversation branch

**Pro Tip:** Enable "Metadata" when exporting to include the conversation creation date. When imported to Apple Notes, this preserves the original conversation date!

### JSON
- Complete data including all branches and metadata
- Best for data preservation and programmatic use
- Includes all message versions

### Plain Text
- Simple format with "User:" and "Claude:" prefixes
- Shows only the current conversation branch
- Ideal for copying into other LLMs

## Importing to Apple Notes

1. Export your conversations with "Metadata" enabled
2. In Apple Notes: File → Import → Select your .md files
3. The conversation date will appear at the top of each note!

## Safari-Specific Issues

### Extension doesn't appear
- Make sure "Allow Unsigned Extensions" is enabled (Develop menu)
- Restart Safari
- Check Safari → Settings → Extensions

### Test Connection fails but exports work
This is a known issue - the connection test may fail while the actual export functionality works perfectly. Just try exporting a conversation!

### Browse All Conversations issues
The browse feature may have compatibility issues in Safari. Use the "Export Current Conversation" or "Export All Conversations" buttons from the popup instead.

## Development

### Project Structure
```
Claude Exporter/
├── Claude Exporter Extension/    # Safari extension wrapper
│   ├── Resources/
│   │   ├── manifest.json         # Extension manifest
│   │   ├── background.js         # Background service worker
│   │   ├── content.js            # Content script
│   │   ├── popup.html/js         # Extension popup
│   │   ├── options.html/js       # Options page
│   │   ├── browse.html/js        # Browse conversations page
│   │   ├── utils.js              # Shared utilities
│   │   └── jszip.min.js          # ZIP creation library
│   └── Info.plist
└── Claude Exporter.xcodeproj
```

### Making Changes

1. Edit files in Xcode
2. Build and run (Cmd+R)
3. Test in Safari
4. Commit changes to Git

### Key Differences from Chrome Version

- Added `"type": "module"` to background service worker in manifest.json
- Added Safari-specific browser settings in manifest.json
- Wrapped in Xcode project for Safari App Extension format
- Same core functionality and JavaScript code

## Troubleshooting

### Extension stops working after macOS update
- Re-enable "Allow Unsigned Extensions" in Safari
- Rebuild the project in Xcode

### Can't find Organization ID
1. Go to any claude.ai conversation
2. Open Safari's Web Inspector (Develop → Show Web Inspector)
3. Network tab → Refresh page
4. Look for requests to `/api/organizations/`
5. Copy the UUID after `/organizations/`

### Downloads not working
- Check Safari's download permissions
- Try a different export format
- Check Safari's Web Inspector Console for errors

## Contributing

This is a community port of the original Chrome extension. Contributions welcome!

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly in Safari
5. Submit a pull request

## Credits

- **Original Extension**: [agoramachina/claude-exporter](https://github.com/agoramachina/claude-exporter)
- **Original Author**: socketteer ([Claude-Conversation-Exporter](https://github.com/socketteer/Claude-Conversation-Exporter))
- **Safari Port**: Created with assistance from Claude Sonnet 4.5
- **ZIP Library**: [JSZip](https://stuk.github.io/jszip/)

## License

MIT License - see LICENSE file for details

## Disclaimer

This extension is not officially affiliated with Anthropic or Claude.ai. It's a community tool that uses the web interface's API endpoints.

## Privacy & Security

- **Local Processing**: All data processing happens in your browser
- **No External Servers**: The extension doesn't send data anywhere
- **Your Authentication**: Uses your existing Claude.ai session
- **Open Source**: You can review all code before installation

## Support

For issues specific to the Safari port, please open an issue on this repository.

For general Claude Exporter questions, see the [original repository](https://github.com/agoramachina/claude-exporter).

---

**Happy exporting!** 🎉
