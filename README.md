# AI Image Lab: how does AI make images?

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/phnam05/stable-diffusion-lab/blob/main/sd_lab.ipynb)
[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](LICENSE)

**Created by [Nam Ngo](https://github.com/phnam05)** (College of Engineering and Computer Science, VinUniversity) for the AI Literacy course, AI in Media session.

A 60-minute, hands-on Stable Diffusion lab for students with no coding background. They open one Google Colab notebook, press ▶ and move sliders, and learn what each setting of an image generator does. Free; needs only a Google account.

| File | What it is |
|---|---|
| [sd_lab.ipynb](sd_lab.ipynb) | The student notebook (code hidden behind Colab forms). |
| [gallery/](gallery/) | Example results shown when a notebook gets no GPU. |

## Before class
1. **Build the backup gallery.** Open the notebook in Colab with a T4 GPU (*Runtime ▸ Change runtime type*). Run **⚙️ Setup**, then the last cell (**🧑‍🏫 Instructor only**) with `export_now` ticked (~3–4 min). Unzip the downloaded `gallery.zip` into `gallery/` and push.
2. **Share the student link** (as a short link + QR code): `https://colab.research.google.com/github/phnam05/stable-diffusion-lab/blob/main/sd_lab.ipynb`
3. **Test run** on a free account at the same time of day as class (*Runtime ▸ Run all*), and have 5–10 people open the link at once.
4. **Pick 1–2 target images** for the playground challenge (generate them and note the secret prompt).
5. **Plan groups of 3.** Free Colab GPUs aren't guaranteed, but a group only needs one member to get one.

## 60-minute run of show
| Time | What happens | Notebook |
|---|---|---|
| 0–5 | Show link/QR. Groups of 3, one driver laptop each. Everyone presses ▶ on Setup right away. | 1 |
| 5–12 | Mini-lecture: *AI images are sculpted out of noise.* First image, watch it denoise live. | 2, 3 |
| 12–30 | Seed → Steps → CFG → Negative prompt, ~4 min each: predict out loud, run, compare. | 4–7 |
| 30–40 | Image-to-image on the sample picture or a student photo. | 8 |
| 40–55 | Bias experiment, then class discussion using the 💬 questions. | 9 |
| 55–60 | Wrap-up and bigger questions (consent, copyright, deepfakes, labeling, energy). Inpainting + playground for early finishers. | 10–11 |

Rotate the driver each section so everyone gets to type a prompt.

## Facilitation tips
- **Predict first, every time.** The lab works best when people are surprised.
- **Bias:** frame it around *training data and defaults*. The images aren't real people.
- **Photos:** students upload only their own photos, no classmates' faces without consent.
- **Black image** = the safety filter blocked it. A good moment to talk about content moderation.

## Troubleshooting
| Problem | Fix |
|---|---|
| "Not authored by Google" | Click **Run anyway**. |
| **No GPU connected** | *Runtime ▸ Change runtime type ▸ T4 GPU*, re-run Setup. Otherwise join another group; cells still show the gallery. |
| "Please run Setup first" / disconnected | Re-run Setup (fast the second time). |
| "GPU ran out of memory" | Smaller size / fewer images, or *Runtime ▸ Restart session* and re-run Setup. |
| Upload fails | Use JPG/PNG (not iPhone HEIC). |
| Anything else | Run `print(lab.last_error)` in a new cell. |

## Technical notes
- Model: [DreamShaper 8](https://huggingface.co/Lykon/dreamshaper-8) (SD 1.5 fine-tune, safety filter always on) via Colab's preinstalled `diffusers`. First Setup downloads ~3 GB; inpainting another ~3 GB.
- Smoke-tested on CPU with a tiny model but **not yet on a real T4**. Do the test run before class.

## Reusing this lab
Free to use and adapt for **non-commercial** purposes with **credit to the author**, under [CC BY-NC 4.0](LICENSE). The DreamShaper 8 model keeps its own licence (CreativeML OpenRAIL-M).

> Ngo, N. (2026). *AI Image Lab: A hands-on Stable Diffusion lab for non-CS students* [Google Colab notebook]. College of Engineering and Computer Science, VinUniversity. https://github.com/phnam05/stable-diffusion-lab

Questions or improvements are welcome as [GitHub issues](https://github.com/phnam05/stable-diffusion-lab/issues).
