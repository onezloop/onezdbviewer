# onezloop/onezdbviewer `BETA`

A lightweight and efficient database viewer application for MariaDB/MySQL databases with a modern React-based interface.

## Quick Start

Run the application with Docker:

```bash
docker run -d -p 9977:9977 --name onezdbviewer onezloop/onezdbviewer:latest
```

Open your browser and navigate to: **http://localhost:9977**

## Features

- **Lightweight & Memory Efficient**: Minimal resource consumption
- **Modern UI**: Clean React-based interface with dark/light theme support
- **Connection Management**: Save and manage multiple database connections with encrypted password storage
- **SQL Query Execution**: Execute queries with pagination and real-time results
- **Data Export**: Export query results to CSV format
- **Cross-platform**: Runs in any modern web browser

## Usage

1. **Connect to Database**: Click "New Connection" and enter your MariaDB/MySQL credentials
2. **Browse Tables**: Explore databases and tables in the left sidebar
3. **Execute Queries**: Use the query editor to run SQL commands
4. **Export Data**: Export results to CSV format
5. **Manage Connections**: Save frequently used connections for quick access

## Environment Variables

- `PORT`: Server port (default: 9977)

## Volumes

The application stores connection profiles and settings in the container. To persist data:

```bash
docker run -d -p 9977:9977 \
  -v onezdbviewer-data:/root/.onezdbviewer \
  --name onezdbviewer \
  onezloop/onezdbviewer:latest
```

## Security
Found issues? Report it here - [Issues](https://github.com/onezloop/onezdbviewer/issues)
- Connection passwords are encrypted before storage
- No database credentials are exposed in logs
- Secure SSL/TLS support for database connections

## Issues
Found issues? Report it here - [Issues](https://github.com/onezloop/onezdbviewer/issues).
