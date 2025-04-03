# DreamCrafter: An Intel® OpenVINO™ & oneAPI-Powered Smart Image Diffusion Hub

Welcome to **DreamCrafter**, a Windows application and a web app (Flask + React) that harnesses the power of [Intel® OpenVINO™](https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html) and [Intel® oneAPI](https://www.intel.com/content/www/us/en/developer/tools/oneapi/overview.html) to generate stunning images in various styles, including **Ghibli-style**, **3D Animate**, **Comic**, and more! This repository offers the perfect starting point for developers looking to create, transform, and experiment with AI-generated art. Let’s dive in!

---

## Table of Contents

1. [Overview](#overview)  
2. [Key Features](#key-features)  
3. [Installation](#installation)  
4. [Usage](#usage)  
5. [Supported Styles](#supported-styles)  
6. [Architecture & Technology](#architecture--technology)  
7. [How OpenVINO™ & OneAPI Help](#how-openvino--oneapi-help)  
8. [Expandability & Fairness](#expandability--fairness)  
9. [Roadmap](#roadmap)  
10. [Contributing](#contributing)  
11. [License](#license)  

---

## Overview

**DreamCrafter** is a smart image diffusion application that showcases how AI can be leveraged to create visually striking art. Through the synergy of **Intel® OpenVINO™** and **Intel® oneAPI**, the application offers:

- **High-performance** model inference on Intel hardware (CPUs, GPUs, VPUs).
- **Cross-platform** availability (with special focus on Windows).
- A **user-friendly** interface (web-based with **Flask + React**, plus a desktop client).

With a few clicks, you can experiment with various artistic styles—_Ghibli-inspired landscapes_, _comic-style portraits_, _3D animated characters_, and many more.

---

## Key Features

1. **Windows Desktop & Web App**: Choose between a native Windows desktop application or run the app in your browser using a **Flask + React** stack.
2. **Multiple Styles**: Generate AI art in different creative styles (Ghibli, Comic, 3D Animate, etc.).
3. **Optimized Inference**: Powered by Intel® OpenVINO™ for fast, hardware-accelerated model performance.
4. **Scalable**: Built on Intel® oneAPI for easy deployment and integration with other AI solutions.
5. **User-Friendly**: Seamless UI for both beginners and experts in AI image generation.

---

## Installation

> **Prerequisites**:
> - Python 3.8+ (for the Flask backend).
> - Node.js 14+ (for the React frontend).
> - [Intel® oneAPI Base Toolkit](https://www.intel.com/content/www/us/en/developer/tools/oneapi/base-toolkit-download.html) installed (optional but recommended).
> - [Intel® OpenVINO™ Toolkit](https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html) installed and configured.

Follow these steps to get your environment up and running:

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/your-username/DreamCrafter.git
   cd DreamCrafter
   ```

2. **Set up Python environment**:

   ```bash
   # Create a virtual environment (recommended)
   python -m venv venv
   source venv/bin/activate  # or venv\Scripts\activate on Windows

   # Install Python dependencies
   pip install -r requirements.txt
   ```

3. **Set up React frontend**:

   ```bash
   cd frontend
   npm install
   # or yarn install
   ```

4. **Configure Intel® OpenVINO™**:

   - Follow the [OpenVINO™ installation guide](https://docs.openvino.ai/latest/openvino_docs_install_guides.html).
   - Run `setupvars.bat` (on Windows) or `setupvars.sh` (on Linux) to configure the environment.

5. **Configure Intel® oneAPI** (Optional but recommended):

   - [Install oneAPI Base Toolkit](https://www.intel.com/content/www/us/en/developer/tools/oneapi/base-toolkit-download.html).
   - Source/Run the environment script so that compilers and libraries are recognized.

6. **Run the Flask server**:

   ```bash
   cd ../backend
   python app.py
   # This should start the Flask app
   ```

7. **Run the React app**:

   ```bash
   cd ../frontend
   npm run start
   # or yarn start
   ```

8. **Access the Application**:

   - Open your web browser and navigate to `http://localhost:3000`.

> **Note**: For the Windows desktop app, consult the `desktop/` folder for build instructions (using PyInstaller, Electron, or your chosen bundler).

---

## Usage

1. **Select a Style**  
   Choose from a variety of pre-defined style prompts: _Ghibli_, _3D Animate_, _Comic_, etc.

2. **Upload or Capture**  
   - Provide an initial image or start from a blank prompt.
   - Adjust parameters like _prompt strength_, _guidance scale_, _steps_, etc.

3. **Generate**  
   Click the **Generate** button and watch your AI-driven creation come to life using the optimized OpenVINO™ backend.

4. **Review & Save**  
   Once satisfied, download your artwork in the format of your choice (JPG, PNG, etc.).

---

## Supported Styles

DreamCrafter supports multiple styles to spark your creativity:

- **Ghibli-style**: Inspired by the delicate, dreamlike aesthetics of Studio Ghibli.
- **3D Animate**: Convert your prompt into a 3D-like animated scene.
- **Comic**: Bold outlines, stylized textures—perfect for that graphic novel flair.
- **Realistic Portrait**: Ultra-detailed, high-fidelity images for near photo-realistic outcomes.
- **Retro-Futuristic**: Synthwave, neon-lit, and vintage vibes.

Feel free to add or tweak styles by modifying the prompt definitions in the codebase.

---

## Architecture & Technology

```
+--------------------+          +----------------------+         +--------------------+
|   Windows Desktop  |          |       React UI       | <-----> |    Flask Server    |
|    Application     |          +----------+-----------+         +---------+----------+
|  (Optional Build)  |                     |                           |
+---------+----------+                     |                           |
          |                                |                           |
          |                                v                           |
          |                        +---------------+                    |
          |                        | AI Inference |    <---  OpenVINO  |
          |                        |   Engine     |                    |
          |                        +-------+------+                    |
          |                                |                           |
          |                                |                           |
          |                        Intel® oneAPI                       |
          |                                |                           |
          v                                v                           v
+-----------------------------------------------------------------------------------+
|                         Intel® Hardware (CPU, GPU, VPU)                           |
+-----------------------------------------------------------------------------------+
```

- **Flask** (Python) handles backend logic and model inference requests.  
- **React** offers a sleek frontend interface for the web application.  
- **Windows Desktop** (optional) for those who prefer an offline experience.  
- **Intel® OpenVINO™** accelerates AI inference, taking advantage of Intel hardware.  
- **Intel® oneAPI** ensures scalable, cross-architecture performance.

---

## How OpenVINO™ & OneAPI Help

### Performance Acceleration
- **OpenVINO™** optimizes deep learning models for Intel hardware, significantly reducing inference time.
- **oneAPI** provides a **unified programming model** that lets you write code once and deploy it across **CPUs, GPUs, and other accelerators**.

### Better Results
- By efficiently utilizing CPU vectorization, GPU parallel processing, or even specialized VPUs (Vision Processing Units), the generation process can handle **larger batch sizes** and **higher-resolution** outputs without sacrificing performance.

### Expandability
- **oneAPI** modules (like DPC++ and MKL) can be tapped into for advanced scientific computing or new AI features.
- The plugin-based architecture of **OpenVINO™** allows additional backends to be integrated as your project scales.

---

## Expandability & Fairness

1. **Expandability**  
   - The codebase is modular, making it easy to add new models or styles.  
   - The synergy between **OpenVINO™** and **oneAPI** means you can scale up from a single machine to distributed environments.

2. **Fairness**  
   - The project encourages users to train and fine-tune models responsibly, ensuring representations are inclusive.  
   - We recommend standardizing training datasets, employing bias detection, and including disclaimers about potential biases inherent in AI models.  
   - Community feedback is welcomed to continually refine fairness measures.

---

## Roadmap

- **Model Upgrades**: Add more advanced diffusion models and style variations.
- **Enhanced Desktop App**: Provide streamlined installers and auto-update capabilities.
- **Cloud Deployment**: Integrate with cloud providers to seamlessly scale large inference jobs.
- **User Profiles & Galleries**: Let users store and share their creations via curated galleries.
- **Improved Fairness Tools**: Tools for auditing and mitigating biases in generated art.

---

## Contributing

Contributions are always welcome! Whether it’s:
- Fixing bugs  
- Adding new diffusion models or style prompts  
- Enhancing the UI/UX  
- Improving documentation  

Please open an [issue](https://github.com/your-username/DreamCrafter/issues) or submit a pull request.

---

## License

This project is licensed under the [MIT License](LICENSE). See the **LICENSE** file for details.

---

**Happy Crafting with DreamCrafter!**
```
