# Key Debouncer Package Repository

This repository hosts the official package repositories for [Key Debouncer](https://github.com/VillageOfGamers/key-debouncer), served via GitHub Pages. Packages are available for Debian-based and RPM-based distributions, as well as the Arch User Repository.

## GPG Signing

All packages and repository metadata are signed with the maintainer's GPG key (nistp384). The public key is available at:

```
https://villageofgamers.github.io/key-debouncer-dist/debounced-archive-keyring.asc
```

**Note for RPM users:** Due to an incompatibility between RPM's PGP implementation and ECDSA-based keys, individual `.rpm` packages are not signed. However the repository metadata (`repomd.xml`) is signed and verified by `dnf` at install time, providing equivalent integrity guarantees for the repository as a whole.

## Debian, Ubuntu, and derivatives

```bash
curl -fsSL https://villageofgamers.github.io/key-debouncer-dist/debounced-archive-keyring.asc | sudo gpg --dearmor -o /etc/apt/keyrings/debounced.gpg
echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/debounced.gpg] https://villageofgamers.github.io/key-debouncer-dist/apt stable main" | sudo tee /etc/apt/sources.list.d/debounced.list
sudo apt-get update
sudo apt-get install debounced
```

For arm64 systems, replace `arch=amd64` with `arch=arm64` in the `echo` command.

## Fedora, RHEL, and derivatives

```bash
sudo rpm --import https://villageofgamers.github.io/key-debouncer-dist/debounced-archive-keyring.asc
sudo tee /etc/yum.repos.d/debounced.repo << EOF
[debounced]
name=Key Debouncer
baseurl=https://villageofgamers.github.io/key-debouncer-dist/rpm/x86_64
enabled=1
gpgcheck=0
repo_gpgcheck=1
gpgkey=https://villageofgamers.github.io/key-debouncer-dist/debounced-archive-keyring.asc
EOF
sudo dnf install debounced
```

For aarch64 systems, replace `rpm/x86_64` with `rpm/aarch64` in the `baseurl` line.

## Arch Linux (AUR)

Key Debouncer is available on the AUR as `debounced`. Install it with your AUR helper of choice:

```bash
yay -S debounced
# or with paru:
paru -S debounced
```

## Verifying the GPG Key

You can verify the signing key fingerprint against the public key hosted at this repository:

```
https://villageofgamers.github.io/key-debouncer-dist/debounced-archive-keyring.asc
```

Expected fingerprint:
```
704157E7B8EF08B065B2E43E1A488E7E9EB9479D
```
