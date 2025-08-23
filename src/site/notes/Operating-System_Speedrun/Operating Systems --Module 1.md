---
{"dg-publish":true,"permalink":"/operating-system-speedrun/operating-systems-module-1/","title":"Introduction to Operating Systems","tags":["Semester-5"],"created":"2025-03-06T18:33:28.729+05:30"}
---


---

# Module 1

### **Unit 1: Introduction to Operating Systems**

#### **1. Generations and Evolution of Operating Systems**

- **First Generation (1940s-1950s)**: Early computers had no operating systems. Programs were manually input using punch cards.
- **Second Generation (1950s-1960s)**: Introduction of batch systems where jobs were collected and processed in batches.
- **Third Generation (1960s-1980s)**: Multiprogramming systems emerged, allowing multiple jobs to reside in memory and the CPU to be shared among them.
- **Fourth Generation (1980s-present)**: Personal computers and distributed systems became common, with advancements in networking, graphical user interfaces (GUIs), and multitasking.
---
#### **2. Types of Operating Systems**

- **Batch Operating Systems**: Execute jobs in batches without user interaction (e.g., early IBM systems).
- **Time-Sharing Systems**: Multiple users can interact with the computer simultaneously, sharing CPU time (e.g., UNIX).
- **Distributed Operating Systems**: Manage a group of independent computers and make them appear as a single system (e.g., Amoeba).
- **Real-Time Operating Systems (RTOS)**: Designed for systems requiring precise timing and reliability (e.g., embedded systems in medical devices).
- **Network Operating Systems**: Provide features for networking and manage data, users, and applications across a network (e.g., Novell NetWare).
- **Mobile Operating Systems**: Designed specifically for mobile devices (e.g., Android, iOS).

---
#### **3. Operating System Services**️

![Pasted image 20240802123603.png](/img/user/Images/Pasted%20image%2020240802123603.png)

![Pasted image 20240802124125.png](/img/user/Images/Pasted%20image%2020240802124125.png)


Operating systems provide various services to both the users and the system itself. These services are crucial for managing hardware resources and providing an interface for user interactions.

1. **Program Execution**
    
    - The OS loads the program into memory, initialises the necessary resources, and begins its execution. It handles the scheduling of processes, manages the execution flow, and ensures that processes can be suspended or resumed as needed.
2. **I/O Operations**
    
    - Operating systems manage input and output devices, such as keyboards, monitors, printers, and disk drives. This involves:
        - **Device Communication**: OS sends and receives data from devices.
        - **Buffering**: Temporarily storing data while it is being transferred between devices or between a device and memory.
        - **Caching**: Storing frequently used data in faster storage (cache) for quick access.
        - **Spooling**: Storing data for devices like printers that cannot handle interleaved data streams.
3. **File System Manipulation**
    
    - OS provides services for file creation, deletion, reading, writing, and permissions management. Key aspects include:
        - **File Attributes**: OS stores metadata about files, such as size, type, and permissions.
        - **Directory Structure**: Organises files in a hierarchical structure, allowing efficient navigation and management.
        - **File Access Methods**: Sequential and direct (or random) access, depending on the file type and application needs.
4. **Communication**
    
    - OS manages communication between processes, either on the same system or across different systems. This can include:
        - **Inter-process Communication (IPC)**: Mechanisms like pipes, shared memory, message queues, and sockets that allow processes to exchange data.
        - **Network Communication**: Protocols and services for data exchange over networks, including TCP/IP stack management.
5. **Error Detection and Handling**
    
    - OS continuously monitors the system for errors, such as hardware failures, software bugs, and resource allocation issues. It provides mechanisms for:
        - **Error Logging**: Recording error events for analysis and debugging.
        - **Error Handling**: Taking corrective actions, such as terminating a process, retrying operations, or notifying the user or administrator.
6. **Resource Allocation**
    
    - OS manages hardware resources like CPU, memory, disk space, and peripheral devices. It allocates resources to processes and ensures fair and efficient use, preventing conflicts and ensuring system stability.
