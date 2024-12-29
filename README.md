# Nmap Scan Report

## Scan Summary
- **Command Used**: `nmap -A -oN nmap_scan_results.txt 192.168.1.0/24`
- **Scan Date**: December 24, 2024
- **Scan Duration**: 301.94 seconds
- **Total Hosts Scanned**: 256
- **Hosts Up**: 3

---

## Host 1: 192.168.1.1
- **Status**: Up (0.0041s latency)

### Open Ports and Services:
| Port    | State  | Service       | Version/Details                                                                                     |
|---------|--------|---------------|-----------------------------------------------------------------------------------------------------|
| 53/tcp  | Open   | Domain        | dnsmasq 2.39                                                                                       |
|         |        |               | - `id.server`: chrcnc-dns-cac-302                                                                  |
|         |        |               | - `bind.version`: dnsmasq-2.39                                                                     |
| 80/tcp  | Open   | HTTP          | uhttpd 1.0.0 (Netgear WNDR4300v2 WAP http config)                                                  |
|         |        |               | - `http-server-header`: uhttpd/1.0.0                                                               |
|         |        |               | - `http-title`: 401 Authorization                                                                  |
| 443/tcp | Open   | HTTPS         | SSL Certificate Details:                                                                           |
|         |        |               | - Subject: `commonName=OpenWrt, stateOrProvinceName=Saxony, countryName=DE`                        |
|         |        |               | - Valid From: 2001-09-09T01:46:40                                                                  |
|         |        |               | - Valid Until: 2003-09-09T01:46:40                                                                 |
| 3333/tcp| Open   | POT           | Netgear POT-(Get/Set) Demo                                                                         |
| 5555/tcp| Open   | FreeCiv       | HTTP Responses: 404 Not Found, 400 Bad Request, 501 Not Implemented                                |
| 20005/tcp| Open  | BTX?          | Unknown                                                                                           |
| 49152/tcp| Open  | UPnP          | Cisco-Linksys E4200 WAP upnpd (UPnP 1.0)                                                          |

### Additional Info:
- **Device**: Netgear WAP, broadband router
- **CPEs**: `cpe:/h:netgear:wndr4300v2`, `cpe:/h:cisco:e4200`

---

## Host 2: 192.168.1.2
- **Status**: Up (0.0046s latency)

### Open Ports and Services:
| Port    | State  | Service       | Version/Details                                             |
|---------|--------|---------------|-------------------------------------------------------------|
| 80/tcp  | Open   | HTTP          | BusyBox httpd 1.13                                          |
|         |        |               | - `http-title`: Grandstream Device Configuration            |

### Additional Info:
- **OS**: Linux
- **CPE**: `cpe:/o:linux:linux_kernel`

---

## Host 3: 192.168.1.12 (Your Device)
- **Status**: Up (0.00039s latency)

### Open Ports and Services:
| Port    | State  | Service       | Version/Details                                             |
|---------|--------|---------------|-------------------------------------------------------------|
| 53/tcp  | Open   | Domain?       | Unknown                                                     |
| 5000/tcp| Open   | RTSP          | AirTunes rtspd 775.3.1                                      |
|         |        |               | - Error in `rtsp-methods`: Script execution failed          |
| 7000/tcp| Open   | RTSP          | AirTunes rtspd 775.3.1                                      |
|         |        |               | - Error in `rtsp-methods`: Script execution failed          |

---

## Observations
- **Host 192.168.1.1**:
  - Multiple services detected (HTTP, HTTPS, DNS, UPnP).
  - SSL certificates expired (2003).
  - HTTP service requires authentication (`401 Authorization`).

- **Host 192.168.1.2**:
  - HTTP service running on BusyBox, likely for device configuration.

- **Host 192.168.1.12**:
  - AirTunes RTSP services detected with errors in response methods.

---

## Recommendations
1. **192.168.1.1**:
   - Replace expired SSL certificates.
   - Limit access to open HTTP and HTTPS ports (443, 80).
   - Disable UPnP if not required.

2. **192.168.1.2**:
   - Restrict access to the BusyBox HTTP configuration page.
   - Apply security patches to BusyBox HTTP service.

3. **192.168.1.12**:
   - Investigate RTSP service errors and secure configuration.

---

## Resources
- [Nmap Documentation](https://nmap.org/docs.html)
- [Report Incorrect Results](https://nmap.org/submit/)
