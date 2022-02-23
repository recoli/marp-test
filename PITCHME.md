---
marp: true
---

# <!--fit--> Introduction to PDC

2022-02-23

[Github link]

<style scoped>a { color: #eee; }</style>

<!-- This is presenter note. You can write down notes through HTML comment. -->

---

<!-- paginate: true -->

# Introduction to Dardel supercomputer
![bg 90% left](https://www.pdc.kth.se/polopoly_fs/1.1053343.1614296818!/image/3D%20marketing%201%20row%20cropped%201000pW%20300ppi.jpg)

---

# HPE/Cray EX system

### Phase 1: CPU partition

* 2.279 petaFlops (Top500 Nov 2021)
* 554 CPU nodes
* Dual AMD EPYC<sup>TM</sup> 64-core processors

### Phase 2: GPU partition

* 56 GPU nodes
* AMD EPYC<sup>TM</sup> processor with 64 cores
* four AMD Instinct<sup>TM</sup> MI250X GPUs

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

# File Systems

Lustre File System (Klemming)

* Open-source massively parallel distributed le system
* Optimized for handling data from many clients
  - Total size is 12 PB (12,000 TB)
* Home directory (25 GB, with backup)
  - /cfs/klemming/home/[u]/[username]
* Project directory
  - /cfs/klemming/projects/snic/[projectname]
* Scratch directory
  - /cfs/klemming/scratch/[u]/[username]

---

# File Systems

* Good practice
  - Minimize the number of I/O operations
  - Avoid creating too many les
  - Avoid creating directories with a large numbers of les
* Bad practice
  - Small reads
  - Opening many les
  - Seeking within a le to read a small piece of data

---

# Access Control Lists

### To view the access for a folder:
```
getfacl -a /cfs/klemming/home/u/user/test
```
### The output looks like this:
```
# file: /cfs/klemming/home/u/user/test
# owner: me
# group: users
user::rwx
group::r-x
other::---
```

---

# Access Control Lists

### To grant the access to another user ("-R" for recursive):
```
setfacl -m u:<uid>:r-x -R /cfs/klemming/home/u/user/test
```
### To remove the access for another user ("-R" for recursive):
```
setfacl -x u:<uid> -R /cfs/klemming/home/u/user/test
```

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
