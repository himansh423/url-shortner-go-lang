# URL Shortener

## Overview
This is a simple URL shortener written in Go. It generates short URLs using an MD5 hash of the original URL and provides functionality to shorten URLs and redirect users to the original URL.

## Features
- Generate short URLs from long URLs.
- Store URLs in memory (no database required).
- Redirect users from a short URL to the original URL.
- Simple REST API for creating and retrieving short URLs.

## Endpoints

### 1. Root Page
**Endpoint:** `GET /`
- Returns a simple "Hello, world!" message.

### 2. Shorten URL
**Endpoint:** `POST /shorten`
- **Request Body:** JSON containing the original URL.
```json
{
  "url": "https://example.com"
}
```
- **Response:** JSON with the shortened URL ID.
```json
{
  "short_url": "d9736711"
}
```

### 3. Redirect to Original URL
**Endpoint:** `GET /redirect/{short_url}`
- Redirects to the original URL based on the short URL ID.

## Installation and Usage

### Prerequisites
- Go installed on your system.

### Running the Project
```sh
git clone https://github.com/himansh423/url-shortner-go-lang.git
cd url-shortner-go-lang
go run main.go
```

The server will start on port **3000**.

### Example Usage
#### Shorten a URL
```sh
curl -X POST http://localhost:3000/shorten -H "Content-Type: application/json" -d '{"url": "https://github.com/himansh423/"}'
```
Response:
```json
{
  "short_url": "d9736711"
}
```

#### Redirect to Original URL
Visit `http://localhost:3000/redirect/d9736711` in your browser, and it will redirect to `https://github.com/himansh423/`.

## Project Structure
```
url-shortener-go-lang/
├── main.go         # Main application logic
├── README.md       # Documentation
```

## Notes
- This implementation stores data in memory (`urlDB`), meaning all shortened URLs will be lost when the server restarts.
- To make it persistent, consider integrating a database like MongoDB or PostgreSQL.



