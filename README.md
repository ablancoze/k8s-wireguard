# wireguard-vpn
![Version 1.0.0](https://img.shields.io/badge/version-1.0.0-blue)
![Made with love](https://img.shields.io/badge/Made_with_love-pink)

<img src="./docs/img/wireguard.png" width="100">

----
- [wireguard-vpn](#wireguard-vpn)
  - [Scope](#scope)
  - [Repository structure](#repository-structure)
  - [Components](#components)
    - [List of components](#list-of-components)
    - [Resources](#resources)
    - [Useful official/unOfficial links](#Useful-officialunOfficial-links)
    - [Compatibility Matrix](#compatibility-matrix)
  - [Considerations before deploy/manage](#considerations-before-deploymanage)
  - [Stack configuration](#stack-configuration)
    - [Monitoring](#monitoring)
    - [Authentication](#authentication)
    - [Services exposed](#services-exposed)
    - [Backup](#backup)
    - [Restore](#restore)
  - [Prerequisites](#prerequisites)
  - [Usage procedures](#usage-procedures)
  - [Known issues](#known-issues)
---
## Scope

-  WireGuard® is an extremely simple yet fast and modern VPN that utilizes state-of-the-art cryptography. It aims to be faster, simpler, leaner, and more useful than IPsec, while avoiding the massive headache. It intends to be considerably more performant than OpenVPN. WireGuard is designed as a general purpose VPN for running on embedded interfaces and super computers alike, fit for many different circumstances. Initially released for the Linux kernel, it is now cross-platform (Windows, macOS, BSD, iOS, Android) and widely deployable. It is currently under heavy development, but already it might be regarded as the most secure, easiest to use, and simplest VPN solution in the industry.

## Repository structure

<details>
  <summary>Show full directory structure</summary>

```bash
.
├── CHANGELOG.md
├── CODEOWNERS
├── README.md
└── k8s
    ├── namespace.yaml
    ├── wireguard-configmap.yaml
    ├── wireguard-storage.yaml
    ├── wireguard-svc.yaml
    └── wireguard.yaml
```
</details>

## Components

### List of components

* [wireguard](https://www.wireguard.com/)

### Resources

wireguard deployment its configure to have 1 replicas, add more in case of need

| Component                        | CPU req | CPU Limit | Mem req. | Mem limit | Disk space             |
|:--------------------------------:|:-------:|:---------:|:--------:|:---------:|:-----------------------:
| wireguard-deployment             | 10m     | 100m      | 64Mi     | 128Mi     | pvc-wireguard-> 50Mi   |

### Useful official/unOfficial links

* [Wireguard](https://www.wireguard.com/)


### Compatibility Matrix

This unit has been tested in:

| Component          | Platform        | Platform version    | Tested versions    |
|:-------------------|:----------------|:--------------------|:-------------------|
| wireguard-vpn      | Kubernetes      | K8s-> v1.30.1       | 1.0.20210914       |


## Considerations before deploy/manage


* **Only one replica** is supported in this version, this implies that the only way to scale this is vertically, **no horizontal scaling** is possible.


## Stack configuration

You can configure wireguard enviroment variable on [wireguard Config File](k8s/wireguard-configmap.yaml), for example SMTP server, CICD, etc.

### Monitoring

<!-- We have differents alerts in this template which covers differents scopes. The most revelant ones are the ones bound to service avilability which are the critical ones: -->

```console
IN PROGRESS
```

### Authentication

* IN PROGRESS
  * **TODO**: 

### Services exposed

* **K8s**:
  * wireguard its expose by a [nodeport](k8s/wireguard-svc.yaml)

  ```
    kubectl -n wireguard get svc
    NAME            TYPE       CLUSTER-IP       EXTERNAL-IP   PORT(S)           AGE
    wireguard-svc   NodePort   10.152.183.134   <none>        51820:31820/UDP   70m
  ```

### Backup
> [!NOTE]    
> NO NEED

### Restore
> [!NOTE]    
> NO NEED

## Prerequisites

Follow [this guide](./docs/prerequisites.md) to verify all the prerequisites before the installation of *wireguard* in any supported container platforms.

## Usage procedures

follow this [this guide](./docs/usage.md) to check the procedures to install/update *wireguard*.

## Known issues

Check [here](./doc/known-issues.md)