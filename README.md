# Mellanox-ConnectX-3
Mellanox ConnectX-3 utils

https://network.nvidia.com/support/firmware/identification/

https://network.nvidia.com/support/firmware/firmware-downloads/

```bash
[root@ ~]# lspci | grep Mellanox
02:00.0 Ethernet controller: Mellanox Technologies MT27500 Family [ConnectX-3]
[root@ ~]#
```


```bash
# mft-4.25.1-11-x86_64-rpm.tgz

tar xzvf mft-4.25.1-11-x86_64-rpm.tgz
cd mft-4.25.1-11-x86_64-rpm

[root@~ mft-4.25.1-11-x86_64-rpm]# ./install.sh
-I- Removing all installed mft packages: mft  kernel-mft
-I- Building the MFT kernel binary RPM...
-I- Installing the MFT RPMs...
Verifying...                          ################################# [100%]
Preparing...                          ################################# [100%]
Updating / installing...
   1:kernel-mft-4.25.1-5.14.0_612.el9.################################# [100%]
Verifying...                          ################################# [100%]
Preparing...                          ################################# [100%]
Updating / installing...
   1:mft-4.25.1-11                    ################################# [100%]
-I- In order to start mst, please run "mst start".
[root@~ mft-4.25.1-11-x86_64-rpm]#
```

```bash
[root@ ~]# mst start
Starting MST (Mellanox Software Tools) driver set
Loading MST PCI module - Success
Loading MST PCI configuration module - Success
Create devices
[root@ ~]#
```


```bash
[root@ ~]# mlxconfig -d /dev/mst/mt4099_pciconf0 set SRIOV_EN=1 NUM_OF_VFS=8
[root@ ~]#
```

```bash
[root@ ~]# mlxconfig -d /dev/mst/mt4099_pciconf0 query

Device #1:
----------

Device type:    ConnectX3
Device:         /dev/mst/mt4099_pciconf0

Configurations:                                      Next Boot
        SRIOV_EN                                    True(1)
        NUM_OF_VFS                                  8
        LINK_TYPE_P1                                ETH(2)
        LINK_TYPE_P2                                ETH(2)
        LOG_BAR_SIZE                                3
        BOOT_PKEY_P1                                0
        BOOT_PKEY_P2                                0
        BOOT_OPTION_ROM_EN_P1                       True(1)
        BOOT_VLAN_EN_P1                             False(0)
        BOOT_RETRY_CNT_P1                           0
        LEGACY_BOOT_PROTOCOL_P1                     PXE(1)
        BOOT_VLAN_P1                                1
        BOOT_OPTION_ROM_EN_P2                       True(1)
        BOOT_VLAN_EN_P2                             False(0)
        BOOT_RETRY_CNT_P2                           0
        LEGACY_BOOT_PROTOCOL_P2                     PXE(1)
        BOOT_VLAN_P2                                1
        IP_VER_P1                                   IPv4(0)
        IP_VER_P2                                   IPv4(0)
        CQ_TIMESTAMP                                True(1)
[root@ ~]#
```

```bash
[root@~]# mlxfwmanager --query
Querying Mellanox devices firmware ...

Device #1:
----------

  Device Type:      ConnectX3
  Part Number:      MCX354A-FCB_A2-A5
  Description:      ConnectX-3 VPI adapter card; dual-port QSFP; FDR IB (56Gb/s) and 40GigE; PCIe3.0 x8 8GT/s; RoHS R6
  PSID:             MT_1090120019
  PCI Device Name:  0000:02:00.0
  Port1 MAC:        248a0723bd75
  Port2 MAC:        248a0723bd76
  Versions:         Current        Available
     FW             2.42.5000      N/A
     PXE            3.4.0752       N/A

  Status:           No matching image found

[root@~]#
```


```bash
dnf install libtool automake autoconf kernel-rpm-macros
```

```
