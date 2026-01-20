# Building Claude Exporter for Safari - Complete Tutorial

## What We're Doing
We're converting the Claude Exporter Chrome extension to work in Safari. Safari extensions need to be wrapped in an Xcode project, but the core JavaScript code will work as-is!

## Prerequisites
✅ macOS (you have this!)
✅ Xcode installed (free from App Store - install if you don't have it)
✅ Safari 15.4 or later
✅ The safari-extension folder (I've created this for you with modified files)

## Step 1: Download the Safari Extension Files

I've prepared all the files for you. Download the `safari-extension` folder that I'll provide.

## Step 2: Use Safari's Web Extension Converter

Apple provides a command-line tool that converts Chrome extensions to Safari format. Here's how to use it:

### Option A: Automatic Conversion (Recommended)

1. Open Terminal
2. Navigate to where you saved the safari-extension folder:
```bash
cd ~/Downloads  # Or wherever you saved it
```

3. Run the converter:
```bash
xcrun safari-web-extension-converter safari-extension --app-name "Claude Exporter" --bundle-identifier "com.yourname.claude-exporter"
```

Replace `yourname` with your name (no spaces, lowercase).

4. The converter will create a new folder called "Claude Exporter" with an Xcode project inside.

### Option B: Manual Creation in Xcode

If the automatic converter doesn't work, follow these steps:

1. **Open Xcode**
2. **File → New → Project**
3. **Select "Safari Extension App"** (under macOS tab)
4. **Fill in the details:**
   - Product Name: Claude Exporter
   - Team: None (or your Apple ID if you have one)
   - Organization Identifier: com.yourname
   - Bundle Identifier: com.yourname.claude-exporter
   - Click Next and save somewhere easy to find (Desktop is fine)

5. **Replace the extension files:**
   - In Finder, navigate to the project folder you just created
   - Find the "Extension" subfolder inside
   - Delete everything inside the Extension folder
   - Copy ALL files from the `safari-extension` folder into this Extension folder
   - In Xcode, right-click on "Extension" in the left sidebar
   - Select "Add Files to Claude Exporter..."
   - Select all the files you just copied and click Add

## Step 3: Configure Build Settings

1. In Xcode, click on the project name at the top of the left sidebar
2. Select the "Claude Exporter Extension" target
3. Under "Signing & Capabilities":
   - If you have an Apple Developer account, select your team
   - If not, select "Sign to Run Locally"
4. Make sure "Automatically manage signing" is checked

## Step 4: Build and Run

1. At the top of Xcode, make sure "My Mac" is selected as the destination
2. Click the Play button (▶) or press Cmd+R
3. Safari will launch automatically
4. If this is your first time, Safari will ask if you want to allow unsigned extensions
   - Go to Safari → Settings → Advanced
   - Check "Show Develop menu in menu bar"
   - Then go to Develop → Allow Unsigned Extensions
5. Restart Safari

## Step 5: Enable the Extension

1. Open Safari → Settings → Extensions
2. Find "Claude Exporter" and check the box to enable it
3. Make sure "claude.ai" has permission (should be automatic)

## Step 6: Configure and Test

1. Go to https://claude.ai and log in
2. Click the Claude Exporter icon in Safari's toolbar (looks like a puzzle piece icon)
3. Click "Click here to set it up" to configure your Organization ID
4. In a new tab, go to https://claude.ai/settings/account
5. Your Organization ID is in the URL - copy it (format: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx)
6. Paste it into the extension options and click Save
7. Click "Test Connection" to verify it works
8. Navigate to any conversation on claude.ai
9. Click the extension icon again
10. Try exporting the conversation!

## Troubleshooting

### Extension doesn't appear in Safari
- Make sure you ran the app at least once from Xcode
- Check Safari → Settings → Extensions
- Make sure "Allow Unsigned Extensions" is enabled (Develop menu)

### "Organization ID not configured" error
- Follow Step 6 carefully
- Make sure you copied the entire UUID from the URL
- It should have dashes in it

### Extension icon not showing in toolbar
- Right-click Safari's toolbar
- Select "Customize Toolbar"
- Drag the extension icon into the toolbar

### Export button doesn't work
- Open Safari's Web Inspector (Develop → Show JavaScript Console)
- Try the export again and look for errors
- Common issue: Make sure you're logged into claude.ai

### Build errors in Xcode
- Make sure all files were added to the project (check the Extension folder in Xcode's sidebar)
- Clean build folder: Product → Clean Build Folder
- Try building again

## What's Next?

Once the extension is working, you can:

1. **Export all your conversations:**
   - Click "Browse All Conversations" in the extension
   - Click "Export All" to download everything as a ZIP

2. **Create a script to import to Apple Notes:**
   - I can help you write a Python/AppleScript to take the exported Markdown files
   - And automatically create notes in Apple Notes
   - This would be a simple script you run once

3. **Set up automation:**
   - Create a script that periodically exports new conversations
   - Automatically syncs them to Apple Notes
   - Could run daily via a Launch Agent

## Need Help?

If you run into issues:
1. Check the troubleshooting section above
2. Look at the Xcode console for errors (View → Debug Area → Activate Console)
3. Check Safari's Web Inspector console while on claude.ai
4. Let me know what error messages you see!

## Tips

- Keep the Xcode project - you'll need it to rebuild if you make changes
- The extension will keep working even after you close Xcode
- To update the extension, modify files in Xcode and rebuild
- Each time you rebuild, you may need to restart Safari

Good luck! This should get you up and running with a Safari version of Claude Exporter.
