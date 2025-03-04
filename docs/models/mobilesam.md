---
comments: true
description: Discover the Segment Anything Model (SAM), a revolutionary promptable image segmentation model, and delve into the details of its advanced architecture and the large-scale SA-1B dataset.
keywords: Segment Anything, Segment Anything Model, SAM, Meta SAM, image segmentation, promptable segmentation, zero-shot performance, SA-1B dataset, advanced architecture, auto-annotation, Ultralytics, pre-trained models, SAM base, SAM large, instance segmentation, computer vision, AI, artificial intelligence, machine learning, data annotation, segmentation masks, detection model, YOLO detection model, bibtex, Meta AI
---

# Segment Anything Model (SAM)

Welcome to the frontier of image segmentation with the Segment Anything Model, or SAM. This revolutionary model has changed the game by introducing promptable image segmentation with real-time performance, setting new standards in the field.

## Introduction to SAM: The Segment Anything Model

The Segment Anything Model, or SAM, is a cutting-edge image segmentation model that allows for promptable segmentation, providing unparalleled versatility in image analysis tasks. SAM forms the heart of the Segment Anything initiative, a groundbreaking project that introduces a novel model, task, and dataset for image segmentation.

SAM's advanced design allows it to adapt to new image distributions and tasks without prior knowledge, a feature known as zero-shot transfer. Trained on the expansive [SA-1B dataset](https://ai.facebook.com/datasets/segment-anything/), which contains more than 1 billion masks spread over 11 million carefully curated images, SAM has displayed impressive zero-shot performance, surpassing previous fully supervised results in many cases.

![Dataset sample image](https://user-images.githubusercontent.com/26833433/238056229-0e8ffbeb-f81a-477e-a490-aff3d82fd8ce.jpg)
Example images with overlaid masks from our newly introduced dataset, SA-1B. SA-1B contains 11M diverse, high-resolution, licensed, and privacy protecting images and 1.1B high-quality segmentation masks. These masks were annotated fully automatically by SAM, and as verified by human ratings and numerous experiments, are of high quality and diversity. Images are grouped by number of masks per image for visualization (there are ∼100 masks per image on average).

## Key Features of the Segment Anything Model (SAM)

- **Promptable Segmentation Task:** SAM was designed with a promptable segmentation task in mind, allowing it to generate valid segmentation masks from any given prompt, such as spatial or text clues identifying an object.
- **Advanced Architecture:** The Segment Anything Model employs a powerful image encoder, a prompt encoder, and a lightweight mask decoder. This unique architecture enables flexible prompting, real-time mask computation, and ambiguity awareness in segmentation tasks.
- **The SA-1B Dataset:** Introduced by the Segment Anything project, the SA-1B dataset features over 1 billion masks on 11 million images. As the largest segmentation dataset to date, it provides SAM with a diverse and large-scale training data source.
- **Zero-Shot Performance:** SAM displays outstanding zero-shot performance across various segmentation tasks, making it a ready-to-use tool for diverse applications with minimal need for prompt engineering.

For an in-depth look at the Segment Anything Model and the SA-1B dataset, please visit the [Segment Anything website](https://segment-anything.com) and check out the research paper [Segment Anything](https://arxiv.org/abs/2304.02643).

## How to Use SAM: Versatility and Power in Image Segmentation

The Segment Anything Model can be employed for a multitude of downstream tasks that go beyond its training data. This includes edge detection, object proposal generation, instance segmentation, and preliminary text-to-mask prediction. With prompt engineering, SAM can swiftly adapt to new tasks and data distributions in a zero-shot manner, establishing it as a versatile and potent tool for all your image segmentation needs.

```python
from ultralytics import MobileSAM

model = MobileSAM('mobile_sam.pt')
model.info()  # display model information
model.predict('path/to/image.jpg')  # predict
```

## Available Models and Supported Tasks

| Model Type | Pre-trained Weights | Tasks Supported       |
|------------|---------------------|-----------------------|
| SAM base   | `mobile_sam.pt`          | Instance Segmentation |

## Operating Modes

| Mode       | Supported          |
|------------|--------------------|
| Inference  | :heavy_check_mark: |
| Validation | :x:                |
| Training   | :x:                |

## Auto-Annotation: A Quick Path to Segmentation Datasets

Auto-annotation is a key feature of SAM, allowing users to generate a [segmentation dataset](https://docs.ultralytics.com/datasets/segment) using a pre-trained detection model. This feature enables rapid and accurate annotation of a large number of images, bypassing the need for time-consuming manual labeling.

### Generate Your Segmentation Dataset Using a Detection Model

To auto-annotate your dataset with the Ultralytics framework, use the `auto_annotate` function as shown below:

```python
from ultralytics.yolo.data.annotator import auto_annotate

auto_annotate(data="path/to/images", det_model="yolov8x.pt", sam_model='sam_b.pt')
```

| Argument   | Type                | Description                                                                                             | Default      |
|------------|---------------------|---------------------------------------------------------------------------------------------------------|--------------|
| data       | str                 | Path to a folder containing images to be annotated.                                                     |              |
| det_model  | str, optional       | Pre-trained YOLO detection model. Defaults to 'yolov8x.pt'.                                             | 'yolov8x.pt' |
| sam_model  | str, optional       | Pre-trained SAM segmentation model. Defaults to 'sam_b.pt'.                                             | 'sam_b.pt'   |
| device     | str, optional       | Device to run the models on. Defaults to an empty string (CPU or GPU, if available).                    |              |
| output_dir | str, None, optional | Directory to save the annotated results. Defaults to a 'labels' folder in the same directory as 'data'. | None         |

The `auto_annotate` function takes the path to your images, with optional arguments for specifying the pre-trained detection and SAM segmentation models, the device to run the models on, and the output directory for saving the annotated results.

Auto-annotation with pre-trained models can dramatically cut down the time and effort required for creating high-quality segmentation datasets. This feature is especially beneficial for researchers and developers dealing with large image collections, as it allows them to focus on model development and evaluation rather than manual annotation.

## Citations and Acknowledgements

If you find SAM useful in your research or development work, please consider citing our paper:

```bibtex
@article{mobile_sam,
  title={Faster Segment Anything: Towards Lightweight SAM for Mobile Applications},
  author={Zhang, Chaoning and Han, Dongshen and Qiao, Yu and Kim, Jung Uk and Bae, Sung Ho and Lee, Seungkyu and Hong, Choong Seon},
  journal={arXiv preprint arXiv:2306.14289},
  year={2023}
}
```

We would like to express our gratitude to Meta AI for creating and maintaining this valuable resource for the computer vision community.

*keywords: Segment Anything, Segment Anything Model, SAM, Meta SAM, image segmentation, promptable segmentation, zero-shot performance, SA-1B dataset, advanced architecture, auto-annotation, Ultralytics, pre-trained models, SAM base, SAM large, instance segmentation, computer vision, AI, artificial intelligence, machine learning, data annotation, segmentation masks, detection model, YOLO detection model, bibtex, Meta AI.*
