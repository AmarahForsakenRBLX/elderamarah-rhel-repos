# elderamarah-rhel-repos

**Repository for Milestone4TwoTime Linux**  
*(Enterprise Linux based — for Forsaken players and the fandom)*

Maintained by [@TwoTimeMilestone4](https://github.com/TwoTimeMilestone4)  
Account: [@AmarahForsakenRBLX](https://github.com/AmarahForsakenRBLX)

---

## For the Spawn.

This is the package repository for **Milestone4TwoTime Linux** — a stability-focused Enterprise Linux distro made with Forsaken players in mind.

If you like Two Time, Azure, Elder Amarah, the Spawn cult lore, or just want a clean, long-term Linux system that doesn’t break every other week, this is for you.

The base system is Enterprise Linux (AlmaLinux/Rocky-compatible). This repo holds extra packages, themes, tools, and configs that fit the Milestone4TwoTime experience.

## What this is

- Extra packages for Milestone4TwoTime Linux
- Themes, wallpapers, and small tools aimed at the Forsaken community
- Clean RPM packaging that stays compatible with EL 9/10
- A place that doesn’t randomly explode like some rolling distros

Whether you mainly play Roblox or you’re also into Linux, the goal is the same: something stable that still feels like it belongs to the fandom.

## Status

**Just starting**

- Repo created
- Packaging work and first packages coming soon
- Themes, configs, and Forsaken-related extras planned

## Repository Structure

```
.
├── SPECS/                  # RPM spec files
├── SOURCES/                # Sources, patches, assets
├── keys/                   # GPG keys
├── repo/                   # .repo files and metadata
|── el9/                    # EL9 Repos
|── el10/                   # EL10 Repos
└── README.md

```

## Adding the Repository

Once packages are published:

```bash
# Add the repo
sudo curl -o /etc/yum.repos.d/milestone4twotime.repo \
  https://raw.githubusercontent.com/AmarahForsakenRBLX/elderamarah-rhel-repos/main/repo/milestone4twotime.repo

# Import the key (when available)
sudo rpm --import https://raw.githubusercontent.com/AmarahForsakenRBLX/elderamarah-rhel-repos/main/keys/RPM-GPG-KEY-milestone4twotime

sudo dnf clean all && sudo dnf makecache
```

Then install normally:

```bash
sudo dnf install <package-name>
```

## Building Packages

On EL 9/10 (AlmaLinux, Rocky, Milestone4TwoTime Linux, etc.):

```bash
sudo dnf groupinstall "Development Tools"
sudo dnf install rpm-build rpmdevtools

rpmdev-setuptree
# copy your .spec and sources, then:
rpmbuild -ba ~/rpmbuild/SPECS/example.spec
```

## Goals

- Give Forsaken players a stable Linux option that actually lasts
- Package useful extras (themes, tools, configs) without breaking the base system
- Keep everything rebuildable and EL-compatible
- Stay simple. No unnecessary chaos.

## Contributing

Forsaken fans and Linux people are both welcome.

If you want to add a package, theme, or small tool:

1. Fork the repo
2. Add your spec + sources
3. Make sure it builds on EL
4. Open a pull request

Even small things (wallpapers, configs, scripts) are useful.

## License

- Upstream software keeps its own license.
- Packaging files and original assets from this repo are under the **MIT License** unless noted otherwise.

## Related

- Main work: [@TwoTimeMilestone4](https://github.com/TwoTimeMilestone4)
- Milestone4TwoTime Linux

## Contact

- Issues: [this repository](https://github.com/AmarahForsakenRBLX/elderamarah-rhel-repos/issues)
- Maintainer: [@TwoTimeMilestone4](https://github.com/TwoTimeMilestone4)

---

*The Spawn does not forgive. It rebirths.*

*For Two Time. For the fandom. For something that doesn’t break.*
