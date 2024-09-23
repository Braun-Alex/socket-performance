# 🚀 Socket performance testing tool 🚀

![License](https://img.shields.io/badge/license-MIT-blue.svg) ![C](https://img.shields.io/badge/language-C-blue.svg)

## 🌟 Project overview

Welcome to the **Socket performance testing tool** 🎉! This project comprises a **client** and **server** application developed in C, designed to evaluate the performance of different socket communication modes. 🧑‍💻👩‍💻

### 🎯 Key objectives

- **Measure** the performance of various socket types and modes.
- **Compare** blocking, non-blocking, synchronous and asynchronous communication.
- **Provide** insights into the efficiency and scalability of each mode.

## 🛠️ Features

- **Dual socket support**: UNIX and INET (TCP/IP) sockets.
- **Multiple communication modes**:
  - blocking and synchronous
  - non-blocking and synchronous
  - blocking and asynchronous
  - non-blocking and asynchronous
- **Comprehensive reporting**: detailed performance metrics.
- **User-friendly**: easy setup and configuration using CMake.

## ⚙️ Installation and running

### 🔧 Prerequisites

Ensure you have the following installed on your system:

- GCC compiler (`sudo apt install gcc`)
- CMake (`sudo apt install cmake`)
- Git (`sudo apt install git`)

### Step 1: clone the repository
Clone the project from GitHub:
```bash
git clone https://github.com/Braun-Alex/socket-performance.git
cd socket-performance
```

### Step 2: build the project
```bash
mkdir build
cd build
cmake ..
make
```

### Step 3: run the server
```bash
./server --type [unix | inet] --mode [blocking-sync | nonblocking-sync | blocking-async | nonblocking-async] --port [PORT]
```

### Step 4: run the client
```bash
./client --type [unix | inet] --mode [blocking-sync | nonblocking-sync | blocking-async | nonblocking-async] --address [ADDRESS] --port [PORT] --workload [NUMBER_OF_PACKETS]
```

- ```--type [unix|inet]```: selects the socket type (either UNIX or INET).
- ```--mode [blocking-sync | nonblocking-sync | blocking-async | nonblocking-async]```: chooses the socket operation mode.
- ```--port [PORT]```: specifies the port number for INET sockets.
- ```--address [ADDRESS]```: IP address of the server (for INET sockets).
- ```--workload [NUMBER_OF_PACKETS]```: number of packets to send in the workload.

## 💡 Examples

The tool supports various modes. Below are example commands for each configuration.

### 1. UNIX socket, blocking-sync mode 🐧🔒🕰️

**Server:**
```bash
./server --type unix --mode blocking-sync
```

**Client:**
```bash
./client --type unix --mode blocking-sync --workload 30000
```

### 2. UNIX socket, nonblocking-sync mode 🐧🔓🕰️

**Server:**
```bash
./server --type unix --mode nonblocking-sync
```

**Client:**
```bash
./client --type unix --mode nonblocking-sync --workload 30000
```

### 3. INET socket, blocking-sync mode 🌐🔒🕰️

**Server:**
```bash
./server --type inet --mode blocking-sync --port 8080
```

**Client:**
```bash
./client --type inet --mode blocking-sync --address 127.0.0.1 --port 8080 --workload 30000
```

### 4. INET socket, nonblocking-sync mode 🌐🔓🕰️

**Server:**
```bash
./server --type inet --mode nonblocking-sync --port 8080
```

**Client:**
```bash
./client --type inet --mode nonblocking-sync --address 127.0.0.1 --port 8080 --workload 30000
```

### 5. UNIX socket, blocking-async mode 🐧🔒⚡️

**Server:**
```bash
./server --type unix --mode blocking-async
```

**Client:**
```bash
./client --type unix --mode blocking-async --workload 30000
```

### 6. UNIX socket, nonblocking-async mode 🐧🔓⚡️

**Server:**
```bash
./server --type unix --mode nonblocking-async
```

**Client:**
```bash
./client --type unix --mode nonblocking-async --workload 30000
```

### 7. INET socket, blocking-async mode 🌐🔒⚡️

**Server:**
```bash
./server --type inet --mode blocking-async --port 8080
```

**Client:**
```bash
./client --type inet --mode blocking-async --address 127.0.0.1 --port 8080 --workload 30000
```

### 8. INET socket, nonblocking-async mode 🌐🔓⚡️

**Server:**
```bash
./server --type inet --mode nonblocking-async --port 8080
```

**Client:**
```bash
./client --type inet --mode nonblocking-async --address 127.0.0.1 --port 8080 --workload 30000
```

### 🛑 Stopping the server

Press Ctrl+C in the server terminal to terminate the server gracefully. 🛑

## 📝 Report: performance analysis

Below is a comparison of different socket configurations across various workloads. 
Each mode was tested under similar conditions, and the results are presented in terms of connection time, 
data transfer rates, and overall throughput. Each packet contains 1024 bytes.

### 1. Workload: 1'000 packets

| Mode | Socket type | Connection time (ms) | Data transfer time (ms) | Throughput (packets/sec) | Throughput (MB/sec) | Connection close time (ms) |
|------|--------------------|-----|-----|-----|-----|-----|
| UNIX | Blocking-sync      | 0.047 | 7.179 | 139292.76 | 136.03 | 0.017 |
| UNIX | Non-blocking-sync  | 0.079 | 6.726 | 148686.15 | 145.2 | 0.013 |
| UNIX | Blocking-async     | 0.084 | 7.345 | 136143.44 | 132.95 | 0.013 |
| UNIX | Non-blocking-async | 0.077 | 6.961 | 143661.73 | 140.29 | 0.011 |
| INET | Blocking-sync      | 0.201 | 6.791 | 147246.69 | 143.8 | 0.036 |
| INET | Non-blocking-sync  | 0.208 | 5.547 | 180261.44 | 176.04 | 0.018 |
| INET | Blocking-async     | 0.14 | 4.619 | 216515.26 | 211.44 | 0.039 |
| INET | Non-blocking-async | 0.208 | 6.799 | 147078.42 | 143.63 | 0.041 |

### 2. Workload: 100'000 packets

| Mode | Socket type | Connection time (ms) | Data transfer time (ms) | Throughput (packets/sec) | Throughput (MB/sec) | Connection close time (ms) |
|------|--------------------|-----|-----|-----|-----|-----|
| UNIX | Blocking-sync      | 0.034 | 262.888 | 380389.9 | 371.47 | 0.011 |
| UNIX | Non-blocking-sync  | 0.034 | 262.839 | 374758.2 | 365.97 | 0.012 |
| UNIX | Blocking-async     | 0.058 | 283.104 | 353227.39 | 344.95 | 0.008 |
| UNIX | Non-blocking-async | 0.064 | 280.685 | 356271.28 | 347.92 | 0.008 |
| INET | Blocking-sync      | 0.223 | 211.968 | 471769.09 | 460.71 | 0.02 |
| INET | Non-blocking-sync  | 0.166 | 216.33 | 462257.59 | 451.42 | 0.02 |
| INET | Blocking-async     | 0.214 | 213.127 | 469204.62 | 458.21 | 0.016 |
| INET | Non-blocking-async | 0.23 | 204.917 | 488003.35 | 476.57 | 0.025 |

### 3. Workload: 10'000'000 packets

| Mode | Socket type | Connection time (ms) | Data transfer time (ms) | Throughput (packets/sec) | Throughput (MB/sec) | Connection close time (ms) |
|------|--------------------|-----|-----|-----|-----|-----|
| UNIX | Blocking-sync      | 0.055 | 23774.262 | 420622.94 | 66.19 | 0.013 |
| UNIX | Non-blocking-sync  | 0.051 | 23721.52 | 421558.14 | 66.34 | 0.012 |
| UNIX | Blocking-async     | 0.046 | 25805.172 | 387519.22 | 60.98 | 0.008 |
| UNIX | Non-blocking-async | 0.058 | 26050.036 | 383876.63 | 60.41 | 0.008 |
| INET | Blocking-sync      | 0.243 | 19118.658 | 523049.27 | 82.31 | 0.028 |
| INET | Non-blocking-sync  | 0.21 | 19220.285 | 520283.64 | 81.87 | 0.02 |
| INET | Blocking-async     | 0.201 | 20053.085 | 498676.39 | 78.47 | 0.012 |
| INET | Non-blocking-async | 0.223 | 20181.067 | 495513.93 | 77.98 | 0.017 |

## 📜 License

This project is licensed under the MIT License. See the LICENSE file 📝 for details.
