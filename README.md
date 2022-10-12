# About

Arch Linux PKGBUILD for the Kaspersky Network Agent for KESL (Kaspersky Endpoint Security for Linux).

## Description

Interaction between the Administration Server and devices is performed by the _Network Agent_ component of Kaspersky Security Center. Network Agent must be installed on all devices on which Kaspersky Security Center is used to manage Kaspersky Lab applications.

If you plan to manage Kaspersky Endpoint Security using Kaspersky Security Center, install Kaspersky Security Center Network Agent and configure its settings.

Details: https://support.kaspersky.com/KES4Linux/11.2.0/en-US/197912.htm

## Configuration

After installing the package, start the service:
```
systemctl start klnagent64.service
```
and [perform initial configuration of the Network Agent](https://support.kaspersky.com/KES4Linux/11.2.0/en-US/197913.htm).
