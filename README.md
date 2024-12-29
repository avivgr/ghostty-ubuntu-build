Below is an example **README.md** that you can include in your **build repository** (the repo that hosts the GitHub Actions workflow). It explains:

- What the workflow does  
- How it is triggered  
- Where the generated binaries come from  
- How the release tags relate to the original Ghostty project.

Feel free to modify the wording or formatting as needed.

---

# Ghostty Debian Package Build

This repository hosts a **GitHub Actions workflow** (see [`.github/workflows/build-deb.yml`](.github/workflows/build-deb.yml)) that automatically builds **Ghostty** from source and packages it into a Debian (`.deb`) package.

## Key Points

1. **Source of Truth**  
   - The workflow checks out the source code from the official [Ghostty repository](https://github.com/ghostty-org/ghostty). 
   - The code is **not** modified or patched in any way—binaries are generated **directly** from upstream source.

2. **Fully Automated Builds**  
   - When a new release is published in _this_ repository, the workflow is triggered on GitHub Actions infrastructure.  
   - The workflow downloads the **exact same release tag** from the Ghostty repo (e.g., `v1.2.3`) and builds it in a clean Docker container using Zig `0.13.0`.

3. **Matching Release Tags**  
   - We maintain the **same version tags** here as in the official Ghostty repository.  
   - For example, if Ghostty upstream releases `v1.0.0`, this repository will also have a `v1.0.0` release.  
   - This ensures the `.deb` you download from here corresponds exactly to that Ghostty release.

4. **Built on GitHub Infrastructure**  
   - All builds run on GitHub’s hosted runners (Ubuntu-based environments).  
   - The Docker image within the workflow includes Zig and all necessary dependencies to compile Ghostty.

5. **What Is Ghostty?**  
   - Ghostty is a **terminal emulator** that differentiates itself by being **fast**, **feature-rich**, and **native**.  
   - While there are many excellent terminal emulators available, they often force you to choose between speed, features, or native UIs. Ghostty provides all three.

6. **Artifact (.deb) Availability**  
   - Once the workflow completes successfully, the resulting `.deb` artifact is attached to the GitHub Actions run.  
   - You can download it from the “Actions” tab or from the “Releases” section in this repository.

## Usage

1. **Download the `.deb`** from the latest release in this repository or the Actions artifacts.  
2. **Install** on an Ubuntu/Debian system:
   ```bash
   sudo dpkg -i ghostty-<version>-amd64.deb
   ```
3. **Run Ghostty**:
   ```bash
   ghostty
   ```

## Contributing

- If you spot any issues in the build process, or want to suggest improvements to the packaging scripts, feel free to open a PR or issue here.  
- For general Ghostty bug reports or feature requests, please visit the [upstream Ghostty repository](https://github.com/ghostty-org/ghostty).

---

**Enjoy using Ghostty**—a lightning-fast, fully featured terminal emulator with native UI components. If you have any questions, don’t hesitate to reach out via [Issues](../../issues).

