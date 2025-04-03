# DreamCrafter: An Intel® OpenVINO™ & oneAPI-Powered Smart Image Diffusion Hub
## Windows & Web AI Diffusion Platform (Anaconda + Visual Studio)

[![DreamCrafter](Media/Images/dreamcrafter-logo.png)](https://github.com/Nitin-Mane/DreamCrafter)

[![VERSION](https://img.shields.io/badge/VERSION-1.0.0-blue.svg)](https://github.com/Nitin-Mane/image/assert/DreamCrafter/tree/1.0.0)
[![DEV BRANCH](https://img.shields.io/badge/DEV%20BRANCH-1.1.0-blue.svg)](https://github.com/Nitin-Mane/image/assert/DreamCrafter/tree/1.1.0)
[![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-lightgrey.svg)](CONTRIBUTING.md)
[![Issues](https://img.shields.io/badge/Issues-Welcome-lightgrey.svg)](issues)
[![LICENSE](https://img.shields.io/badge/LICENSE-MIT-blue.svg)](LICENSE)

&nbsp;

# Table Of Contents

- [Introduction](#introduction)
- [Key Features](#key-features)
- [Architecture](#architecture)
- [Projects](#projects)
    - [Windows App (Visual Studio)](#windows-app-visual-studio)
    - [Web App (Flask + React)](#web-app-flask--react)
- [Installation](#installation)
    - [Prerequisites](#prerequisites)
    - [Anaconda Setup](#anaconda-setup)
    - [Visual Studio Setup](#visual-studio-setup)
- [Usage](#usage)
- [Supported Styles](#supported-styles)
- [Expandability & Fairness](#expandability--fairness)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
    - [Contributors](#contributors)
- [Versioning](#versioning)
- [License](#license)
- [Bugs/Issues](#bugsissues)

---

## Introduction

**DreamCrafter** is a **Windows & Web AI Diffusion Platform** leveraging [Intel® OpenVINO™](https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html) and [Intel® oneAPI](https://www.intel.com/content/www/us/en/developer/tools/oneapi/overview.html) to create generative art in various styles: **Ghibli**, **3D Animate**, **Comic**, and more. This repository provides both a **Visual Studio** project for a native Windows application and a **Flask + React** web app, offering a flexible, multi-project solution for AI-driven art generation.

---

## Key Features

- **High-Performance Inference**: Hardware-accelerated with Intel® OpenVINO™.  
- **Cross-Platform**: A Windows-native application (Visual Studio) + a web-based solution.  
- **Multiple AI Styles**: Ghibli, 3D Animate, Comic, etc.  
- **Scalable**: Built to leverage Intel® oneAPI across CPU, GPU, or VPU hardware.  
- **Easy Setup**: Anaconda environment for Python-based server modules.

---

## Architecture

```plaintext
+---------------------------+          +----------------------+         +--------------------+
| Windows App (VisualStudio)|          |       React UI       | <-----> |    Flask Server    |
|  (Native .NET/C++/C#)     |          +----------+-----------+         +---------+----------+
+-------------+-------------+                     |                           |
              |                                   |                           |
              |                                   v                           |
              |                           +---------------+                    |
              |                           | AI Inference |    <---  OpenVINO  |
              |                           |   Engine     |                    |
              |                           +-------+------+                    |
              |                                   |                           |
              |                                   |                           |
              |                           Intel® oneAPI                       |
              |                                   |                           |
              v                                   v                           v
+-------------------------------------------------------------------------------------------------+
|                              Intel® Hardware (CPU, GPU, VPU)                                    |
+-------------------------------------------------------------------------------------------------+
```

- **Windows App**: A native Windows application built with Visual Studio (C#/C++/WPF, etc.).  
- **Flask Backend**: Python-based inference server.  
- **React Frontend**: Modern UI for the web version.  
- **OpenVINO™**: Optimized model execution on Intel hardware.  
- **Intel® oneAPI**: Unified programming model for cross-architecture performance.

---

## Projects

### Windows App (Visual Studio)

- Located in the `/windows-app` directory (or similar).
- Uses a standard Visual Studio solution (`.sln`) and project (`.csproj` / `.vcxproj`).
- Communicates with the AI backend (optionally local or remote) for inference requests.

### Web App (Flask + React)

- Located in `/backend` (Flask) and `/frontend` (React).
- Flask serves inference endpoints.
- React provides a user-friendly interface for generating images on the fly.

---

## Installation

### Prerequisites

1. **Anaconda** or **Miniconda** (for Python 3.8+)
2. **Node.js 14+** (for the React frontend)
3. **Visual Studio 2019/2022** (for the Windows app)
4. **Intel® oneAPI Base Toolkit** (optional but recommended)
5. **Intel® OpenVINO™ Toolkit** (installed and configured for your system)

### Anaconda Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Nitin-Mane/DreamCrafter.git
   cd DreamCrafter
   ```

2. **Create and activate a new Anaconda environment**:
   ```bash
   conda create -n dreamcrafter_env python=3.8
   conda activate dreamcrafter_env
   ```

3. **Install Python dependencies**:
   ```bash
   cd backend
   pip install -r requirements.txt
   ```

4. **Install frontend dependencies**:
   ```bash
   cd ../frontend
   npm install
   # or yarn install
   ```

5. **Configure OpenVINO™**:
   - Follow the [OpenVINO™ installation guide](https://docs.openvino.ai/latest/openvino_docs_install_guides.html).
   - Run `setupvars.bat` (on Windows) to configure your environment (or source the equivalent script on Linux).

6. **Configure Intel® oneAPI** (Optional):
   - [Install oneAPI Base Toolkit](https://www.intel.com/content/www/us/en/developer/tools/oneapi/base-toolkit-download.html).
   - Source/Run the environment setup script to ensure compilers and libraries are recognized.

### Visual Studio Setup

1. **Open the `DreamCrafter.sln` file** in Visual Studio (found in `/windows-app/` or your chosen folder).
2. **Install any required NuGet packages** upon first load (if prompted).
3. **Configure your build** (Debug/Release) and **platform** (x64 recommended).
4. **Build & Run** the project.  
   - This should produce a Windows application that, when run, can either self-contain the inference logic or communicate with the Flask backend for AI requests.

---

## Usage

1. **Run the Web Backend**  
   - Activate your Anaconda environment:  
     ```bash
     conda activate dreamcrafter_env
     ```
   - Start Flask backend:  
     ```bash
     cd backend
     python app.py
     ```
   - Start the React frontend:  
     ```bash
     cd ../frontend
     npm start
     # or yarn start
     ```
   - Access via [http://localhost:3000](http://localhost:3000).

2. **Run the Windows App**  
   - Launch the application from Visual Studio or the compiled `.exe`.
   - Configure the backend endpoint (if needed) to point to the Flask server.  
     - For local setup, it might be `http://127.0.0.1:5000/`.  
   - Use the desktop UI to select styles, prompt text, etc.

---

## Supported Styles

- **Ghibli**: Whimsical animations reminiscent of Studio Ghibli  
- **3D Animate**: Pixar-like rendering  
- **Comic**: Bold lines, stylized color palette  
- **Realistic Portrait**: High-fidelity, photo-realistic results  
- **Retro-Futuristic**: Neon-lit, vintage sci-fi vibe  

---

## Expandability & Fairness

1. **Expandability**  
   - Modular codebase allows new AI models or style prompts to be easily integrated.  
   - Intel® oneAPI’s scalable approach supports multi-architecture deployments.

2. **Fairness**  
   - We encourage responsible and inclusive dataset usage.  
   - Community input is sought to address AI biases and improve representation.

---

## Roadmap

- **More Advanced Models**: Integration with additional diffusion or generative models.  
- **Cloud Solutions**: Containerization & orchestration (Docker, Kubernetes).  
- **Enhanced Desktop Features**: Auto-updates, usage analytics, and offline generation.  
- **User Portfolio**: Allow users to store or share generated images.

---

## Contributing

We welcome contributions via pull requests and bug reports through GitHub issues.


## License

[![LICENSE](https://img.shields.io/badge/LICENSE-MIT-blue.svg)](LICENSE)

This project is licensed under the [MIT License](LICENSE).

---

## Bugs/Issues

Please create [issues here](issues) for any bugs or feature requests. We greatly value your feedback and contributions!
```

---

### Usage Notes

1. **File Organization**  
   - Make sure your Visual Studio project is located in a clearly labeled folder (e.g., `windows-app/`) separate from your `backend/` and `frontend/` directories.
2. **Conda Environment**  
   - Using Anaconda ensures reproducibility for Python-based dependencies.  
   - The same environment can be shared or exported with `conda env export > environment.yml`.
3. **License & Badges**  
   - Update the badges (version, dev branch, etc.) to reflect your repository’s current states.  
   - Replace `YourUsername` with your actual GitHub handle.

Feel free to **modify** any part of the script to better suit your project’s structure or naming conventions. This layout highlights a **multi-project** setup combining a **native Windows app** (Visual Studio) with a **web-based** AI inference application (Flask + React) under a **single repository**.
