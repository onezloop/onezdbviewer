# onezDBViewer BETA - User Guide

**OnezDBViewer** is a lightweight, privacy-focused database viewer designed for developers who need a simple, efficient way to explore and manage their MySQL/MariaDB and PostgreSQL databases. Built with performance and security in mind, it's the perfect companion for database exploration without the bloat.

<img width="1918" height="872" alt="onezDBViewer1 - Copy" src="https://github.com/user-attachments/assets/1a7cda96-82b2-437b-9c3f-a047105e95bd" />


## Why onezdbviewer?

We have used lots of database tools. Many of them felt heavy, not modern enough, or too slow for simple querying and checks. So we built onezdbviewer to be modern, straight to the point, simple to use, and fast.

We give ultimate preference to privacy. Because our users connect to databases that store user data and other sensitive information, we never collect any data from the app – not even telemetry or error reports. Your data stays on your machine only.

## What onezdbviewer is?

It's a simple DB viewer tool that is fast and easy to use. Just connect and query – that's it.

Almost all developers use Docker, so we provide onezdbviewer as a Docker image that you can just run and start querying. It is completely free to use.

## What onezdbviewer is not?

onezdbviewer is not a huge SQL script writing tool. We didn't build it for that. While you can still write queries, format them, and use them, we didn't design it for very heavy query authoring workflows.

In today's world, AI can write most SQL, and we as developers can review and correct it as needed. onezdbviewer, at least as of today, is not an open-source project. We are still actively focusing on adding features and refinements that simplify database querying and viewing even more, and we're not yet ready to open source it.

## How did we build it?

We leverage AI extensively to build onezdbviewer. We relied on AI to explore and understand many database-level details and edge cases we needed to support.

We didn't just vibe-code it – we followed a systematic, AI-driven development approach. If you want to know more about AI-driven development, you can explore the following projects:

- https://openspec.dev/
- https://github.com/github/spec-kit
- https://github.com/bmad-code-org/BMAD-METHOD

---

## 🌟 Why Choose OnezDBViewer?

### 🔒 **Privacy First**

- **Zero Telemetry**: We don't collect any usage data, analytics, or telemetry
- **Your Data Stays Yours**: All connection information remains on your machine
- **Local Encryption**: Database passwords are encrypted and stored locally
- **No Cloud Dependencies**: Fully self-contained application

### ⚡ **Built for Performance**

- **Lightweight**: Minimal resource consumption - perfect for containers
- **Efficient Memory Management**: Stream large datasets without loading everything into memory
- **Smart Connection Pooling**: Optimized database connections for responsive queries
- **Stateless Architecture**: Clean, scalable design for reliable operations

### 🎯 **Simple Yet Powerful**

- **Multi-Database Support**: Connect to MySQL, MariaDB, and PostgreSQL
- **Multiple Connections**: Manage and switch between multiple databases effortlessly
- **Read-Only Mode**: Prevent accidental modifications with global read-only protection
- **Modern Interface**: Clean, intuitive UI with dark/light theme support
- **Multi-Tab Workspace**: Work on multiple queries and tables simultaneously

### 💰 **Completely Free**

- **100% Free**: No hidden costs, no premium tiers, no subscriptions
- **No Upselling**: Every feature is available to everyone

## 🚀 Quick Start

### Running the Container

Get started in seconds with a single command:

```bash
docker run -d -p 9977:9977 \
  -v onezdbviewer-data:/root/.onezdbviewer \
  --name onezdbviewer \
  onezloop/onezdbviewer:latest
```

Once the container is running, open your browser and navigate to:

```
http://localhost:9977
```

### What This Command Does

- **`-d`**: Runs the container in detached mode (background)
- **`-p 9977:9977`**: Maps port 9977 from container to your host machine
- **`-v onezdbviewer-data:/root/.onezdbviewer`**: Creates a persistent volume for your data
  - Saves database connection profiles
  - Preserves encryption keys for password storage
  - Maintains your workspace and preferences
- **`--name onezdbviewer`**: Names the container for easy management

## 📋 Common Operations

### Stop the Container

```bash
docker stop onezdbviewer
```

### Start the Container

```bash
docker start onezdbviewer
```

### View Container Logs

```bash
docker logs onezdbviewer
```

### Follow Logs in Real-Time

```bash
docker logs -f onezdbviewer
```

### Remove the Container

```bash
docker stop onezdbviewer
docker rm onezdbviewer
```

**Note**: Your data persists in the `onezdbviewer-data` volume even after removing the container.