7. **Protection and Security**
    
    - OS provides mechanisms to protect data and resources from unauthorised access. This includes:
        - **User Authentication**: Ensuring that only authorised users can access the system.
        - **Access Control**: Defining permissions for users and groups to access files and resources.
        - **Data Encryption**: Protecting data during transmission and storage.

---
#### 4. System Calls

- **Definition:** Imagine a computer program as a chef in a kitchen, needing ingredients and tools to prepare a meal. The operating system is like the restaurant manager, responsible for providing these essentials. But the chef can't just wander into the pantry or grab any tool they want. They need to communicate with the manager through specific requests, called **system calls**.

	System calls are essentially structured messages sent by user programs to the operating system kernel, requesting a specific service or action.  Think of them as the "commands" a program uses to interact with the OS and its underlying hardware. These services can range from simple tasks like reading data from a file (`open()`) or creating a new process (`fork()`) to more complex operations like accessing network resources (`socket()`) or managing memory allocation (`malloc()`).


	Let's look at an example: imagine you're writing a program that needs to display text on the screen. Your program can't directly control the display hardware. Instead, it uses a system call called `write()` to tell the operating system "I want to write this text to the console."  The OS kernel then handles the intricate details of sending those characters to the appropriate display drivers and ultimately rendering them on your screen.

	By providing a well-defined interface through system calls, the OS ensures that programs interact with it in a controlled and predictable manner. This promotes stability, security, and efficient resource utilisation within the system.
#### **Types of System Calls**

1. **Process Control**
    
    - **Examples**: `fork()`, `exec()`, `exit()`, `wait()`
    - **Functions**: Create and terminate processes, load and execute programs, and manage process synchronisation.
2. **File Management**
    
    - **Examples**: `open()`, `read()`, `write()`, `close()`, `delete()`
    - **Functions**: Handle file creation, deletion, reading, writing, and closing. Also, manage file attributes and metadata.
3. **Device Management**
    
    - **Examples**: `ioctl()`, `read()`, `write()`
    - **Functions**: Control device-specific operations, such as setting device parameters, and managing I/O operations for devices like disk drives and printers.
4. **Information Maintenance**
    
    - **Examples**: `getpid()`, `alarm()`, `sleep()`, `time()`
    - **Functions**: Provide information about the system and processes, set timers and alarms, and manage system time.
5. **Communication**
    
    - **Examples**: `pipe()`, `shmget()`, `msgsnd()`, `msgrcv()`, `socket()`
    - **Functions**: Facilitate communication between processes, either within the same system or across networked systems. This includes shared memory, message passing, and socket communication for network connections.

#### **System Call Mechanism**

- **Interface**: System calls provide a programming interface that abstracts the underlying hardware complexities. They are often provided as part of the standard library in programming languages (e.g., C standard library).
- **Execution**: When a system call is made, control is transferred from the user mode to kernel mode, where the OS executes the requested service. This transition is crucial for security, as it prevents user programs from directly accessing hardware and critical system resources.
- **Return Values**: System calls typically return values indicating success or failure, along with additional information (e.g., error codes).

	==System calls act as a bridge between the software world your programs live in and the underlying hardware==. Imagine you're writing a program to create a file. You don't need to know the intricate details of how the hard drive works or the specific commands to format a new file on it.  Instead, you use a system call like "open" provided by your operating system (OS). This system call acts as a request to the OS, saying "Hey, I want to create a new file."

	The magic happens behind the scenes. When you make a system call, your program temporarily hands over control to the OS kernel – think of it like the central manager of your computer. The kernel, with its deep understanding of hardware, then carries out the requested task, such as allocating space on the hard drive and setting up the new file structure.

	==Once the operation is complete, the kernel sends a signal back to your program==, indicating success or failure. This signal might include an error code if something went wrong, for example, if there wasn't enough free space on the hard drive. 


	Think of it like ordering food at a restaurant. You tell the waiter (system call) what you want, they relay the message to the kitchen (kernel), and then they bring your meal back with a bill (return value) indicating how much it cost.

