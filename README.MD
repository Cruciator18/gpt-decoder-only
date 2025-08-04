

-----

````markdown
# Character-Level GPT Language Model

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.1-orange.svg)](https://pytorch.org/)

This project is a clean, polished PyTorch implementation of a decoder-only Transformer (GPT-style model), designed for character-level text generation. The architecture is based on the groundbreaking "Attention Is All You Need" paper and inspired by Andrej Karpathy's nanoGPT project.

The model is trained on the TinyShakespeare dataset to generate new text in the style of Shakespeare.

---

## Key Features & Improvements

# Character-Level GPT Language Model

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.1-orange.svg)](https://pytorch.org/)

This project is a clean, polished PyTorch implementation of a decoder-only Transformer (GPT-style model), designed for character-level text generation. The architecture is based on the groundbreaking "Attention Is All You Need" paper and inspired by Andrej Karpathy's nanoGPT project.

The model is trained on the TinyShakespeare dataset to generate new text in the style of Shakespeare.

---

## Key Features & Improvements

* **GPT-2 Style Weight Initialization**: The model uses a more sophisticated initialization scheme where the weights of residual projection layers are scaled down. This is crucial for stabilizing training in deeper networks by ensuring a clean gradient flow from the start.
* **Mixed Precision Training**: The training loop leverages PyTorch's Automatic Mixed Precision (`torch.amp`). This boosts performance by using `float16` for certain operations, which significantly speeds up computation on modern GPUs with Tensor Cores and reduces memory footprint.
* **Overfitting Mitigation**: To ensure the model generalizes well on the small TinyShakespeare dataset, several regularization techniques have been implemented:
    * **Weight Decay**: The `AdamW` optimizer is configured with weight decay to prevent model weights from growing too large.
    * **Reduced Model Complexity**: The hyperparameters (`n_layer`, `n_embd`, `n_head`) have been carefully chosen to create a smaller model with ~3.26M parameters, reducing its capacity to simply memorize the training data.

---

## Hardware Requirements

⚠️ **GPU Required**

This model was trained and validated on a **T4 GPU**. Due to the computational intensity of Transformer models, training on a CPU is **not recommended** as it will be extremely slow. A CUDA-enabled GPU is required for reasonable training times.

---

## Setup and Usage

### 1. Prerequisites
* Git
* Python 3.9+
* A CUDA-enabled NVIDIA GPU

### 2. Clone the Repository
```bash
git clone [https://github.com/Cruciator18/gpt-decoder-only.git](https://github.com/Cruciator18/gpt-decoder-only.git)
cd gpt-decoder-only

### 3\. Create and Activate a Virtual Environment

It's highly recommended to use a virtual environment to manage dependencies.

**Create the environment**

```bash
python -m venv .venv
```

**Activate it**

```bash
# On Windows:
.\.venv\Scripts\activate

# On macOS/Linux:
source .venv/bin/activate
```

### 4\. Install Dependencies

The primary dependency, PyTorch, must be installed with a specific command to ensure CUDA compatibility.

First, visit the **[official PyTorch website](https://pytorch.org/get-started/locally/)** to get the correct command for your system. For example, for CUDA 12.1:

```bash
pip3 install torch torchvision torchaudio --index-url [https://download.pytorch.org/whl/cu121](https://download.pytorch.org/whl/cu121)
```

Then, install the other packages from `requirements.txt`:

```bash
pip install -r requirements.txt
```

### 5\. Run the Training Script

Simply execute the Python script to start training the model.

```bash
python train.py
```

-----

## Training Log

The model was trained for 5000 steps. The following log shows the training and validation loss at various checkpoints.

  * **Device Used**: `cuda`
  * **Automatic Mixed Precision**: `True`
  * **Total Parameters**: `3.26M`

<!-- end list -->

```
step 0: train loss 4.2584, val loss 4.2571
step 500: train loss 1.7309, val loss 1.8834
step 1000: train loss 1.4422, val loss 1.6569
step 1500: train loss 1.3401, val loss 1.5700
step 2000: train loss 1.2796, val loss 1.5429
step 2500: train loss 1.2379, val loss 1.5104
step 3000: train loss 1.2039, val loss 1.4940
step 3500: train loss 1.1717, val loss 1.4819
step 4000: train loss 1.1479, val loss 1.4786
step 4500: train loss 1.1240, val loss 1.4735
step 4999: train loss 1.1093, val loss 1.4804
```

-----

## Example Output

Here is a sample of text generated by the model after training for 5000 steps:

```
the most great Duke of Alas, bestideedessed in parloabm
on. Go to Hermiony lief to Restason,
But to have vise again very prophetul shertors,
And put healt, to rest in deay and next,
Parogr, that marful wurder coupls that she conceives;
That how taughts in their swer our lean--
God gentle probaben in Salisbury;
Then, till reties an happy franther furmwerful tols!
Didst thou a fearful king?

EDWARD:
For John pider I all beared, and in heavior hand,
And rob our raven, unquer'd the breacing sweed.

Sof
ISTBUSHY:
Ay, the devices Shallow them no bear with them.
What shall I be speak?

KING HENRY VI:
Wemet Xary souls? al's quickled death:
Home made 'when in time a quent, brothers,
And he'll more hur own harm, by's head
'Twere the physicial to fully dost of you.'

Clown:
Oh appeal of a warledge doined preyes! Caese confoine.
```

-----

## Acknowledgements

  * This project is heavily inspired by Andrej Karpathy's amazing work on **[nanoGPT](https://github.com/karpathy/nanoGPT)**.
  * The architecture is based on the original Transformer paper: **[Attention Is All You Need](https://arxiv.org/abs/1706.03762)**.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

```
```

