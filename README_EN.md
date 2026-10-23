# TextViewer 📝

A lightweight, cross-language desktop text viewer/editor. 
The front-end is built with **PySide6** for a modern UI, and the back-end uses **Java** for high-performance file reading and smart encoding detection.

> **Note:** [Click here for the Chinese version (中文版)](./README.md)

## ✨ Features
- 🚀 **Smart Encoding Detection:** Seamlessly handles UTF-8, GBK, and other encodings without garbled characters.
- 🔍 **Search & Highlight:** Press `Ctrl + F` to find and highlight text across the entire file.
- 🌙 **Dark Mode:** One-click toggle to protect your eyes.
- 🔢 **Line Numbers:** Clear code positioning.
- 📦 **Portable:** Comes with a built-in lightweight Java runtime (JRE). No installation or environment configuration required!

## 📥 Download & Usage
1. Go to the **Releases** section on the right.
2. Download the latest `TextViewer_v..._Beta.zip`.
3. Extract the zip file and double-click `TextViewer.exe` to run.

## 🛠️ Build from Source
If you want to compile it yourself:
1. Requirements: Python 3.11 and JDK 21.
2. Compile Java backend: `javac TextReader.java`
3. Install Python dependencies: `pip install PySide6 pyinstaller`
4. Run the source code: `python main.py`
