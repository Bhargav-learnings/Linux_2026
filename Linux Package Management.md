# Linux Package Management

## What Is Package Management?
Package management is the process of **installing, updating, upgrading, and removing software** on a Linux system in a controlled and secure way.

Linux uses **package managers** to handle:
- Software installation
- Dependency resolution
- Version management
- Updates and security patches

---

## What Is a Package?
A package is a **compressed archive** that contains:
- Application binaries
- Configuration files
- Dependency information
- Metadata (version, description)

---

## Common Package Managers

### RPM-Based Systems (RHEL, CentOS, Amazon Linux)
- yum
- dnf
- rpm

---

### DEB-Based Systems (Ubuntu, Debian)
- apt
- apt-get
- dpkg

---

## Package Manager Roles

- Downloads packages from repositories
- Resolves dependencies automatically
- Installs files in correct locations
- Tracks installed packages

---

## Repository (Repo)

### What Is a Repository?
A repository is a **central storage location** that contains packages and metadata.

Types:
- Official OS repositories
- Third-party repositories
- Internal/private repositories

---

### Repository Configuration Locations
RPM-based:
- /etc/yum.repos.d/

Debian-based:
- /etc/apt/sources.list
- /etc/apt/sources.list.d/

---

## Installing Packages

### Using yum / dnf
yum install nginx  
dnf install docker

---

### Using apt
apt update  
apt install nginx

---

## Removing Packages

### yum / dnf
yum remove nginx  
dnf remove docker

---

### apt
apt remove nginx  
apt purge nginx

Difference:
- remove → removes package
- purge → removes package and config files

---

## Updating Packages

### Update All Packages
yum update  
dnf update  
apt upgrade

---

### Update OS
dnf upgrade  
apt full-upgrade

---

## Searching Packages

yum search nginx  
apt search nginx

---

## Listing Installed Packages

yum list installed  
dnf list installed  
apt list --installed

---

## Package Information

yum info nginx  
dnf info nginx  
apt show nginx

---

## RPM and DPKG (Low-Level Tools)

### rpm
- Installs RPM files directly
- Does not resolve dependencies automatically

rpm -ivh package.rpm  
rpm -qa  

---

### dpkg
- Low-level package tool for Debian systems

dpkg -i package.deb  
dpkg -l  

---

## Dependency Management

### Why Dependencies Matter
- Applications rely on shared libraries
- Missing dependency causes application failure

Package managers automatically resolve dependencies.

---

## Package Cache

### Why Cache Exists
- Improves performance
- Avoids re-downloading packages

Clear cache:
yum clean all  
dnf clean all  
apt clean

---

## Real Production Scenarios

### Package Installation Fails
Common causes:
- Repository unreachable
- Dependency conflict
- GPG key missing

Steps:
- Check repo configuration
- Check network connectivity
- Verify GPG keys

---

### Security Updates
- Regular patching is mandatory
- Use automated updates or maintenance windows

---

## Interview Summary
Linux package management allows controlled software installation and updates using tools like yum, dnf, and apt. Repositories provide package sources, dependencies are resolved automatically, and low-level tools like rpm and dpkg manage individual packages.

---

## Key Takeaways
- Package managers automate software handling
- Repositories store packages
- yum/dnf/apt resolve dependencies
- rpm and dpkg are low-level tools
- Regular updates are critical for security
