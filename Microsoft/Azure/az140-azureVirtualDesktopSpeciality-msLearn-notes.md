# AZ-140: Azure Virtual Desktop Speciality - MSLearn notes

## Index

- [AZ-140: Azure Virtual Desktop Speciality - MSLearn notes](#az-140-azure-virtual-desktop-speciality---mslearn-notes)
  - [Index](#index)
  - [Plan Azure Virtual Desktop implementation](#plan-azure-virtual-desktop-implementation)
    - [Architecture](#architecture)
    - [Components](#components)
    - [Limitations](#limitations)
    - [Virtual Machine Sizing](#virtual-machine-sizing)

## Plan Azure Virtual Desktop implementation

### Architecture

![AVD architecture](../../images/msLearn/image-msLearn-azure-virtual-desktop-architecture.png)

### Components

- **Host pools** - Host pools are a collection of one or more identical virtual machines (VMs) within Azure Virtual Desktop environments. Each host pool can contain an app group that users can interact with as they would on a physical desktop. Users obtain access to host pools by being allocated to a host pool using an assigned Application Group. There are two types of host pools.
  - **Pooled:** You can configure a pooled host pool for several users to sign in and share a VM. Typically, none of those users would be a local administrator on the pooled VM. With pooled, you can use one of the recommended images that includes Windows 10 Enterprise multi-session. This operating system is exclusive to Azure Virtual Desktop. You can also use your own custom image. Pooled desktop solutions assign users to whichever session host is currently available, depending on the load-balancing algorithm. Because the users don't always return to the same session host each time they connect, they have limited ability to customize the desktop environment and don't usually have administrator access.
  - **Personal:** A personal host pool is where each user has their own dedicated VM. Those users would typically be local administrators for the VM. This enables the user to install or uninstall apps without impacting other users. Personal desktop solutions (sometimes called persistent desktops) allow users to always connect to the same specific session host. Users can typically modify their desktop experience to meet personal preferences, and save files in the desktop environment. Personal desktop solutions:
    - Let users customize their desktop environment, including user-installed applications and saving files within the desktop environment.
    - Allow assigning dedicated resources to a specific user, which can be helpful for some manufacturing or development use cases.

### Limitations

| **Azure Virtual Desktop object** | **Per Parent container object**  | **Service limit** |
|----------------------------------|----------------------------------|-------------------|
| Workspace                        | Microsoft Entra tenant           | 1300              |
| HostPool                         | Workspace                        | 400               |
| Application group                | Microsoft Entra tenant           | 500               |
| RemoteApp                        | Application group                | 500               |
| Role assignment                  | Any Azure Virtual Desktop object | 200               |
| Session host                     | HostPool                         | 10,000            |

### Virtual Machine Sizing

![Virtual Machine Sizing](../../images/msLearn/image-msLearn-virtual-machine-sizes.png)

