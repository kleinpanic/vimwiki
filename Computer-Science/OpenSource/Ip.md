## IP Command (iproute2)

### Command Overview
The `ip` command, part of the `iproute2` suite, is the modern utility for managing network interfaces, routing tables, and network-related settings in Linux systems. It supersedes older utilities like `ifconfig`, `route`, and `arp`, providing a more robust and versatile approach to network configuration and management.

### Syntax
```bash
ip [options] object [command] [arguments]
```
- **options**: Modifiers that alter the command’s behavior (e.g., `-4` for IPv4, `-6` for IPv6).
- **object**: The network-related object to manage (e.g., `address`, `link`, `route`).
- **command**: The action to perform on the object (e.g., `add`, `delete`, `show`).
- **arguments**: Additional parameters or values required by the command.

### Common Objects and Their Functions
1. **Address**
   - Manages IP addresses associated with network interfaces.
   - Example:
     ```bash
     ip address show
     ```
     Displays assigned IP addresses on all interfaces.

2. **Link**
   - Manages network interfaces (e.g., enabling/disabling interfaces).
   - Example:
     ```bash
     ip link set dev eth0 up
     ```
     Brings the `eth0` network interface online.

3. **Route**
   - Configures routing tables and policies.
   - Example:
     ```bash
     ip route add default via 192.168.1.1
     ```
     Sets a default gateway for outbound traffic.

4. **Neighbor**
   - Manages ARP or NDP (Neighbor Discovery Protocol) tables.
   - Example:
     ```bash
     ip neighbor show
     ```
     Displays current neighbor cache entries (similar to `arp -a`).

### Common Use Cases
1. **Display IP Addresses**
   ```bash
   ip addr show
   ```
   Lists all IP addresses assigned to the system's interfaces.

2. **Assign a Static IP Address**
   ```bash
   sudo ip addr add 192.168.1.100/24 dev eth0
   ```
   Adds a static IP to `eth0` with a subnet mask of 255.255.255.0.

3. **Remove an IP Address**
   ```bash
   sudo ip addr del 192.168.1.100/24 dev eth0
   ```
   Deletes the specified IP address from the interface.

4. **Bring an Interface Up/Down**
   ```bash
   sudo ip link set eth0 down
   sudo ip link set eth0 up
   ```
   Disables and enables the network interface, respectively.

5. **Flush All IP Addresses**
   ```bash
   sudo ip addr flush dev eth0
   ```
   Removes all IP addresses from the specified interface.

### Advanced Options
- `-4`: Display IPv4-specific information.
- `-6`: Display IPv6-specific information.
- `-s`: Provide detailed statistics for interfaces or addresses.
- `-br`: Output data in a concise, tabular format (e.g., `ip -br addr`).

### Configuration Tips
- Use `ip route save > /etc/network/routes` to persist custom routing rules.
- Add static IP configurations in `/etc/network/interfaces` (Debian-based) or `/etc/netplan/` for systems using Netplan.

### Scripting Examples
**Automatically Restart Networking Interface:**
```bash
#!/bin/bash
interface="eth0"
sudo ip link set $interface down
sudo ip link set $interface up
```
This script restarts the specified network interface.

### Troubleshooting
- **Error: RTNETLINK answers: File exists**
  - Cause: Duplicate route or IP assignment.
  - Solution: Remove the conflicting route or IP using `ip route del` or `ip addr del`.

- **Error: Device not found**
  - Cause: The network interface name is incorrect.
  - Solution: List interfaces using:
    ```bash
    ip link show
    ```

### Related Commands
- `ifconfig`: Legacy command for interface configuration (deprecated in favor of `ip`).
- `netstat`: Used for displaying network connections (replaced by `ss`).
- `ss`: Displays socket statistics and connection information.

### External Resources
- [iproute2 Documentation](https://man7.org/linux/man-pages/man8/ip.8.html)
- [Linux IP Command Cheat Sheet](https://linuxize.com/post/linux-ip-command/)
- [Advanced IP Routing](https://wiki.linuxfoundation.org/networking/iproute2)


