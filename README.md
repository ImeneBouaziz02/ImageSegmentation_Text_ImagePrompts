# Image Segmentation Using Text and Image Prompts - CLIPSeg

## 📋 Project Overview

This repository documents my research project on **CLIPSeg** by Timo Lüddecke and Alexander Ecker from the University of Göttingen. The project involved:

- 📖 Reading and comprehending the research paper
- 💻 Running the original code and models
- 🎯 Understanding the problem, solution, and architecture
- 🎨 Creating an AI-generated presentation (using Gamma)
- 🚀 Demonstrating the model’s performance on example datasets

**Project Duration:** ~20 hours

## 🎯 Problem Statement

Traditional image segmentation methods require:

- Large amounts of labeled training data for each new class
- Expensive annotation processes
- Separate models for different segmentation tasks

**CLIPSeg solves this by enabling zero-shot and one-shot image segmentation using natural language descriptions or reference images as prompts.**

## 💡 Proposed Solution

CLIPSeg extends CLIP (Contrastive Language-Image Pre-training) to perform image segmentation by:

1. **Text-based prompts**: Segment objects described in natural language
   - Examples: "cat", "tree"
2. **Image-based prompts**: Segment objects similar to a reference image

   - Example: Show a picture of a specific object to find similar objects

3. **Zero-shot capability**: Segment novel object categories without additional training

## 🏗️ Architecture

### Core Components

```
Input Image → CLIP Visual Encoder → Feature Maps
                                         ↓
Text/Image Prompt → CLIP Encoder → Conditioning Vector
                                         ↓
                              Decoder (FiLM layers)
                                         ↓
                              Segmentation Mask
```

**Key Technical Details:**

- **Backbone**: CLIP ViT-B/16 or RN50x4
- **Decoder**: Transformer-based with FiLM (Feature-wise Linear Modulation) layers
- **Input Resolution**: 352×352 pixels
- **Output**: Binary or multi-class segmentation masks

## 📊 Datasets Used

The authors trained and evaluated CLIPSeg on:

1. **PhraseCut** - 340k referring expressions for image regions
2. **COCO-Stuff** - 164k images with dense annotations
3. **Pascal VOC 2012** - Semantic segmentation benchmark
4. **Pascal Context** - Extended Pascal VOC annotations

**Evaluation datasets for zero-shot:**

- FSS-1000: Few-shot segmentation
- PASCAL-5i: Few-shot semantic segmentation

## 🚀 Getting Started

### Prerequisites

```bash
# Python 3.8+
pip install torch torchvision
pip install transformers
pip install opencv-python
pip install matplotlib
pip install Pillow
```

### Installation

```bash
# Clone the original repository
git clone https://github.com/timojl/clipseg.git
cd clipseg

# Download pre-trained weights
wget https://owncloud.gwdg.de/index.php/s/ioHbRzFx6th32hn/download -O weights.zip
unzip weights.zip
```

## 🎬 Demo Results

Please view the demo video in the [`results`](./results) folder.

## 📈 Key Results

From the paper:

- **Zero-shot Performance**: Competitive with supervised methods on Pascal VOC
- **PhraseCut Accuracy**: 61.5% mIoU
- **Generalization**: Strong performance on unseen categories
- **Flexibility**: Works with both text and image prompts

### Qualitative Observations

✅ **Strengths:**

- No training data needed for new categories
- Natural language interface
- Handles complex, compositional queries
- Fast inference

⚠️ **Limitations:**

- Lower resolution than some specialized models
- Performance depends on CLIP's understanding
- May struggle with very fine-grained details

## 🎓 Presentation

The presentation was 100% AI-generated using **Gamma.app**.
Please view the [`presentation`](./presentation) folder.

## 🎯 Key Takeaways

### Technical Insights

- **CLIP's Power**: Pre-trained vision-language models enable powerful zero-shot capabilities
- **FiLM Conditioning**: Effective way to incorporate multimodal conditioning
- **Trade-offs**: Flexibility vs. precision in segmentation tasks

### Research Skills Developed

- Reading and understanding academic papers
- Reproducing research results
- Running pre-trained models
- Creating technical presentations
- Explaining complex concepts clearly

## ⚙️ Key Takeaways

### Tools & Technologies

- **Python, PyTorch**
- **CLIP, OpenAI embeddings**
- **Gamma (AI presentation generator)**
- **Google Colab / Local GPU**
- **Git, GitHub**

## 📚 References

```bibtex
@inproceedings{lueddecke2022clipseg,
  title={Image Segmentation Using Text and Image Prompts},
  author={L{\"u}ddecke, Timo and Ecker, Alexander},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  pages={7086--7096},
  year={2022}
}
```

**Original Paper**: [arXiv:2112.10003](https://arxiv.org/abs/2112.10003)  
**Original Code**: [github.com/timojl/clipseg](https://github.com/timojl/clipseg)