#### **Examples of Common System Calls**

1. **`fork()`**: Creates a new process by duplicating the calling process. The new process is called the child process.
2. **`exec()`**: Replaces the current process image with a new process image, effectively running a new program.
3. **`open()` and `close()`**: Open and close files, returning a file descriptor used for subsequent operations.
4. **`read()` and `write()`**: Read from and write to files or devices.
5. **`ioctl()`**: Performs device-specific operations that are not covered by standard system calls.
6. **`pipe()`**: Creates a unidirectional data channel that can be used for IPC.
7. **`shmget()` and `shmat()`**: Allocate and attach shared memory segments for IPC.

---
#### **5. Structure of an Operating System**

- **Monolithic Systems**: The entire OS runs as a single program in kernel mode. It has direct access to hardware and provides rich and powerful system calls (e.g., early UNIX).
- **Layered Systems**: OS is divided into layers, with each layer only interacting with its immediate lower and upper layers (e.g., THE Operating System).
- **Microkernel Systems**: Only the most essential functions are kept in the kernel, with other services running in user space (e.g., Mach).
- **Modules**: A modular structure where the OS is divided into modules that communicate with each other (e.g., modern Linux).

### A bit in depth about the structure of an OS.

![Pasted image 20241123201644.png](/img/user/media/Pasted%20image%2020241123201644.png)


| Category                       | Description                                                                                                                                                                                                                                                                                                                                                                |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **User Interface (CLI / GUI)** |                                                                                                                                                                                                                                                                                                                                                                            |
| **System Utilities**           | * **File Management Tools**: Copying, moving, and deleting files.  <br>* **Disk Management Tools**: Formatting disks, checking disk integrity, and partitioning.  <br>* **System Monitoring Tools**: Programs that monitor system performance and resource usage.  <br>* **Backup and Recovery Tools**: Utilities for backing up data and recovering from system failures. |
| **System Libraries**           | * **File Management Tools**: Utilities for copying, moving, and deleting files.  <br>* **Disk Management Tools**: Utilities for formatting disks, checking disk integrity, and partitioning.  <br>* **Networking**: Managing network communication and protocols.  <br>* **Utility Functions**: Providing mathematical calculations, data manipulation, etc.               |
| **Middleware**                 | * **Database Middleware**: Facilitates interaction between applications and databases.  <br>* **Message-Oriented Middleware (MOM)**: Enables communication between distributed systems.  <br>* **Web Middleware**: Provides services for web applications, such as web servers and application servers.                                                                    |
| **Device Drivers**             |                                                                                                                                                                                                                                                                                                                                                                            |
| **Kernel**                     | * Process Management  <br>* Memory Management  <br>* File System Management  <br>* Device Management  <br>* Security and Access Control                                                                                                                                                                                                                                    |
| **Bootloader**                 |                                                                                                                                                                                                                                                                                                                                                                            |
| **Hardware**                   |                                                                                                                                                                                                                                                                                                                                                                            |

### 1. Kernel

==The kernel is the core component of an operating system==. It acts as a bridge between applications and the hardware. The kernel is responsible for:

- **Process Management**: Handling the creation, scheduling, and termination of processes.
- **Memory Management**: Managing the allocation and deallocation of memory space to processes.
- **File System Management**: Managing files on various storage devices.
- **Device Management**: Handling communication with hardware devices via device drivers.
- **Security and Access Control**: Ensuring that unauthorised access to data and resources is prevented.

### 2. User Interface

The user interface is what allows users to interact with the computer. There are two main types of user interfaces:

- **Command-Line Interface (CLI)**: Users interact with the OS by typing commands into a console or terminal.
- **Graphical User Interface (GUI)**: Users interact with the OS through graphical elements like windows, icons, and menus.

### 3. System Libraries

System libraries provide a set of standard functions and routines that programs can use to perform common tasks without needing to interact directly with the kernel. These libraries facilitate:

