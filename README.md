# AI Image Lab: how does AI make images?

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/phnam05/stable-diffusion-lab/blob/main/sd_lab.ipynb)
[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](LICENSE)

**Created by [Nam Ngo](https://github.com/phnam05)** (College of Engineering and Computer Science, VinUniversity) for the AI Literacy course, AI in Media session.

A 60-minute, hands-on Stable Diffusion lab for the AI Literacy course (AI in Media). Students need no coding background. They open one Google Colab notebook, press ▶ buttons and move sliders, and learn what each setting of an image generator actually does. It costs $0 and needs only a Google account.

| File | What it is |
|---|---|
| [sd_lab.ipynb](sd_lab.ipynb) | The student notebook (all code hidden behind Colab forms). |
| [gallery/](gallery/) | Example results shown to students whose notebook gets no GPU (you generate these once). |

## Why it's built this way
- **Free Colab, but not the AUTOMATIC1111 / ComfyUI / Fooocus web UIs.** Google restricts those UIs on Colab (the [A1111 wiki](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Online-Services) warns that accounts can be banned). They also take 5–10 min to install and show 100+ settings. This notebook calls the `diffusers` library directly: no web server and no tunnel. It installs nothing extra, because Colab already ships `diffusers`.
- **Other hosts considered and rejected:** Kaggle (phone verification per student), SageMaker Studio Lab (1–5+ days for account approval), Paperspace (free tier unclear), RunPod/vast.ai (paid), and Hugging Face ZeroGPU Spaces (a 2–5 min daily quota per visitor, which a full room uses up).
- **Experiments instead of free play.** Every setting gets one cell that draws a side-by-side strip with the same seed, and students *predict before they run*.
- **Model:** [DreamShaper 8](https://huggingface.co/Lykon/dreamshaper-8), a Stable Diffusion 1.5 fine-tune. It is fast on a free T4 at 512×512, needs no Hugging Face login, and includes the standard safety filter (always on). Licence: CreativeML OpenRAIL-M, which forbids harmful uses. Backup: the original SD 1.5.

## One-time setup (≈30 min, at least a week before class)
1. ~~**Create a public GitHub repo**~~ Done: [phnam05/stable-diffusion-lab](https://github.com/phnam05/stable-diffusion-lab).
2. ~~**Point the notebook at your gallery.**~~ Done: `GALLERY_BASE_URL` in the Setup cell points at this repo's `gallery/`.
3. **Build the backup gallery.** Open the notebook in Colab (link below) → *Runtime ▸ Change runtime type ▸ T4 GPU*. Run **⚙️ Setup**, then scroll to the last cell (**🧑‍🏫 Instructor only**), tick `export_now`, and run it (~3–4 min). It downloads `gallery.zip`. Unzip it into `gallery/` and push.
4. **Student link:** `https://colab.research.google.com/github/phnam05/stable-diffusion-lab/blob/main/sd_lab.ipynb`. Put it on a slide as a short link and a QR code. The Open in Colab badge is at the top of this README.

## Pre-class checklist
- [ ] **Test run on a free account, at the same weekday and time as the class:** *Runtime ▸ Run all*. Note how long Setup and each experiment take.
- [ ] **Load test:** 5–10 people open the link at the same time. Everyone should get a GPU and finish Setup.
- [ ] Gallery images load: open the notebook on a CPU runtime and check that the sections show the example pictures.
- [ ] Pick 1–2 target images for the playground challenge (generate them yourself and note the secret prompt).
- [ ] Plan the **groups of 3**. With 60+ students that's ~20–22 notebooks running instead of 60+, which makes it much more likely everyone gets a GPU.

## 60-minute run of show
| Time | What happens | Notebook |
|---|---|---|
| 0–5 | Link/QR on screen. Groups of 3, one **driver** laptop per group. *"Open the link, press ▶ on Setup right now, click 'Run anyway'."* Setup downloads while you talk. | 1 |
| 5–12 | Mini-lecture: *AI images are sculpted out of noise.* Groups make a first image, then watch it denoise live. | 2, 3 |
| 12–30 | Seed → Steps → CFG → Negative prompt, ~4 min each. For each one: read, **groups predict out loud**, run, compare. | 4–7 |
| 30–40 | Image-to-image: restyle the sample picture or a photo the students took. | 8 |
| 40–55 | Bias experiment (~3 min to run), then a class discussion using the 💬 questions in the notebook. | 9 |
| 55–60 | Wrap-up: the "What did we learn" table and the bigger questions (consent, copyright, deepfakes, labeling, energy). Inpainting + playground for early finishers or homework. | 10–11 |

**Timing will vary.** Each image takes a few seconds on a T4, and each experiment strip takes roughly 15–40 s (the bias grid ~30–60 s). Check your own numbers in the test run. The **driver** changes every section so everyone gets to type a prompt; the others predict and pick the prompts.

## Facilitation tips
- **Predict first, every time.** Ask for a show of hands (*"Who thinks 40 steps will look twice as good?"*). The lab works best when people are surprised by the result.
- **Bias discussion:** frame it as being about *training data and defaults*, not about individuals. Results are random and can be uncomfortable. Remind students the images aren't real people, and steer toward *where patterns come from* and *who is affected*.
- **Photos:** students upload only their own photos (no faces of classmates without consent). Uploads stay in that student's Colab session and are deleted from the machine right after reading.
- **Safety filter:** a black image means the filter blocked it. That's a good moment to talk about content moderation and its false positives.
- **Video (Leandro's "video" angle):** generating video on a free T4 is too slow for a live lab. Show a 3–5 min demo of a current free video tool at the end, and check what's actually free the week before, since free tiers change often.

## Troubleshooting
| Problem | Fix |
|---|---|
| "This notebook was not authored by Google" | Click **Run anyway** (expected for notebooks opened from GitHub). |
| Setup says **No GPU connected** | *Runtime ▸ Change runtime type ▸ T4 GPU ▸ Save*, run Setup again. If Colab can't give a GPU: join a neighbour's group. The cells still show the example gallery. |
| "Please run ⚙️ 1. Setup first" | Setup wasn't run in this session (or the runtime restarted). Run it again; it's fast the second time. |
| Image is **black** / "[blocked]" | Safety filter. Change the prompt or seed. |
| "GPU ran out of memory" | Use a smaller size / fewer images. If it repeats: *Runtime ▸ Restart session*, re-run Setup. |
| Notebook disconnected after a break | Colab disconnects idle sessions. Reconnect and re-run Setup (~1 min). |
| Upload fails | Use JPG/PNG. iPhone HEIC doesn't work, so screenshot the photo and upload that instead. |
| Anything else | The red box gives a short error. For details run `print(lab.last_error)` in a new cell. |

## Technical notes
- Uses Colab's preinstalled `torch` and `diffusers` (checked against Colab's November 2026 image: diffusers 0.42.1, transformers 5.22, torch 2.14). It installs `diffusers==0.42.1` only if Colab ever stops shipping it.
- The first Setup downloads ~3 GB (model in fp16, including the safety checker). The inpainting section downloads another ~3 GB the first time it runs.
- The live denoising preview uses [TAESD](https://huggingface.co/madebyollin/taesd), a tiny decoder (~10 MB).
- The notebook was smoke-tested end to end on CPU with a tiny test model: every cell, the no-GPU path, bad inputs, all five samplers and the gallery export. It has **not** yet been run on a real T4. Do the test run above before class.

## Reusing this lab
You're welcome to use and adapt this lab in your own course, as long as it's **non-commercial** and you **credit the author**. It's licensed under [CC BY-NC 4.0](LICENSE). This covers the notebook and this guide. The DreamShaper 8 model keeps its own licence (CreativeML OpenRAIL-M).

**How to cite:**
> Ngo, N. (2026). *AI Image Lab: A hands-on Stable Diffusion lab for non-CS students* [Google Colab notebook]. College of Engineering and Computer Science, VinUniversity. https://github.com/phnam05/stable-diffusion-lab

**Contact:** [github.com/phnam05](https://github.com/phnam05). Questions or improvements are welcome as GitHub issues.
