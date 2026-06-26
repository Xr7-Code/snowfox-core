# 🦊 SnowFoxOS — Core Specifications & Development Blueprint

Welcome to the central planning, architecture, and issue-tracking repository for **SnowFoxOS**. 

Unlike a traditional source-code repository, this space is dedicated entirely to the high-level conceptualization, performance optimization tracking, and architectural design of the SnowFoxOS Linux distribution. It serves as the single source of truth for the OS development lifecycle, linking user experience goals with system-level configurations.

---

## 🎯 Purpose of this Repository

Developing a customized, ultra-lightweight, and visually cohesive Linux distribution requires rigorous testing and documentation. This repository is used to:
* **Track Bugs & Enhancements:** Document system-level fixes, kernel parameter updates, and desktop environment patches.
* **Architect Future Releases:** Design core features for upcoming versions, such as the `snowfox node` workflow switcher in v3.
* **Maintain Visual Consistency:** Outline precise GTK, X11, and terminal color schemes to preserve the signature SnowFox purple aesthetic.

## 🔗 Related Repositories

This project is part of the SnowFoxOS ecosystem. Depending on what you are looking for, please refer to the following companion repositories:
* 💻 **`snowfoxos-installer`** *(Coming Soon)*: The actual shell scripts, package lists, and dotfiles used to deploy the OS on hardware.
* 🎨 **`snowfox-theme`**: The decoupled GTK, Rofi, and Polybar asset configuration files.

---

## 🗺️ Repository Structure & Quick Links

To navigate the current development phase, explore our structured documentation in the **GitHub Wiki**:

* 📄 **[System & Error Log (Changelog)](../../wiki/System-&-Error-Log)** *Our live development journal containing all resolved kernel/driver blocks, current performance metrics, and immediate hotfixes.*
* 🎮 **[SnowFox Node Concept (v3 Roadmap)](../../wiki/SnowFox-Node-Concept)** *The technical architectural breakdown for the upcoming 3-stage switcher (`desktop`, `server`, and controller-driven `console` mode).*
* ⚙️ **[Component Architecture](../../wiki/Component-Architecture)** *Details on how the underlying system components (i3wm, Polybar, Picom, NetworkManager) seamlessly interlock.*

---

## 📋 Active Core Focus (v2.2 Polish Phase)

Before expanding into version 3, the current development milestone is strictly focused on bulletproofing **SnowFoxOS v
