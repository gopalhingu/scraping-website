# Scraping Website API

A Node.js web scraping API built with Express.js, supporting multiple scraping engines including Playwright and Puppeteer. This API provides endpoints to scrape websites and retrieve IP information.

## Features

- 🌐 **Web Scraping**: Scrape websites using Playwright or Puppeteer
- 📄 **HTML Processing**: Clean HTML content and convert to markdown/text
- 🔍 **IP Information**: Get your public IP address and location details
- 🚀 **Express API**: RESTful API endpoints for easy integration
- ⚡ **Fast & Efficient**: Headless browser automation for dynamic content

## Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18 or higher recommended)
- **npm** (comes with Node.js) or **yarn**
- **Git** (for cloning the repository)

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/gopalhingu/scraping-website.git
cd scraping-website
```

### 2. Install Dependencies

Install all required packages using npm:

```bash
npm install
```

This will install the following dependencies:
- **express** - Web framework for Node.js
- **playwright** - Browser automation library
- **puppeteer** - Headless Chrome browser automation
- **axios** - HTTP client for making requests
- **turndown** - HTML to Markdown converter
- **dotenv** - Environment variable management
- **nodemon** - Development server with auto-reload
- **@sparticuz/chromium** - Chromium binary for serverless environments

### 3. Install Browser Binaries

After installing npm packages, you need to install browser binaries:

**For Playwright:**
```bash
npx playwright install chromium
```

**For Puppeteer:**
Puppeteer will automatically download Chromium on first run, but you can also install it manually:
```bash
npx puppeteer browsers install chrome
```

### 4. Environment Configuration

Create a `.env` file in the root directory (optional):

```bash
PORT=3000
```

If no `.env` file is provided, the server will default to port 3000.

## Usage

### Start the Development Server

```bash
npm start
```

This will start the server using `nodemon`, which automatically restarts the server when you make changes to the code.

The API will be available at `http://localhost:3000` (or the port specified in your `.env` file).

### Start the Production Server

If you want to run without nodemon (for production):

```bash
node server.js
```

## API Endpoints

### 1. Get IP Information

Get your public IP address and location details.

**Endpoint:** `GET /api/scrape/ip`

**Example Request:**
```bash
curl http://localhost:3000/api/scrape/ip
```

**Example Response:**
```json
{
  "source": "ip",
  "data": {
    "ip": "xxx.xxx.xxx.xxx",
    "city": "City Name",
    "region": "Region",
    "country": "Country Code",
    ...
  }
}
```

### 2. Scrape with Playwright

Scrape a website using Playwright.

**Endpoint:** `POST /api/scrape/playwright`

**Request Body:**
```json
{
  "url": "https://example.com"
}
```

**Example Request:**
```bash
curl -X POST http://localhost:3000/api/scrape/playwright \
  -H "Content-Type: application/json" \
  -d '{"url": "https://example.com"}'
```

**Example Response:**
```json
{
  "source": "playwright",
  "data": "Cleaned HTML content..."
}
```

### 3. Scrape with Puppeteer

Scrape a website using Puppeteer.

**Endpoint:** `POST /api/scrape/puppeteer`

**Request Body:**
```json
{
  "url": "https://example.com"
}
```

**Example Request:**
```bash
curl -X POST http://localhost:3000/api/scrape/puppeteer \
  -H "Content-Type: application/json" \
  -d '{"url": "https://example.com"}'
```

**Example Response:**
```json
{
  "source": "puppeteer",
  "data": "Cleaned HTML content..."
}
```

## Project Structure

```
scraping-website/
├── server.js          # Main server file with API endpoints
├── package.json       # Dependencies and scripts
├── .env              # Environment variables (create this)
└── README.md         # This file
```

## Technologies Used

- **Express.js** - Web application framework
- **Playwright** - Browser automation and testing
- **Puppeteer** - Headless Chrome Node.js API
- **Axios** - Promise-based HTTP client
- **Turndown** - HTML to Markdown converter
- **dotenv** - Environment variable loader

## Development

The project uses ES modules (`type: "module"` in package.json), so all imports use the `import` syntax instead of `require()`.

## Troubleshooting

### Browser Installation Issues

If you encounter issues with browser binaries:

1. **Playwright**: Run `npx playwright install chromium` again
2. **Puppeteer**: Delete `node_modules` and reinstall: `rm -rf node_modules && npm install`

### Port Already in Use

If port 3000 is already in use, change the `PORT` in your `.env` file or set it as an environment variable:

```bash
PORT=3001 npm start
```

## License

ISC

## Repository

GitHub: https://github.com/gopalhingu/scraping-website.git
