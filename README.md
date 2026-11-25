# elderamarah-rhel-repos

**Repository for Milestone4TwoTime Linux (Enterprise Linux based)**

Maintained by [@TwoTimeMilestone4](https://github.com/TwoTimeMilestone4)  
Account: [@AmarahForsakenRBLX](https://github.com/AmarahForsakenRBLX)

---

## Overview

`elderamarah-rhel-repos` hosts additional package repositories, RPM packaging metadata, and related files for **Milestone4TwoTime Linux**.

Milestone4TwoTime Linux is an Enterprise Linux–based distribution focused on stability, long-term support, and practical daily use. This repository provides extra packages and repository configuration that complement the base EL system (AlmaLinux / Rocky Linux / RHEL-compatible).

The goal is to keep the packaging clean, rebuildable, and compatible with Enterprise Linux 9 and 10.

## Status

**Early stage**

- Repository created
- Initial structure and packaging guidelines in progress
- First packages and repository metadata forthcoming

## Repository Structure

```
.
├── SPECS/                  # RPM spec files
├── SOURCES/                # Upstream source tarballs, patches, and auxiliary files
├── RPMS/                   # Built binary RPMs (usually not committed)
├── SRPMS/                  # Source RPMs (optional)
├── comps/                  # comps.xml / modulemd files
├── keys/                   # GPG keys (public)
├── repo/                   # Repository metadata and .repo files
└── README.md
```

The structure will be expanded as packaging work progresses.

## Adding the Repository

Once the repository is published, add it to a Milestone4TwoTime Linux or compatible Enterprise Linux system:

```bash
# Download the repo file
sudo curl -o /etc/yum.repos.d/milestone4twotime.repo \
  https://raw.githubusercontent.com/AmarahForsakenRBLX/elderamarah-rhel-repos/main/repo/milestone4twotime.repo

# Import the GPG key (once published)
sudo rpm --import https://raw.githubusercontent.com/AmarahForsakenRBLX/elderamarah-rhel-repos/main/keys/RPM-GPG-KEY-milestone4twotime

# Refresh metadata
sudo dnf clean all
sudo dnf makecache
```

You can then install packages normally:

```bash
sudo dnf install <package-name>
```

## Building Packages

### Prerequisites

- Enterprise Linux 9 or 10 (or compatible: AlmaLinux, Rocky Linux, etc.)
- `rpm-build`, `rpmdevtools`, and related build tools
- Sufficient disk space for sources and build artifacts

Install basic build dependencies:

```bash
sudo dnf groupinstall "Development Tools"
sudo dnf install rpm-build rpmdevtools
```

### Local Build

```bash
# Set up the RPM build tree (once)
rpmdev-setuptree

# Place spec and sources
cp SPECS/example.spec ~/rpmbuild/SPECS/
cp SOURCES/* ~/rpmbuild/SOURCES/

# Build
rpmbuild -ba ~/rpmbuild/SPECS/example.spec
```

Built packages appear under `~/rpmbuild/RPMS/` and `~/rpmbuild/SRPMS/`.

### Notes

- Spec files should follow Fedora/EL packaging guidelines where practical.
- Prefer rebuilding from source rather than shipping pre-built binaries in the repository.
- Document any custom macros or build requirements in the individual spec files.

## Goals

- Provide useful additional packages for Milestone4TwoTime Linux
- Maintain clean, rebuildable RPMs compatible with Enterprise Linux
- Keep the repository focused and minimal
- Support both workstation and server use cases
- Ensure long-term rebuildability against future EL minor releases

## Contributing

Contributions are welcome. If you want to add or update a package:

1. Fork the repository
2. Add or update the spec file under `SPECS/`
3. Place required sources/patches under `SOURCES/`
4. Ensure the package builds cleanly on EL 9/10
5. Open a pull request with a clear description

Please follow existing packaging style and include a short changelog entry in the spec file.

## License

- Individual packages retain their original upstream licenses.
- Packaging files (spec files, patches created for this repository, repository configuration) are licensed under the **MIT License** unless otherwise noted.

See individual `SPECS/*.spec` files and any accompanying `LICENSE` files for details.

## Related Projects

- Main distribution and tooling: [@TwoTimeMilestone4](https://github.com/TwoTimeMilestone4)
- Milestone4TwoTime Linux

## Contact / Support

- GitHub Issues: [AmarahForsakenRBLX/elderamarah-rhel-repos](https://github.com/AmarahForsakenRBLX/elderamarah-rhel-repos/issues)
- Primary maintainer: [@TwoTimeMilestone4](https://github.com/TwoTimeMilestone4)

---

*The Spawn does not forgive. It rebirths.*
