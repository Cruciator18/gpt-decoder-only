# Character-Level GPT Language Model

This project is a clean, polished PyTorch implementation of a decoder-only Transformer (GPT-style model), designed for character-level text generation. The architecture is based on the groundbreaking "Attention Is All You Need" paper and inspired by Andrej Karpathy's nanoGPT project.

The model is trained on the TinyShakespeare dataset to generate new text in the style of Shakespeare.

---
## Key Features & Improvements

This implementation goes beyond a basic script by incorporating several key enhancements to improve training stability, performance, and model generalization.

* **GPT-2 Style Weight Initialization:** The model uses a more sophisticated initialization scheme where the weights of residual projection layers are scaled down. This is crucial for stabilizing training in deeper networks by ensuring a clean gradient flow from the start.
* **Mixed Precision Training:** The training loop leverages PyTorch's Automatic Mixed Precision (`torch.amp`). This boosts performance by using `float16` for certain operations, which significantly speeds up computation on modern GPUs with Tensor Cores and reduces memory footprint.
* **Overfitting Mitigation:** To ensure the model generalizes well on the small TinyShakespeare dataset, several regularization techniques have been implemented:
    * **Weight Decay:** The AdamW optimizer is configured with weight decay to prevent model weights from growing too large.
    * **Reduced Model Complexity:** The hyperparameters (`n_layer`, `n_embd`, `n_head`) have been carefully chosen to create a smaller model with ~3.26M parameters, reducing its capacity to simply memorize the training data.

---
## Setup and Usage

To run this project locally, you'll need a Python environment and PyTorch with CUDA support.

### 1. Clone the Repository
```bash
git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
cd your-repo-name
```

### 2. Create and Activate a Virtual Environment
It's highly recommended to use a virtual environment to manage dependencies.
```bash
# Create the environment
python -m venv .venv

# Activate it
# On Windows:
.\.venv\Scripts\activate
# On macOS/Linux:
source .venv/bin/activate
```

### 3. Install Dependencies
The primary dependency, PyTorch, must be installed with a specific command to ensure CUDA compatibility.

First, visit the **[official PyTorch website](https://pytorch.org/get-started/locally/)** to get the correct command for your system. For example, for CUDA 12.1:
```bash
pip3 install torch torchvision torchaudio --index-url [https://download.pytorch.org/whl/cu121](https://download.pytorch.org/whl/cu121)
```
Then, install any other packages:
```bash
pip install -r requirements.txt
```

### 4. Run the Training Script
Simply execute the Python script to start training the model.
```bash
python train.py
```
The script will print the training and validation loss at regular intervals and generate a 500-token sample of text upon completion.