- **Standard Input/Output Operations**: Handling input from keyboards and output to displays.
- **File Manipulation**: Creating, reading, and writing files.
- **Networking**: Managing network communication and protocols.
- **Utility Functions**: Providing mathematical calculations, data manipulation, etc.

### 4. System Utilities

System utilities are programs that perform system maintenance and configuration tasks. These include:

- **File Management Tools**: Utilities for copying, moving, and deleting files.
- **Disk Management Tools**: Utilities for formatting disks, checking disk integrity, and partitioning.
- **System Monitoring Tools**: Programs that monitor system performance and resource usage.
- **Backup and Recovery Tools**: Utilities for backing up data and recovering from system failures.

### 5. Device Drivers

Device drivers are specialized programs that allow the OS to communicate with hardware devices. Each hardware component (e.g., printers, graphics cards, network adapters) requires a driver to function correctly. Drivers translate general OS commands into specific instructions for the hardware.

### 6. Shell

The shell is a command interpreter that provides a user interface for access to the services of the operating system. In UNIX and Linux systems, the shell can be either a command-line interface (like Bash or Zsh) or a graphical interface.

### 7. Bootloader

The bootloader is a small program that loads the operating system into the computer's main memory (RAM) when the system is powered on. It is the first software that runs when a computer starts and is responsible for initializing the system hardware and starting the kernel.

### 8. Middleware

Middleware is software that lies between the OS and the applications, facilitating communication and data management. It includes:

- **Database Middleware**: Facilitates interaction between applications and databases.
- **Message-Oriented Middleware (MOM)**: Enables communication between distributed systems.
- **Web Middleware**: Provides services for web applications, such as web servers and application servers.

### 9. System Call Interface

The system call interface provides the means for user programs to communicate with the kernel. System calls are functions provided by the OS that programs can call to request services such as process creation, file operations, and communication.

### 10. Virtual Machines

Some modern operating systems support virtualization, allowing multiple operating systems to run on a single physical machine. The OS can manage these virtual environments, each with its own isolated resources


---

#### **6. Virtual Machine Concept**

- **Definition**: A virtual machine (VM) is an emulation of a computer system. It allows multiple operating systems to run on a single physical machine by abstracting the hardware layer.
- **Types**:
    - **System VMs**: Provide a complete system platform, supporting the execution of a complete operating system (e.g., VMware, VirtualBox).
    - **Process VMs**: Designed to run a single program, providing a platform-independent programming environment (e.g., Java Virtual Machine).

### How Virtual Machines Work

#### 1. Hypervisor

The core technology behind virtual machines is the hypervisor, also known as the virtual machine monitor (VMM). The hypervisor manages the creation, execution, and termination of VMs. There are two types of hypervisors:

- **Type 1 (Bare-Metal) Hypervisor**: Runs directly on the host's hardware to control the hardware and manage guest operating systems. Examples include VMware ESXi and Microsoft Hyper-V.
- **Type 2 (Hosted) Hypervisor**: Runs on a host operating system to provide virtualization services. Examples include VMware Workstation and Oracle VirtualBox.

#### 2. Virtual Machine Components

Each virtual machine consists of the following components:

- **Virtual CPU (vCPU)**: A portion of the host's CPU resources allocated to the VM.
- **Virtual Memory**: A portion of the host's RAM allocated to the VM.
- **Virtual Storage**: Emulated storage devices such as virtual hard drives (VHDs) stored as files on the host system.
- **Virtual Network Interface**: Emulated network adapters that allow the VM to connect to networks.
- **Virtual Devices**: Emulated hardware devices like CD/DVD drives, USB devices, and more.

#### 3. VM Lifecycle

The lifecycle of a VM includes the following stages:

- **Creation**: A new VM is created with specified resources (CPU, memory, storage, etc.).
- **Boot**: The VM is started, and the guest OS begins to boot up.
- **Execution**: The VM runs applications just like a physical computer.
- **Pause/Resume**: The VM can be paused (suspended) and later resumed, saving and restoring its state.
- **Snapshot**: The VM's state can be captured at a specific point in time and restored later.
- **Migration**: The VM can be moved from one host to another without shutting it down (live migration).
- **Termination**: The VM is powered off and its resources are released.

