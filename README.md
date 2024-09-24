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

- ```--type [unix | inet]```: selects the socket type (either UNIX or INET).
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

## 📝 Performance analysis

Below is a comparison of different socket configurations across various workloads. 
Each mode was tested under similar conditions, and the results are presented in terms of connection time, 
data transfer rates, and overall throughput. **Each packet contains 1024 bytes**.

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

## 🔍 Key findings

The performance analysis of the **Socket performance testing tool** reveals insightful patterns based on socket types and communication modes across varying workloads. Below are the key observations derived from the test results.

### 📌 UNIX vs INET sockets

- **UNIX sockets** consistently demonstrate **lower connection times** and **faster connection closures** compared to **INET sockets** across all modes and workloads. This advantage is attributed to the absence of network protocol overhead, making UNIX sockets highly efficient for **local inter-process communication**.

- **INET sockets**, while introducing additional overhead due to network protocol processing, exhibit robust performance, especially in **medium to high workloads**. Their higher connection times are a trade-off for their capability to handle networked communications effectively.

### 📌 Communication modes performance

#### 1. **Low workload (1,000 packets)**

- **INET sockets** in **blocking-async mode** achieved the **highest throughput**.
  
- **UNIX sockets** excelled in **non-blocking-sync mode**, delivering superior throughput compared to other UNIX configurations.

#### 2. **Medium workload (100,000 packets)**

- **INET sockets** in **non-blocking-async mode** led in throughput.
  
- **UNIX sockets** maintained strong performance with both **blocking-sync** and **non-blocking-sync** modes, though slightly behind their INET counterparts in this workload.

#### 3. **High workload (10,000,000 packets)**

- **INET sockets** in **blocking-sync mode** achieved the **highest throughput**, suggesting that synchronous communication can be more effective for large-scale data transfers over networks.
  
- **UNIX sockets** showed comparable performance between **non-blocking-sync** and **blocking-sync** modes, both outperforming asynchronous configurations in this high-load scenario.

### 📌 Mode-specific insights

**Non-blocking-async mode** did **not consistently** lead in throughput across all socket types and workloads. While it performed admirably in medium workloads for **INET sockets**, it was outperformed by other modes in both low and high workloads.

### 📌 Throughput and latency

- **UNIX sockets** generally offer **higher throughput** and **lower latency** for local communications due to reduced overhead.
  
- **INET sockets**, despite higher connection times, provide **competitive throughput**, especially when leveraging appropriate communication modes tailored to the workload size.

### 📌 Connection overheads

**INET sockets** consistently exhibit **higher connection times** compared to **UNIX sockets** across all modes and workloads. This is expected due to the inherent overhead of network protocol processing involved in INET communications.

### 📊 Summary of optimal configurations

- **UNIX sockets**
  - **Non-blocking-sync** mode is optimal for **low and medium workloads**, providing the highest throughput.
  - **Blocking-sync** mode remains competitive, especially in **high workloads**.

- **INET sockets**
  - **Blocking-async** mode is best suited for **low workloads**.
  - **Non-blocking-async** mode excels in **medium workloads**.
  - **Blocking-sync** mode is preferable for **very high workloads**.

### 💡 Theoretical alignment

The observed performance aligns with socket communication theories.

- **UNIX sockets** benefit from lower latency and higher throughput in local environments due to bypassing the network stack.
  
- **INET sockets** incur additional overhead from network protocols but offer flexibility for networked applications, with performance highly dependent on the chosen communication mode and workload.

- **Non-blocking and asynchronous modes** enhance scalability and throughput by allowing the handling of multiple connections without waiting for I/O operations to complete, which is particularly beneficial in high-load scenarios.

## ⚠️ Important notes

While **non-blocking** and **asynchronous** communication modes are designed to maximize scalability and performance, particularly in environments with a large number of concurrent connections, their benefits are not always evident in tests with **single or low numbers of connections**. Here are some key points to consider when interpreting the results.

1. **Non-blocking and asynchronous modes are optimized for handling multiple concurrent connections**. In scenarios with many simultaneous clients, these modes shine by reducing idle time waiting for I/O operations. However, in tests with a single connection or limited concurrency, the **overhead of managing asynchronous events** can outweigh the benefits, which may explain why synchronous modes (especially blocking-sync) performed better in high-load scenarios.

2. **Asynchronous communication introduces complexity**, such as managing state and event handling, which incurs computational overhead. For small-scale, one-to-one communication, **blocking modes** can achieve higher throughput due to simpler execution paths and fewer context switches.

3. **Non-blocking and asynchronous modes, such as those using `epoll` or similar mechanisms, are most beneficial in large-scale applications** like servers handling thousands of connections simultaneously. The scalability offered by these modes is crucial when connections need to remain open for long periods, but data transmission is sporadic or unpredictable.

4. **Blocking modes** may be more efficient in scenarios with **continuous, large-scale data transfer** between a fixed number of connections. The overhead involved in managing asynchronous events can cause a drop in performance when the workload consists of heavy, uninterrupted data transfers over few connections.

In summary, the performance of different modes depends heavily on the specific use case. **Non-blocking and asynchronous modes** are optimal for high-concurrency, low-latency environments, while **blocking and synchronous modes** may provide better performance for large, continuous data transfers with a limited number of connections.

## 📜 License

This project is licensed under the MIT License. See the LICENSE file 📝 for details.
