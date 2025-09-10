# [.devcontainer](/.devcontainer)

This directory contains configuration files for the development container, which provides an isolated environment for working on this project.

## Purpose

- **Isolation:** The devcontainer acts as a boundary between your host system and the project workspace. When you open the project in a devcontainer (e.g., using VS Code's "Remote - Containers" extension), you are working inside a controlled environment that only includes files and tools defined within the container.
- **Reproducibility:** All dependencies and tools required for development are managed outside the devcontainer itself, specifically in the [flake.nix](/flake.nix) file at the project root. This ensures consistent environments across different machines and contributors.

## How it works

- The devcontainer uses a prebuilt Nix-based image (see `devcontainer.json`) to provide a consistent base environment.
- Any additional configuration (such as mounting the Nix store or updating gitignore rules) is handled via the files in this directory.
- The container does **not** define the actual development toolchain or dependencies—these are managed by Nix and specified in `flake.nix`.

## Notes for Newcomers

- **Getting Started:** Open the project in a compatible editor (such as VS Code) and choose "Reopen in Container" if prompted. The environment will be set up automatically.
- **Customizing Dependencies:** To add or update development tools, edit the `flake.nix` file, not the devcontainer files.
- **Security:** The devcontainer provides some isolation, but it is not a security boundary. Do not use it to run untrusted or potentially malicious code.

For more details on the development environment and how to contribute, see the main [README.md](/README.md).