#### 4. Resource Allocation and Management

The hypervisor manages the allocation of host resources (CPU, memory, storage, network) to the VMs. It ensures that each VM gets its fair share of resources while maintaining isolation between VMs to prevent them from interfering with each other.

#### 5. Isolation and Security

VMs are isolated from each other and from the host system. This isolation ensures that processes running inside one VM cannot affect those in another VM or the host. It enhances security by containing potential threats within individual VMs.

### Advantages of Virtual Machines

1. **Resource Optimization**: VMs allow multiple operating systems to run on a single physical machine, optimizing hardware usage.
2. **Isolation**: VMs are isolated from each other, improving security and stability.
3. **Scalability**: Easy to create, modify, and delete VMs based on resource needs.
4. **Flexibility**: VMs can run different operating systems and software configurations on the same physical hardware.
5. **Disaster Recovery**: VMs can be easily backed up, restored, and migrated, aiding in disaster recovery scenarios.

### Example of VM Usage

- **Development and Testing**: Developers can create multiple VMs with different operating systems and configurations to test software applications in varied environments.
- **Server Consolidation**: Organizations can consolidate multiple physical servers into VMs running on fewer physical machines, reducing hardware and maintenance costs.
- **Cloud Computing**: Cloud service providers offer VMs as a service (e.g., AWS EC2, Microsoft Azure VMs), allowing customers to run applications without managing physical servers.

### Diagram
```
+--------------------------------------------------+
|                  Host Machine                    |
|                                                  |
| +----------------------------------------------+ |
| |               Hypervisor/VMM                 | |
| |                                              | |
| | +--------+   +--------+   +--------+         | |
| | |  VM 1  |   |  VM 2  |   |  VM 3  |         | |
| | |--------|   |--------|   |--------|         | |
| | | vCPU   |   | vCPU   |   | vCPU   |         | |
| | | vRAM   |   | vRAM   |   | vRAM   |         | |
| | | vDisk  |   | vDisk  |   | vDisk  |         | |
| | | vNIC   |   | vNIC   |   | vNIC   |         | |
| | +--------+   +--------+   +--------+         | |
| +----------------------------------------------+ |
+--------------------------------------------------+

```
---

#### **7. Case Study: UNIX and Windows Operating Systems**

```
+-----------------+------------------------+------------------------+
|     Feature     |       Unix/Linux       |        Windows         |
+-----------------+------------------------+------------------------+
| Kernel          | Monolithic             | Hybrid                 |
| User Interface  | CLI (Shell), GUI       | GUI                    |
| File System     | Hierarchical (ext4,    | NTFS                   |
|                 | XFS, etc.)             |                        |
| Security        | Strong permissions,    | User Account Control,  |
|                 | multiuser              | Windows Defender       |
| Networking      | Built-in TCP/IP,       | Built-in TCP/IP,       |
|                 | robust server support  | file sharing, remote   |
|                 |                        | access                 |
| Portability     | High (C-based)         | Moderate (x86-based)   |
| Use Cases       | Servers, development,  | Desktops, enterprise,  |
|                 | embedded systems       | gaming, development    |
+-----------------+------------------------+------------------------+
```


- **UNIX**: A multiuser, multitasking operating system originally developed in the 1960s. Known for its simplicity, portability, and powerful command-line interface.
- **Windows**: A family of proprietary operating systems developed by Microsoft. It offers a graphical user interface and is widely used in personal and business environments.

### Unix Operating System

#### History

- **Origin**: Unix was developed in the late 1960s at AT&T's Bell Labs by Ken Thompson, Dennis Ritchie, and others.
- **Evolution**: Initially designed for minicomputers, Unix became popular in academic and research settings, leading to various versions and derivatives (e.g., BSD, System V).
- **Open Source Influence**: The development of Unix-like operating systems like Linux and BSD contributed to its widespread adoption.