**Warning**: All connection profiles and settings will be lost when the container is removed.

### Update to Latest Version

```bash
# Pull the latest image
docker pull onezloop/onezdbviewer:latest

# Stop and remove the old container
docker stop onezdbviewer
docker rm onezdbviewer

# Start with the new image (same data volume)
docker run -d -p 9977:9977 \
  -v onezdbviewer-data:/root/.onezdbviewer \
  --name onezdbviewer \
  onezloop/onezdbviewer:latest
```

## 🎨 Key Features

### Database Management

- **Multi-Database Connections**: Save and manage multiple database profiles
- **Encrypted Passwords**: Your credentials are encrypted and stored securely
- **Quick Switching**: Easily switch between different database connections

### Query Interface

- **SQL Query Execution**: Run queries with real-time results
- **Multi-Tab Support**: Work on multiple queries simultaneously
- **Result Filtering**: Filter and sort results directly in the interface

### Data Operations

- **Table Browsing**: Explore tables with pagination for large datasets
- **Data Export**: Export query results and tables to CSV format
- **Streaming Export**: Handle large exports without memory issues
- **Read-Only Mode**: Enable globally to prevent accidental data modifications

### User Experience

- **Modern UI**: Clean, responsive interface that works on any device
- **Theme Support**: Choose between light and dark modes
- **Tab Persistence**: Your workspace is automatically saved and restored
- **Smart Notifications**: Contextual alerts that auto-dismiss

## 💾 Data Export

When running in Docker, all exports (SQL dumps and CSV files) are automatically downloaded through your browser:

- **Browser Downloads**: Files go directly to your browser's download folder
- **No Volume Mounting Needed**: No need to mount export directories
- **No Docker Copy Required**: No need to use `docker cp` commands
- **Efficient**: Files are streamed on-demand without storing in the container

---

## 🌐 Network Considerations

### Connecting to Databases

#### Database on Host Machine

Use `host.docker.internal` to connect to databases running on your host:

```
Host: host.docker.internal
Port: 3306 (MySQL) or 5432 (PostgreSQL)
```

#### Database in Another Container

Use Docker networks to connect containers:

```bash
# Create a network
docker network create dbviewer-network

# Run your database (example with MySQL)
docker run -d --name mysql-db \
  --network dbviewer-network \
  -e MYSQL_ROOT_PASSWORD=password \
  mysql:8

# Run OnezDBViewer on the same network
docker run -d -p 9977:9977 \
  --network dbviewer-network \
  -v onezdbviewer-data:/root/.onezdbviewer \
  --name onezdbviewer \
  onezloop/onezdbviewer:latest
```

Then connect using the container name:

```
Host: mysql-db
Port: 3306
```

#### Remote Database

For databases on remote servers, use their hostname or IP address as you normally would:

```
Host: db.example.com
Port: 3306
```

---

## 🔍 Troubleshooting

### Container Won't Start

Check if the port is already in use.

```bash
# If port is in use, either stop the other service or use a different port
docker run -d -p 8080:9977 ...
```

### Cannot Connect to Database

1. **Check Network Connectivity**: Ensure the database is reachable from the container
2. **Verify Credentials**: Double-check username, password, and database name
3. **Firewall Rules**: Ensure the database server allows connections from Docker
4. **Database Running**: Verify your database server is running and listening

### Lost Saved Connections

Ensure you're using a persistent volume (`-v onezdbviewer-data:/root/.onezdbviewer`) and that the volume is properly mounted. Check volume exists:

### View Application Logs

```bash
docker logs onezdbviewer
```

## 📖 Additional Resources

- **GitHub Repository**: https://github.com/onezloop/onezdbviewer
- **Issue Tracker**: https://github.com/onezloop/onezdbviewer/issues
- **Docker Hub**: https://hub.docker.com/r/onezloop/onezdbviewer
- **Discussion Forum**: https://github.com/onezloop/onezdbviewer/discussions

## 🆘 Need Help?

If you encounter any issues or have questions:

1. Check the troubleshooting section above
2. Review the container logs: `docker logs onezdbviewer`
3. Visit our GitHub issues page - https://github.com/onezloop/onezdbviewer/issues
4. Ensure you're using the latest version
5. Create issue on GitHub here - [New Issue](https://github.com/onezloop/onezdbviewer/issues/new)
6. Ask questions here - https://github.com/onezloop/onezdbviewer/discussions

---

**Happy DB Hacking** 🚀

