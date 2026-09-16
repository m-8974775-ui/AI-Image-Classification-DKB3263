# AI Image Classification – DKB3263

A Computer Vision image-classification application built with **Google Teachable Machine** and deployed as a browser application through GitHub Pages.

## Project Overview

This project implements image classification using a trained Teachable Machine model. The application accepts an image upload or webcam input and displays the predicted class, confidence score, and a simple confidence/status indicator.

**Teachable Machine model:** https://teachablemachine.withgoogle.com/models/YOrkzhUi-/

## Project Requirements Covered

- Image classification using Google Teachable Machine
- Input through webcam and/or image upload
- Prediction/class display
- Confidence score display
- Simple prediction status indicator
- Reset/retry function
- Low-confidence handling
- Browser-based model integration using TensorFlow.js
- GitHub version control and documentation
- Experiment and testing documentation templates

The assignment requires at least three classes, new test images not used during training, recorded prediction/confidence/error results, and at least two model experiments. The actual class names and measured results should be recorded from the trained model and real testing sessions rather than invented.

## Repository Structure

```text
.
├── index.html                 # Main web application
├── README.md                  # Project documentation
├── docs/
│   ├── dataset.md             # Dataset documentation template
│   ├── experiments.md         # Two-experiment comparison template
│   ├── testing.md              # Testing/evaluation record template
│   └── ai-code-assistant.md   # AI Code Assistant usage evidence
└── .nojekyll
```

## Run Locally

1. Open `index.html` in a modern browser.
2. Allow camera permission if webcam mode is used.
3. Select an image or start the webcam.
4. The application loads the Teachable Machine model and displays the prediction and confidence.

For GitHub Pages, enable **Settings → Pages → Deploy from branch → main → / (root)**.

## Model Integration

The application loads the exported Teachable Machine TensorFlow.js model directly from the public model URL. The inference flow is:

`Image/Webcam → Teachable Machine TensorFlow.js Model → Prediction Probabilities → Highest Confidence Class → UI`

No API keys, passwords, or private tokens are stored in this repository.

## Testing & Experiments

See:

- [`docs/dataset.md`](docs/dataset.md)
- [`docs/experiments.md`](docs/experiments.md)
- [`docs/testing.md`](docs/testing.md)
- [`docs/ai-code-assistant.md`](docs/ai-code-assistant.md)

These documents are structured to record the evidence required by the DKB3263 project brief. Measured accuracy, confidence values, sample counts, and error cases should only be entered from actual project observations.

## Ethical / Integrity Notes

Use legally obtained or permitted datasets. Do not place passwords, API keys, access tokens, or private personal information in the repository. AI-assisted code must be reviewed, understood, and tested by the student.

## License

For academic/project use.