#### Architecture

- **Kernel**: Monolithic kernel, responsible for managing system resources, hardware communication, and core system functions.
- **Shell**: Provides a command-line interface for user interaction (e.g., Bourne shell, C shell, Bash).
- **File System**: Hierarchical file system with a root directory (`/`) and a standard set of directories (`/bin`, `/usr`, `/home`, etc.).
- **Processes**: Unix uses a multitasking, multiuser approach with preemptive scheduling. Each process has a unique PID.
- **Inter-process Communication**: Supports pipes, message queues, shared memory, and semaphores.

#### Features

- **Portability**: Written in C, making it easier to port to different hardware platforms.
- **Security**: Strong permission and ownership model for files and processes.
- **Networking**: Built-in networking capabilities, making it ideal for servers and networked environments.
- **Text Processing**: Powerful text processing tools (e.g., awk, sed, grep) and scripting capabilities.

#### Use Cases

- **Servers**: Unix and Unix-like systems (e.g., Linux) dominate the server market, including web servers, database servers, and cloud infrastructure.
- **Development**: Popular in academic and research environments due to its robust development tools and open-source nature.
- **Embedded Systems**: Used in various embedded systems and devices.

---
### Windows Operating System

#### History

- **Origin**: Developed by Microsoft, with the first version released in 1985 as a graphical shell for MS-DOS.
- **Evolution**: Evolved from Windows 3.x and Windows 95/98 to NT-based systems (Windows NT, 2000, XP, Vista, 7, 8, 10, and 11).
- **Market Dominance**: Achieved widespread adoption in both consumer and enterprise markets.

#### Architecture

- **Kernel**: Hybrid kernel, combining features of monolithic and microkernel designs. The NT kernel is modular and extensible.
- **User Interface**: Graphical user interface (GUI) with the Windows Shell providing a user-friendly desktop environment.
- **File System**: Uses NTFS (New Technology File System) for modern versions, supporting features like file compression, encryption, and permissions.
- **Processes**: Multitasking, multiuser capabilities with preemptive scheduling. Each process has a unique PID.
- **Inter-process Communication**: Supports various IPC mechanisms, including pipes, mailslots, shared memory, and COM (Component Object Model).

#### Features

- **Ease of Use**: User-friendly GUI, making it accessible to non-technical users.
- **Compatibility**: Extensive software compatibility, supporting a wide range of applications and games.
- **Security**: Enhanced security features in recent versions (e.g., User Account Control, Windows Defender).
- **Networking**: Strong networking capabilities, with built-in support for TCP/IP, file sharing, and remote access.

#### Use Cases

- **Desktops**: Widely used on personal and business desktops and laptops.
- **Enterprise**: Common in corporate environments for office productivity, enterprise applications, and Active Directory-based network management.
- **Gaming**: Popular gaming platform due to extensive support for game developers and hardware compatibility.
- **Development**: Used for developing applications for Windows environments, including desktop, mobile, and web applications.

### Comparison

#### Architecture

- **Kernel**: Unix has a monolithic kernel, while Windows uses a hybrid kernel.
- **User Interface**: Unix primarily relies on the command-line interface, though GUIs like GNOME and KDE exist. Windows is primarily GUI-based.
- **File System**: Unix uses a hierarchical file system, while Windows uses NTFS with features like file permissions and encryption.

#### Features

- **Portability**: Unix is highly portable due to its C-based design. Windows is less portable but widely supported on x86 architectures.
- **Security**: Unix systems are known for robust security features and multiuser support. Windows has improved security significantly in recent versions.
- **Networking**: Both systems have strong networking capabilities, but Unix has traditionally been favored for server environments.

#### Use Cases

- **Servers**: Unix/Linux dominate the server market, while Windows Server is popular in enterprise environments.
- **Desktops**: Windows dominates the desktop market, while Unix/Linux is popular among developers and in certain specialized environments.
- **Development**: Unix/Linux is preferred for open-source development and server-side applications, while Windows is common for desktop and enterprise application development.
