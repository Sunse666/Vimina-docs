# Vimina vs Anjian Jingling

This document provides a detailed comparison between Vimina and Anjian Jingling (按键精灵), two Windows automation tools, analyzing their features, pros and cons, and suitable use cases.

## Overview

### Vimina

**Vimina** is a Windows desktop automation tool inspired by the browser extension Vimium. Built on the FlaUI automation framework, it identifies window controls through the UIA3 protocol and generates letter labels for each interactive control. Users can precisely click any control just by typing on the keyboard. It also provides a complete HTTP API for integration with AI assistants and external programs.

**Core Philosophy:** Keyboard-first, control-level identification, AI-friendly

**Open Source Status:** Open source

### Anjian Jingling

**Anjian Jingling** (按键精灵) is a well-established Windows automation tool with nearly 20 years of history. It simulates mouse and keyboard operations through recording/scripting, supporting image recognition, color finding, memory reading, and is widely used in domestic game automation and RPA fields.

**Core Philosophy:** Record and replay, image recognition, script automation

**Open Source Status:** Commercial software

## Core Differences

### Control Recognition Technology

| Aspect | Vimina | Anjian Jingling |
|--------|--------|-----------------|
| **Core Technology** | FlaUI (UIA3 Protocol) | Coordinate positioning + Image recognition |
| **Recognition Method** | Control-level, semantic recognition | Pixel/coordinate/image level |
| **Recognition Precision** | Precise to control object | Precise to pixel |
| **Resolution Dependency** | :material-check: Completely independent | :material-alert: Partially dependent on coordinates |
| **Window Scaling Adaptation** | :material-check: Automatic adaptation | :material-close: Requires readjustment |
| **Dynamic Layout** | :material-check: Automatically adapts to control position changes | :material-close: Requires re-recording/adjustment |

**Vimina Control Recognition Example:**

```
After scanning the window, identified:
- Button "OK" → Label DJ
- Edit "Username Input" → Label DK
- MenuItem "File" → Label DL

No matter how the window position changes, clicking label DJ will always accurately click the "OK" button
```

**Anjian Jingling Recognition Example:**

```
Recording: Click at coordinate (500, 300)
Problem: After window moves, coordinates may no longer correspond to correct position
Solution: Use window binding + relative coordinates, or image recognition
```

### Interaction Method

| Aspect | Vimina | Anjian Jingling |
|--------|--------|-----------------|
| **Primary Interaction** | Keyboard label clicking | Mouse recording/script execution |
| **Real-time Feedback** | :material-check: Colored label highlighting | :material-close: No visual feedback |
| **Immediate Operation** | :material-check: Alt+F shows labels, direct input | :material-close: Need to write/record script first |
| **Learning Curve** | Low (similar to Vimium) | Medium (need to learn script syntax) |
| **Operation Threshold** | Zero-code usage | Need to write or record scripts |

### API and Integration Capabilities

| Aspect | Vimina | Anjian Jingling |
|--------|--------|-----------------|
| **HTTP API** | :material-check: Complete RESTful API | :material-close: No built-in HTTP API |
| **External Calls** | :material-check: Any language HTTP calls | :material-alert: Limited external call support |
| **AI Integration** | :material-check: Native support, JSON response | :material-close: Requires additional bridge development |
| **CORS Cross-origin** | :material-check: Supported | - |

### Image Recognition Capabilities

| Aspect | Vimina | Anjian Jingling |
|--------|--------|-----------------|
| **Image Finding** | :material-close: Not supported | :material-check: Powerful image finding |
| **Color Finding** | :material-close: Not supported | :material-check: Multi-point color finding |
| **OCR Text Recognition** | :material-close: Not supported | :material-check: Built-in OCR |
| **Screenshot Function** | :material-check: Supported | :material-check: Supported |

### Game Support

