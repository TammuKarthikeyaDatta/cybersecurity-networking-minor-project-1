# Company network diagram

```text
                    [Internet / ISP]
                           |
                  [Router + Firewall]
                           |
                     [Main Switch]
                    /      |       \
                   /       |        \
          [User Switches] [Servers] [Wi-Fi Access Points]
                |           |              |
        [45 employee PCs] [5 servers] [Employee devices]
```

The design should also account for 10 network devices, access point and switch uplinks, printers, spare ports, and future growth. Consider VLANs for employees, servers, guests, and management.
