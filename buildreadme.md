# 🥏 Disc Golf Scorecard - Build & Deployment Documentation

This repository contains a native Android Disc Golf Scorecard application built with Jetpack Compose and Kotlin. This document outlines the optimized development, build, and deployment processes tailored for Windows 10 environments.

---

## 🛠 Prerequisites & Environment Setup

Before compiling, verify that your local environment variables point to your integrated Android Studio Java runtime to prevent compilation errors.

### Direct PowerShell Java Injection
If your terminal cannot locate Java, inject the path directly into your active PowerShell session before running a build:
```powershell
\$env:JAVA_HOME="C:\Program Files\Android\Android Studio\jbr"
```

### Persistent Project Java Configuration
To bypass Windows environment configurations entirely, ensure your root `local.properties` contains the direct path map (using escaped double-backslashes):
```properties
org.gradle.java.home=C:\\Program Files\\Android\\Android Studio\\jbr
```

---

## 🚀 Daily Development Workflow

Use these sequential PowerShell terminal (`Alt + F12`) commands inside Android Studio to save modifications, resolve branch syncing, and compile the final mobile package.

### 1. Synchronizing Codebase with GitHub
Always use **double quotes (`"`)** for commit text formatting to ensure safe parsing within the Windows PowerShell terminal environment.

```powershell
# Stage all local modifications
git add .

# Snapshot changes locally
git commit -m "Describe your code changes here"

# Push updates directly to the synchronized main branch
git push origin main
```

### 2. Low-Resource APK Compilation
Bypassing the graphical user interface elements saves system memory and guarantees build stability.

```powershell
# Execute the automated Gradle build wrapper task
.\gradlew.bat assembleDebug
```

### 3. Locating and Deploying the Package
Once the terminal outputs a green `BUILD SUCCESSFUL` completion alert, run this command to open the build target folder on your Windows 10 desktop:

```powershell
explorer .\app\build\outputs\apk\debug\
```

* **Target File:** Locate the **`app-debug.apk`** file inside the directory.
* **Installation:** Transfer this file to your physical Android device via a USB data cable or secure cloud storage, then open the file on your device to execute the application installation layer.

---

## ⚠️ Troubleshooting Common Pitfalls

* **Unrelated Histories Error:** If pulling from the cloud fails due to conflicting initial structures, resolve it via the terminal using:
  ```powershell
  git pull origin main --allow-unrelated-histories
  ```
* **GitIgnore Conflicts:** If `.gitignore` clashes during synchronization, prioritize the cloud version using:
  ```powershell
  git checkout --theirs .gitignore
  git add .gitignore
  git commit -m "Resolved .gitignore merge conflict"
  ```
