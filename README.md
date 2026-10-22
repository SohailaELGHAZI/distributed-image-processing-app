# Distributed Client/Server Image Processing Application

A Java-based distributed system where clients send images to a remote server for real-time filtering. It supports multiple users simultaneously using **multithreading**, **TCP sockets**, and **Java RMI** (Remote Method Invocation).

> 🎓 **Academic project**: built in 15 days by a team of 2 · Status: ✅ Completed

## 🎬 Video Demo

[![Watch the demo](https://img.youtube.com/vi/7zDbz8VpTCk/maxresdefault.jpg)](https://www.youtube.com/watch?v=7zDbz8VpTCk)

🌐 [Project page in my portfolio](https://sohailaelghazi.vercel.app/projects/m9w3q8b7)

---

## 📖 The Story

### The Problem
Image processing can be computationally heavy, and serving requests from many clients at once raises networking and concurrency challenges. This project explores how image processing can be split between clients and a remote server.

### The Solution
A distributed client/server application in Java: the client sends an image to a remote server, the server applies the selected filter and sends the result back. Communication is implemented in two ways, **raw sockets** and **RMI**, and the server uses **multithreading** to handle several clients at the same time.

---

## ✨ Key Features

- 📤 Remote image upload & download
- ⚡ Real-time filtering
- 👥 Multiple clients served simultaneously (one thread per client)
- 🔌 Socket-based communication
- 📡 RMI remote method calls
- 🖼️ Image filters: **Average**, **Gaussian**, **Sobel**, **Median**

---

## 🛠️ Tech Stack

| Technology | Usage |
|---|---|
| Java SE | Core language |
| Java Sockets | TCP client/server communication |
| Java RMI | Remote method invocation for filtering |
| Multithreading | Handling concurrent clients |
| BufferedImage / ImageIO | Reading, processing and writing images |

---

## 🏗️ Architecture

```
                    ┌──────────────────────┐
                    │       Client         │
                    │  (MyClient – GUI)    │
                    └─────────┬────────────┘
              image + filter  │   filtered image
             ┌────────────────┴─────────────────┐
             ▼                                  ▼
┌────────────────────────┐        ┌────────────────────────┐
│     ServerSocket       │        │       ServerRMI        │
│  MyServerSocket        │        │  MyServerRmi           │
│  → thread per client   │        │  → FiltreRemote (RMI)  │
│  → FiltreSocket        │        │                        │
└────────────────────────┘        └────────────────────────┘
```

## 📁 Project Structure

```
projetFi/
├── client/
│   └── src/ClientServer/
│       ├── MyClient.java        # Client application (UI + sending/receiving images)
│       └── Filtrer.java         # Shared filter interface
├── ServerRMI/
│   └── src/ClientServer/
│       ├── MyServerRmi.java     # Starts the RMI registry and binds the remote object
│       ├── FiltreRemote.java    # Remote implementation of the filters
│       └── Filtrer.java         # Remote interface
└── ServerSocket/
    └── src/ClientServer/
        ├── MyServerSocket.java  # Socket server, one thread per connected client
        └── FiltreSocket.java    # Filter processing for the socket server
```

---

## 🚀 Getting Started

### Prerequisites
- Java JDK 8 or higher
- IntelliJ IDEA (recommended, the project contains IntelliJ modules)

### Run
1. Clone the repository:
   ```bash
   git clone https://github.com/SohailaELGHAZI/distributed-image-processing-app.git
   ```
2. Open the `projetFi` folder in IntelliJ IDEA.
3. Start the servers:
   - Run `MyServerRmi` (ServerRMI module)
   - Run `MyServerSocket` (ServerSocket module)
4. Run `MyClient` (client module).
5. Choose an image, pick a filter, and get the processed image back from the server.

> You can launch several clients at the same time to test concurrent processing.

---

## 👩‍💻 Author

**Sohaila EL GHAZI**: Full-Stack Developer

- 🌐 Portfolio: [sohailaelghazi.vercel.app](https://sohailaelghazi.vercel.app/)
- 💼 LinkedIn: [sohaila-el-ghazi](https://www.linkedin.com/in/sohaila-el-ghazi)
- 🐙 GitHub: [SohailaELGHAZI](https://github.com/SohailaELGHAZI)

*Academic project completed in a team of 2.*