| Aspect | Vimina | Anjian Jingling |
|--------|--------|-----------------|
| **Regular Games** | :material-alert: Limited support | :material-check: Complete support |
| **DirectX Games** | :material-close: Mostly unsupported | :material-check: Supported |
| **OpenGL Games** | :material-close: Mostly unsupported | :material-check: Supported |
| **Memory Reading** | :material-close: Not supported | :material-check: Supported |

## Feature Comparison Table

| Category | Feature | Vimina | Anjian Jingling |
|----------|---------|--------|-----------------|
| **Basic Operations** | Mouse click | :material-check: | :material-check: |
| | Mouse move | :material-check: | :material-check: |
| | Mouse drag | :material-check: | :material-check: |
| | Keyboard press | :material-check: | :material-check: |
| | Combo keys | :material-check: | :material-check: |
| | Text input | :material-check: | :material-check: |
| **Control Recognition** | UIA control recognition | :material-check: | :material-close: |
| | Handle recognition | :material-check: | :material-check: |
| | Image recognition | :material-close: | :material-check: |
| | Color recognition | :material-close: | :material-check: |
| | OCR recognition | :material-close: | :material-check: |
| **Window Operations** | Window finding | :material-check: | :material-check: |
| | Window activation | :material-check: | :material-check: |
| | Window closing | :material-check: | :material-check: |
| | Multi-window management | :material-check: | :material-check: |
| **Background Operations** | Background mouse | :material-check: | :material-check: |
| | Background keyboard | :material-check: | :material-check: |
| | Background binding | :material-check: | :material-check: |
| **Script Features** | Variables | :material-check: | :material-check: |
| | Arrays | :material-check: | :material-check: |
| | Functions | :material-check: | :material-check: |
| | Loops | :material-check: | :material-check: |
| | Conditional statements | :material-check: | :material-check: |
| | Multi-threading | :material-alert: | :material-check: |
| | Plugin system | :material-close: | :material-check: |
| **Integration** | HTTP API | :material-check: | :material-close: |
| | Command line | :material-check: | :material-check: |
| | External calls | :material-check: | :material-alert: |
| | AI integration | :material-check: | :material-close: |
| **Others** | Recording function | :material-close: | :material-check: |
| | Visual editing | :material-alert: | :material-check: |
| | Script encryption | :material-check: | :material-check: |
| | Compile to exe | :material-check: | :material-check: |

## Pros and Cons Analysis

### Vimina

#### Pros

1. **Control-level Precise Recognition**
   - Based on UIA3 protocol, directly identifies buttons, input boxes, menus, etc.
   - Independent of screen coordinates, window movement/scaling doesn't affect operations
   - Supports getting control properties (name, type, state, etc.)

2. **Keyboard-first Design**
   - Label system allows users to operate any control without mouse
   - Vimium-like experience, keyboard-friendly
   - Zero-code usage, just press Alt+F to start

3. **AI-friendly**
   - Complete HTTP API, supports RESTful calls
   - JSON format response, easy to parse
   - Supports CORS cross-origin, can be called directly from web pages
   - Scan results contain semantic information, suitable for AI analysis

4. **Real-time Visual Feedback**
   - Colored labels show matching status (yellow/orange/green/gray)
   - Instant display of current input matching

5. **Stable Background Operations**
   - Click without moving mouse
   - Operate background windows without switching
   - Suitable for automation scripts and AI assistants

6. **Developer-friendly**
   - Can be called by Python, Node.js, Java, and any language
   - Complete API documentation
   - Easy to integrate into existing workflows

7. **Lightweight and Open Source**
   - Single exe file, no installation needed
   - Open source project, customizable

#### Cons

1. **Limited Game Support**
   - Most games don't expose UIA interfaces
   - DirectX/OpenGL games cannot identify controls
   - No image recognition, cannot operate through image finding

2. **Small Community Ecosystem**
   - Fewer script libraries
   - Relatively fewer tutorials and cases
   - Small user community

3. **No Image Recognition**
   - No image/color finding support
   - Cannot perform image comparison
   - No OCR text recognition

4. **No Recording Function**
   - Need to write scripts manually
   - No operation recording feature

### Anjian Jingling

#### Pros

