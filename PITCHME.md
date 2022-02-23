---
marp: true
---

![bg](./assets/gradient.jpg)

# <!--fit--> Introduction to PDC

2022-02-23

[Github link]

<style scoped>a { color: #eee; }</style>

<!-- This is presenter note. You can write down notes through HTML comment. -->

---

<!-- paginate: true -->

# Introduction to Dardel supercomputer
![bg 90% left](https://www.pdc.kth.se/polopoly_fs/1.1053343.1614296818!/image/3D%20marketing%201%20row%20cropped%201000pW%20300ppi.jp
g)

---

# HPE/Cray EX system

The system will be installed in 2 phases

### Phase 1: CPU partition

### Phase 2: GPU partition

---

# Dardel CPU partition

## Processor

Each node has...

* 128 cores
* Dual AMD EPYC 2.25 Ghz 64 core

## Interconnect

* HPE Slingshot using Dragonfly topology
* 100 Gb/s first phase

---

# Compute nodes

| Nodes | RAM (GB) | Name |
| --- | --- | --- |
| 488 | 256 | Thin |
| 20 | 512 | Large |
| 8 | 1024 | Huge |
| 2 | 2048 | Giant |
| 36 | 256 | Business |
| ? | 256 | SCANIA |

Total: **554** Nodes with 128 cores

---

# How to use EasyBuild
![bg h:150 80% left](https://docs.easybuild.io/en/latest/_static/easybuild_logo_alpha.png)
### 2022-02-23

### https://docs.easybuild.io/en/latest/

---

# What modules are available

### For global installations
```
module load PDC/21.11
module load EasyBuild-production/4.5.0
```
* Builds into */pdc/software/21.11/eb/*

### For local installations
Good to evaluate prior of global installation and testing purposes
```
module load PDC/21.11
module load EasyBuild-user/4.5.0
```
* Builds into *~/easybuild_user*
* You must include ~/easybuild_user/modules in Lmod to use installed software
