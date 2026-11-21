#!/usr/bin/env python3
"""
Voyager OS · GK-06 — Single-File GitHub Profile README Generator
Generates 5 gallery-grade algorithmic symbol portraits from S. Gokula Kumaran's
photo, assembles the 100% zero-external-dependency README.md using verified
GitHub MathJax colorv2 (strictly within MathJax's 5 KB maxBuffer per block) +
Mermaid + Hover-Reactive HTML biometrics, runs an automated sanitizer audit,
and outputs a GitHub-authentic local preview harness.
"""
from __future__ import annotations
import html
import json
import math
import re
from collections import deque
from pathlib import Path
from typing import Dict, List, Tuple
import numpy as np
from PIL import Image, ImageEnhance, ImageFilter
PHOTO_PATH = Path(
    r"C:/Users/gokul/.gemini/antigravity/brain/1704e1f8-1a1e-4155-a17b-eec440cc2964/.user_uploaded/media_1795284615359_c6292c14.jpg"
)
PROJECT_DIR = Path(
    r"C:/Users/gokul/.gemini/antigravity/scratch/sGokulaKumaran-github-profile"
)
README_PATH = PROJECT_DIR / "README.md"
PREVIEW_PATH = PROJECT_DIR / "preview" / "github_preview.html"
# ---------------------------------------------------------------------------
# 1. Image Preprocessing, Segmentation & Sculptural Facial Shading
# ---------------------------------------------------------------------------
def load_and_segment_portrait(photo_path: Path) -> Tuple[np.ndarray, np.ndarray]:
    """
    Loads the portrait, crops cleanly centered on the face/bust, and removes
    the white studio background via edge-seeded flood fill.
    """
    img = Image.open(photo_path).convert("RGB")
    arr = np.array(img)
    h, w, _ = arr.shape  # 682 x 1024
    x0, x1 = 224, 800   # width 576
    y0, y1 = 22, 566    # height 544 (aspect 1.059)
