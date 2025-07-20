# LLM Comparison

This repository provides a lightweight benchmark and utilities for comparing the math-reasoning performance of several small language models (1 – 3 B parameters).  It contains:

* **`main.ipynb`** – a Jupyter notebook that loads multiple open-source models, runs them on a small math-focused dataset (`maths.json`), and stores the raw model outputs to the `model_output/` directory.
* **`maths.json`** – a curated set of short-answer math problems used for evaluation.
* **`model_output/`** – text files containing the generated answers from each model that has been evaluated so far.

<p align="center">
  <img src="https://raw.githubusercontent.com/your-username/llm_comparison/main/.github/assets/llm_comparison_banner.png" alt="LLM Comparison banner"/>
</p>

## Table of Contents

1. [Quick Start](#quick-start)
2. [Project Structure](#project-structure)
3. [Running Your Own Evaluation](#running-your-own-evaluation)
4. [Adding New Models](#adding-new-models)
5. [Contributing](#contributing)
6. [License](#license)

## Quick Start

1. Clone the repository and install the dependencies

   ```bash
   git clone https://github.com/your-username/llm_comparison.git
   cd llm_comparison
   python -m venv .venv
   source .venv/bin/activate  # Windows: .venv\Scripts\activate
   pip install -r requirements.txt
   ```

2. Launch Jupyter (or JupyterLab) and open the notebook:

   ```bash
   jupyter lab
   # or
   jupyter notebook
   ```

3. Run all cells in `main.ipynb` – this will download the Hugging Face models, perform inference on the problems in `maths.json`, and write each model’s answers into `model_output/<model_name>.txt`.

⚠️  **Note:** Some models require a reasonably powerful GPU (≥ 10 GB VRAM) or will fall back to slower CPU inference.

## Project Structure

```text
llm_comparison/
├── main.ipynb         # Notebook orchestrating the evaluation
├── maths.json         # Evaluation dataset
├── model_output/      # Generated answers for each model
├── requirements.txt   # Python dependencies
└── README.md          # Project documentation (you are here)
```

## Running Your Own Evaluation

To evaluate additional models, simply add their model IDs to the list inside `main.ipynb` and re-run the relevant cells.  Results will automatically be appended as new files under `model_output/`.

If you would rather script the evaluation instead of using Jupyter, you can export each cell as a Python script using **File ▸ Export Notebook As… ▸ Export as Python** in JupyterLab.

## Adding New Models

1. Make sure the model is available on [Hugging Face Hub](https://huggingface.co/) and supports causal language-model inference.
2. Append its repo ID to the list in the notebook.
3. Optionally tweak the generation parameters (temperature, max tokens, etc.).
4. Commit the new output file so others can compare results.

## Contributing

Pull requests are very welcome!  Please open an issue first to discuss major changes.

1. Fork the repo and create your feature branch:
   ```bash
   git checkout -b feature/awesome-thing
   ```
2. Commit your changes with clear commit messages.
3. Push to your fork and open a pull request.
