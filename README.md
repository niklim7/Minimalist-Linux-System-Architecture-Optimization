Minimalist Linux System Architecture & Optimization

Project Goal: To architect, build, and optimize a highly efficient, keyboard-driven computing environment using minimal resources. The system was designed to meet strict Non-Functional Requirements (NFRs) for low power consumption, speed, and focus, maximizing operational time for specialized tasks like contest logging and embedded system management.

Project Summary & Technical Achievements

Area

Achievement & Rationale

System Architecture

Musl Void Linux (x86_64): Selected and installed a minimal, non-default distribution (musl and runit) to ensure the smallest possible footprint and deepest understanding of Linux service fundamentals.

Resource Optimization

Validated Power Consumption: Achieved a steady-state power consumption of 5–6 watts, extending battery life for specialized portable operations to over 12 hours. This was achieved through BIOS/CPU tuning and running a completely headless TTY environment.

UX & Usability

Custom Framebuffer Workflow: Architected a complete TUI (Text-User Interface) workflow using fbterm and tmux on TTYs, allowing for a keyboard-driven, distraction-free environment without relying on a full desktop environment.

Low-Level Integration

Hardware Event Handling: Successfully integrated low-level hardware events (acpid) to manage power (Sleep/Hibernate) and map laptop keys (Volume, Mic, Mute) to system functions (amixer), ensuring the system responds correctly to physical user interaction.

Software Customization

Build from Source & Toolchain: Identified the necessity for specialized tools (tlf) not available in the musl repository, demonstrating competence in setting up a build environment and compiling application software from source code.

Detailed Application Stack

The final system architecture required careful selection of applications optimized for efficiency and the framebuffer interface:

Core Workflow: tmux (Window/Session Manager), fbterm (Terminal), nnn (File Manager), aerc (Email Client), rbw (Password Manager).

Media & Browsing: w3m (Web Browser with w3m-img support), amfora (Gemini Browser), mpv --vo=fbdev (Video), fbi (Image Viewer).

Specialized Tools: wordgrinder (Word Processor), cmus (Audio Player), tlf / yfklog (Contest/General QSO Loggers).

Key Technical Challenges & Resolutions

This systematic approach required extensive low-level troubleshooting:

Service Dependency Debugging: Diagnosed and fixed complex dependency chain issues for services like Bluetooth (dbus -> bluetoothd -> bluez).

Bootloader Repair: Manually corrected a failed GRUB installation by installing to the EFI fallback path.

Event Consistency: Solved the "corrupted screen" bug on system resume by implementing the tmux refresh-client command, ensuring visual state consistency post-suspend.

Authentication Integration: Successfully integrated the aerc email client with the external CLI password manager (rbw) to manage specialized credentials (e.g., Posteo App Passwords).

https://private-user-images.githubusercontent.com/219470651/514367705-7e4dde31-3496-43fc-9da4-e75783242e86.jpg?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjMxMTcwNTAsIm5iZiI6MTc2MzExNjc1MCwicGF0aCI6Ii8yMTk0NzA2NTEvNTE0MzY3NzA1LTdlNGRkZTMxLTM0OTYtNDNmYy05ZGE0LWU3NTc4MzI0MmU4Ni5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUxMTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MTExNFQxMDM5MTBaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT05NzVjMjQ1ZmRjMjMxMzYzMmJiMGNlZmZhMjYxMGU1ODVjOTljZGY5YTZmNWY0MThiMTBhZjNmZmUzZTEyNjE4JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.NjnvGZkv3IXTb9F058EwiIKvES6yyyRvi5Qu5HxtLCQ
