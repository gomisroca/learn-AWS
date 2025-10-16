# 🔐 Deep Dive on Container Security

## 🛑 Risks in Containers

- **Confidentiality** → Data leaks between containers or to the host.
- **Access Control** → Who can start, stop, or modify containers; audit logging.
- **Resource Usage** → One container monopolizing CPU/memory.
- **Integrity** → Unauthorized modification of images or runtime.
- **Availability** → Denial of Service from misbehaving containers.

## 🖥️ System Layers

- System = User Layer + Kernel + Hardware.
- Containers add a new layer on top of the OS → share the host kernel/hardware.
- Security concern: “nosy neighbor” effect (containers seeing or affecting each other).

## 🪞 Namespaces

- **Purpose:** Isolate resources so containers think they have their own system view.
- **Created by:** `clone(2)` system call.
- **Hierarchy:** Parent can see children; children can’t see parent or siblings.

### Common Namespace Types

| Type       | Description                                    |
| ---------- | ---------------------------------------------- |
| PID        | Process isolation (own process tree)           |
| Network    | Separate network interfaces and routing tables |
| User       | Maps container users to host users             |
| Mount / FS | Separate file system mounts                    |
| IPC        | Isolated inter-process communication           |
| UTS        | Separate hostname and domain                   |
| Cgroups    | Limit CPU, memory, and I/O resources           |

## ✍️ Final Thoughts

- Containers can influence each other very easily.
- Even if process-to-process isolation is tight, it’s not a complete solution.
- Network is always a concern, especially to the outside.
- We should asses which apps we put together on a server.
