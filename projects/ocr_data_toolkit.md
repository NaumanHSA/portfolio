![OCR Data Toolkit Cover](https://raw.githubusercontent.com/NaumanHSA/ocr-data-toolkit/main/docs/cover.png)
<a href="https://github.com/your-username/enigma" target="_blank">
  <img src="https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub Repo" />
</a>

A powerful Python toolkit for generating high-quality **synthetic datasets** for Optical Character Recognition (OCR) model training and evaluation. It enables generating realistic text images with configurable backgrounds, fonts, augmentations, and corresponding ground-truth labels—ideal for both academic research and production training pipelines.

---

## 📦 Overview

The **OCR Data Toolkit** (`ocr_data_toolkit`) helps simulate a wide range of real-world OCR scenarios. Its features are tailored for robustness, scalability, and flexibility in synthetic data generation.

- 🎯 **Flexible text generation** (words, numbers, dates)
- 🖋️ **Custom fonts and backgrounds**
- 🧪 **Rich image augmentations**
- ⚙️ **Parallel processing with multiprocessing**
- 🔍 **Built-in visualization tools**
- 🧱 **Modular and extensible design**

Synthetic datasets allow developers to boost OCR performance, especially when real annotated data is hard to obtain.

---

## 🚀 Features

### 📝 Text Generation
- Randomized text including words, numbers, and dates
- Customizable generation probabilities

### 🖼️ Font & Background Selection
- Use bundled or custom font/background image collections
- Auto-loading built-in fonts and images based on language code

### 🎨 Rich Augmentations
- Gaussian blur, motion blur, bokeh blur
- Moiré patterns, elastic distortions, ink bleed
- Perspective transforms, brightness, opacity control
- Letter spacing, cropping, resizing, and stretch factors

### ⚡ Fast Multiprocessing
- Parallel generation using multiple CPU cores for speed and scalability

### 🧪 Train/Test Dataset Creation
- Auto-split datasets and generate consistent `gt.txt` ground truth files

### 🔍 Font Visualization Utility
- Generate a visual catalog of fonts for quality assurance

### 🔧 Easy Configuration
- Entire toolkit controlled using Python config dataclasses or dictionaries

---

## 🛠️ Configuration

### Input Config (`Config` class)
All generation parameters are defined using a dataclass. Highlights include:

| Parameter | Type | Description |
|----------|------|-------------|
| `language` | `str` | Language code (e.g., `"en"`). Defaults to English |
| `bag_of_words` | `List[str]` | Optional vocabulary list |
| `backgrounds_path` | `str` | Path to background images |
| `fonts_path` | `str` | Path to font files |
| `text_probs` | `Dict[str, float]` | Probability for text/date/number generation |
| `output_image_size` | `Tuple[int, int]` | Image size (width, height) or None for natural |
| `train_test_ratio` | `float` | Train/test split ratio (default `0.2`) |
| `output_save_path` | `str` | Save directory |
| `augmentation_config` | `Dict` | Customizable augmentation options |
| `num_workers` | `int` | Number of workers (default `4`) |

Defaults ensure immediate usability without needing extensive setup.

---

## 🧪 Augmentation Options (`AugmentationConfig`)

| Parameter | Type | Default | Description |
|----------|------|---------|-------------|
| `max_num_words` | `int` | `5` | Max words per image |
| `num_lines` | `int` | `1` | Lines of text |
| `font_size` | `int` | `36` | Font size |
| `text_colors` | `List[str]` | `["#2f2f2f", "black", "#404040"]` | Text color palette |
| `letter_spacing_prob` | `float` | `0.4` | Apply random spacing |
| `margin_x`, `margin_y` | `Tuple[float, float]` | `(0.5, 1.5)` | Padding multipliers |
| `blur_probs` | `Dict[str, float]` | `{gaussian: 0.3, custom_blurs: 0.6}` | Blurring probability |
| `moire_prob` | `float` | `0.3` | Moiré effect |
| `opacity_prob` | `float` | `0.3` | Faded text simulation |
| `opacity_range` | `Tuple[int, int]` | `(150, 210)` | Alpha transparency |
| `brightness_range` | `Tuple[float, float]` | `(0.7, 1.2)` | Brightness variation |
| `perspective_transform_prob` | `float` | `0.3` | Perspective warping |
| `random_crop_*_range` | `Tuple[float, float]` | Cropping image edges |
| `random_resize_factor_range` | `Tuple[float, float]` | `(0.9, 1.0)` | Resize range |
| `random_stretch_factor_range` | `Tuple[float, float]` | `(0.1, 0.3)` | Vertical stretching |

---

## 🖼️ Output Image & Padding Strategy

If `output_image_size` is specified, each image is resized and padded to match the target size, preserving aspect ratio. Padding is added to bottom/right with black pixels—ensuring uniform image sizes.

---

## 📁 Output Structure

When using `generate_training_data`, the toolkit produces:

- `images/`: Folder with all generated `.png` images
- `gt.txt`: Ground truth text file (`filename -> text mapping`)

This standard output format is compatible with many OCR training pipelines.

---

## 🧩 Extensible Design

The codebase is modular and extensible, making it easy to integrate new fonts, languages, background styles, or augmentations.

---

## 🔧 Ideal For

- Training OCR models with diverse data
- Benchmarks and robustness testing
- Low-resource language OCR experiments
- Custom production OCR systems

---

**OCR Data Toolkit** helps you simulate the unpredictable messiness of real-world text in a controlled, high-performance environment—boosting the accuracy and generalization power of your OCR models.