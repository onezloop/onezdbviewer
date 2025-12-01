# onezDBViewer `BETA` - User Guide

A completely free database viewer application to connect and manage your MariaDB databases with ease.

> We never collect user data or any kind of telemetry data.


<img width="1920" height="873" alt="onezdbviewer_screen" src="https://github.com/user-attachments/assets/1e7eb710-b4bf-4504-b0c6-7b3a31a60bd2" />


## Introduction

onezDBViewer is a lightweight, modern database viewer application designed specifically for MariaDB/MySQL databases. Built with efficiency in mind, it provides a clean interface for database exploration, query execution, and data management without consuming excessive system resources.

## Installation

### Docker Installation

onezDBViewer is available as a Docker image for easy deployment:

```bash

# Run the container with volume for data persistence
docker run -d -p 9977:9977 \
  -v onezdbviewer-data:/root/.onezdbviewer \
  --name onezdbviewer \
  onezloop/onezdbviewer:latest
```

After starting the container, access the application at `http://localhost:9977` in your web browser.

## Connecting to a Database

### Adding a New Connection

1. **Open Connection Form**: Click the "New Connection" button or the "+" icon in the sidebar
2. **Enter Connection Details**:

   - **Connection Name**: A friendly name for your connection (e.g., "Production DB")
   - **Host**: Database server hostname or IP address
   - **Port**: Database port (default: 3306 for MariaDB/MySQL)
   - **Username**: Database username
   - **Password**: Database password (encrypted when saved)
   - **Database Name**: Initial database to connect to

3. **Save Connection**: Click "Connect" to establish connection and save profile

### Managing Connections

- **Switch Connections**: Click on any saved connection in the sidebar to switch
- **Edit Connection**: Click the edit icon next to a connection name
- **Delete Connection**: Click the delete icon and confirm removal
- **Auto-Connect**: The application automatically reconnects to your last used connection

### Theme Options

- **Light Mode**: Clean, bright interface
- **Dark Mode**: Easy on the eyes for low-light environments
- **System Theme**: Automatically matches your operating system preference

## Troubleshooting

### Common Issues

**Connection Failed**:

- Verify host, port, username, and password
- Check if database server is running
- Ensure network connectivity to database server
- Verify database user has proper permissions

## Found Issues?

For issues, feature requests, or bug reports, please visit our GitHub repository:

**Issue Tracker**: [https://github.com/onezloop/onezdbviewer/issues](https://github.com/onezloop/onezdbviewer/issues)

When reporting issues, please include:

- Application version (found in Settings)
- Operating system and version
- Database server type and version
- Steps to reproduce the issue
- Any error messages displayed

---

Happy database exploring! 🚀