1. **Mature Ecosystem**
   - Nearly 20 years of history, large user base
   - Many ready-made script libraries available
   - Rich tutorials and community support

2. **Strong Game Support**
   - Complete image recognition and color finding features
   - Supports memory reading
   - DirectX/OpenGL game support

3. **Recording Function**
   - Can record operations to automatically generate scripts
   - Lowers usage threshold
   - Quickly create automation scripts

4. **Rich Plugins**
   - Many third-party plugins extend functionality
   - Supports custom plugin development
   - Infinite functionality expansion

5. **Visual Editing**
   - Graphical script editor
   - Drag-and-drop interface design
   - Lower learning curve

#### Cons

1. **Coordinate Dependency**
   - Some features depend on screen coordinates
   - Resolution changes require script adjustment
   - Window position changes may affect scripts

2. **No API Interface**
   - No HTTP API
   - Difficult to be called by external programs
   - Not suitable for integration into modern applications

3. **Difficult AI Integration**
   - No native API support
   - Requires additional bridge program development
   - Not suitable for AI assistant scenarios

4. **Commercial Pricing**
   - Free version has limited features
   - Advanced features require payment
   - Commercial use requires licensing

## Usage Scenario Recommendations

### Scenarios Recommended for Vimina

| Scenario | Reason |
|----------|--------|
| **Daily Office Operations** | Label system for quick clicking, no scripting needed |
| **AI Assistant Integration** | Native HTTP API support, JSON response |
| **Developer Automation** | Can be called by code, integrated into workflows |
| **RPA Enterprise Applications** | Control-level recognition more stable, coordinate-independent |
| **Cross-resolution Deployment** | Control recognition unaffected by resolution |
| **CI/CD Integration** | HTTP API can be called in pipelines |
| **Web Application Integration** | CORS support, can be called from web pages |
| **Desktop Application Testing** | Control-level operations, more precise testing |

### Scenarios Recommended for Anjian Jingling

| Scenario | Reason |
|----------|--------|
| **Game AFK** | Image recognition, color finding, memory reading |
| **Game Automation** | DirectX/OpenGL game support |
| **Image Recognition Tasks** | Powerful image/color finding features |
| **Beginner Entry** | Recording function, visual editing |
| **Batch Operations** | Mature script libraries ready to use |
| **Multi-instance AFK** | Native multi-instance support |
| **Quick Prototyping** | Recording function for quick script creation |

## How to Choose

### Quick Selection Guide

| Your Need | Recommended Choice |
|-----------|-------------------|
| I want to quickly operate desktop apps with keyboard | **Vimina** |
| I want AI assistant to help me operate computer | **Vimina** |
| I want to develop automation tool integration | **Vimina** |
| I want to make game AFK scripts | **Anjian Jingling** |
| I need image/color finding features | **Anjian Jingling** |
| I'm a beginner, want to get started quickly | **Anjian Jingling** |
| I need cross-resolution usage | **Vimina** |
| I need to operate multiple game windows | **Anjian Jingling** |

## Summary

| Dimension | Vimina | Anjian Jingling |
|-----------|--------|-----------------|
| **Positioning** | Modern AI-era automation tool | Traditional automation script tool |
| **Strengths** | Control recognition, API integration, keyboard operation | Game automation, image recognition, community ecosystem |
| **Weaknesses** | Game support, image recognition | API integration, AI-friendly |
| **Target Users** | Developers, keyboard enthusiasts, AI users | Game players, automation beginners |
| **Learning Curve** | Low | Medium |
| **Price** | Free and open source | Free version limited, Pro version paid |

**Final Recommendation:**

- If you need **desktop application operations, AI integration, keyboard efficiency, developer automation** → Choose **Vimina**
- If you need **game AFK, image recognition, image/color finding, quick script recording** → Choose **Anjian Jingling**

Both can be used complementarily, choosing the right tool for different scenarios. Vimina is more suitable for modern developers and AI scenarios, while Anjian Jingling is better for traditional gaming and image automation scenarios.
