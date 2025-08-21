<div align="center">
  <a href="https://github.com/krysngabi/chibisafe.git">
    <img src="readme-logo.png" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Chibisafe — Secure File Upload and Sharing Platform</h3>
</div>

<p style="text-align: center;">
  This is the Chibisafe project, a secure file upload and sharing platform built with Docker containers. It provides a simple interface for uploading files, serving them via a reverse proxy, and managing storage with a server backend. It uses Caddy as a reverse proxy and supports custom configurations for file serving and API routing.
</p>

## 📦 Features

- ✅ File upload and sharing capabilities
- 🔒 Secure file storage with volume mapping
- 🌐 Reverse proxy with Caddy for routing
- 📂 Customizable upload and database storage
- 🌍 CORS support via Caddy configuration
- 📊 Logging support for server operations
- 💾 Persistent storage with Docker volumes
- ⚡ Lightweight and containerized

## ⚙️ Getting Started (Setup, Run, and Test)

### Built With

This section lists the major frameworks/libraries used to bootstrap the project.

* [![Docker][Docker]][Docker-url]
* [![Chibisafe][Chibisafe]][Chibisafe-url]

## 1. Clone the Project

   ```
   https://github.com/krysngabi/file-vault.git
   ```


## 2. Setup and Run

### Prerequisites

- Docker and Docker Compose installed on your system.
- Ensure sufficient disk space for uploads and logs.

### Steps

1. **Navigate to the Project Directory**
```js
cd file-vault
```

2. **Start the Services**
   Run the following command to start the Chibisafe services using:
```aiignore
docker-compose up -d
```

3. **Verify Services**
- Check the container status in Docker Desktop. All services (`chibisafe`, `chibisafe_server`, and `caddy`) should show a green circle.
- Access the service at `http://localhost:24424` to confirm it’s running.
- Once you can see the home page login with the default user credentials:
   - **Username**: `admin`
   - **Password**: `admin`
- Once logged in, you can create a new user called `central-user` or use the default user `admin`.
- In the left sidebar, go to albums and create a new album called `central-app` and copy its uuid by hovering over the album name. This will be used in the next step.

## 3. Configuration

- **Volume Mappings:**
- `./database:/app/database:rw` - Stores database files.
- `./uploads:/app/uploads:rw` - Stores uploaded files.
- `./logs:/app/logs:rw` - Stores server logs.
- Adjust these paths in `docker-compose.yml` to match your local directory structure.

- **Environment Variables:**
- `BASE_API_URL=http://chibisafe_server:8000` - Sets the API endpoint for the Chibisafe client.

- **Ports:**
- `24424:80` - Maps the host port 24424 to the Caddy container's port 80.

## 4. Additional Notes

- **Storage Management**: Ensure the **./uploads**, **./database**, and **./logs** directories exist locally or are created automatically by Docker with appropriate permissions.
- **Restart Policy**: The `unless-stopped` restart policy ensures services recover after a system reboot.
- **Access**: Upload files via the web interface at http://localhost:24424 and access them directly from the /uploads path.
- **Troubleshooting**: If you encounter issues, check the logs in the `./logs` directory or use `docker logs <container_name>` to view service logs.

!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[Chibisafe]: https://img.shields.io/badge/file-upload
[Chibisafe-url]: https://github.com/chibisafe/chibisafe?tab=readme-ov-file
[Docker]: https://img.shields.io/badge/docker-257bd6?style=for-the-badge&logo=docker&logoColor=white
[Docker-url]: https://www.docker.com/