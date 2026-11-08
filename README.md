# PotatoCare AI — Potato Leaf Disease Screening Demo

PotatoCare AI is a Flask application concept built around a Vision Transformer (ViT) classifier for potato leaf images. The intended model labels are **Early blight**, **Late blight**, and **Healthy**.

> **Repository status:** The current public GitHub repository contains this README only. The application source code, dependency file, trained checkpoint, and notebook are not currently committed here. The setup instructions below describe the local project layout and will become reproducible from GitHub once those files are added.

> **Agricultural disclaimer:** This is an educational screening aid, not a definitive plant-disease diagnosis. Confirm uncertain cases with a qualified agricultural extension specialist.

## Intended application features

- Flask web application.
- Potato leaf image upload and preview.
- ViT-based image classification.
- Three output classes: Early blight, Late blight, and Healthy.
- Prediction confidence and class-probability display.
- Friendly handling for missing checkpoints and invalid images.
- Health endpoint and responsive upload interface.

## Technology

- Python, Flask
- PyTorch, torchvision, timm
- Pillow
- HTML, CSS, JavaScript

## Expected local project files

```text
potato_disease_flask/
├── app.py
├── potato_vit.pth
├── requirements.txt
├── templates/
│   └── index.html
└── README.md
```

The local application expects a checkpoint named `potato_vit.pth` beside `app.py`, unless `POTATO_MODEL_PATH` is configured. The checkpoint is expected to contain `model_state_dict` and `classes`, and to match `timm.create_model("vit_base_patch16_224", pretrained=False, num_classes=...)` plus the training preprocessing.

## Setup after adding the application files

Use a Python version compatible with your installed PyTorch build.

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
python app.py
```

Open [http://127.0.0.1:5000](http://127.0.0.1:5000).

## Model evaluation and limitations

The training notebook reports 100% validation accuracy on 430 images, but this should not be presented as evidence of real-world accuracy. The healthy validation class contains only 25 samples, and a single random split may be unrepresentative.

Before making stronger claims:

1. Evaluate on a separate, untouched test set.
2. Use stratified splitting.
3. Check for near-duplicate images and leakage across splits.
4. Report per-class precision, recall, F1-score, and a confusion matrix.
5. Test photographs collected in real field conditions.

## Next repository steps

- Commit the Flask source code and templates.
- Add a `requirements.txt` with compatible dependency versions.
- Add the training notebook or a reproducible training script.
- Document how to obtain the model checkpoint without committing large or restricted files.
- Add screenshots of the actual running application.

## Author

**Ahmad Zulfiqar** — [GitHub](https://github.com/malikahmad) · [LinkedIn](https://www.linkedin.com/in/malik-ahmad-06abb31a1/)
