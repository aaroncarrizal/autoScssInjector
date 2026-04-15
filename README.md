# Auto SCSS Injector

A development tool that automatically compiles SCSS files and injects the resulting CSS into a webpage for live preview.

## What it does

This tool watches your SCSS files for changes, automatically compiles them to CSS, and injects the CSS into a specified webpage. It eliminates the need for manual refreshes when developing with SCSS by providing real-time preview of your styles.

## Technologies Used

- **Node.js** - JavaScript runtime
- **Puppeteer** - Browser automation for launching and controlling Chrome/Chromium
- **Chokidar** - File watching library to detect SCSS file changes
- **Sass** - SCSS compilation to CSS
- **Dotenv** - Environment variable loading from .env file

## How to Use

1. **Clone the repository**
   ```bash
   git clone https://github.com/aaroncarrizal/autoScssInjector.git
   cd autoScssInjector
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   Create a `.env` file in the root directory with:
   ```
   URL=http://localhost:3000  # The webpage to inject CSS into
   SCSS_SOURCE_FOLDER=./src/scss  # Folder containing your SCSS files
   ```

4. **Run the tool**
   ```bash
   npm run dev
   ```

5. **Develop normally**
   Edit your SCSS files in the specified folder. The tool will automatically detect changes, recompile to CSS, and inject into the webpage.

## How It Works

1. Launches a Chromium browser instance pointing to the URL specified in `.env`
2. Reads all `.scss` files from the folder specified in `SCSS_SOURCE_FOLDER`
3. Compiles SCSS to CSS using the Sass compiler
4. Injects the compiled CSS into the webpage's `<head>` element
5. Watches for changes in SCSS files and repeats steps 3-4 when changes are detected

## Notes

- The browser launches in non-headless mode so you can see the webpage
- The browser window starts maximized
- Only files with `.scss` extension are processed
- Existing injected CSS is replaced with new compilation on each update