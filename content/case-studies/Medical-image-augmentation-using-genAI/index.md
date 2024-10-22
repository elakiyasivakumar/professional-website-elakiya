---
title: Data Augmentation methods using Generative-AI
authors:
  - admin
  - Dr K Nirmala, SSN Biomedical Engineering
  - Anjana Anand
tags:
  - Gen AI
  - Medical Images
  - Markdown
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com)'
---
### Aim

Deep Learning methods require large datasets to overcome overfitting and class generalization problems.
Well-annotated and sufficient datasets are expensive economically and computationally to produce and store - problem is especially aggravated in the biomedical field. 

Our main aim to do this project came from trying to apply segmentation techniques to medical image datasets but realizing we simply did not have enough data to train the models with! 

We decided to then focus on augmentation techniques for medical image datasets! 


### Dataset - VinDr SpineXR Dataset

- Large-scale annotated medical image dataset for spinal lesion detection and classification from radiographs. 
- Contains 10,466 spine X-ray images from 5,000 studies, each of which is manually annotated with 13 types of abnormalities by an experienced radiologist.
Lesion types: (1) Ankylosis, (2) Disc space narrowing, (3) Enthesophytes, (4) Foraminal stenosis, (5) Fracture, (6) Osteophytes, (7) Sclerotic lesion, (8) Spondylolysthesis, (9) Subchondral sclerosis, (10) Surgical implant, (11) Vertebral collapse, (12) Foreign body, and (13) Other lesions.

We mainly selected the dataset because of the significant class variance and class imbalance. There is about 13 different types of diseases and all the disease-types have only 100-200 images each.


</code>
</pre>
</div>

renders as

```markmap
- Mindmaps
  - Links
    - [Hugo Blox Docs](https://docs.hugoblox.com/)
    - [Discord Community](https://discord.gg/z8wNYzb)
    - [GitHub](https://github.com/HugoBlox/hugo-blox-builder)
  - Features
    - Markdown formatting
    - **inline** ~~text~~ *styles*
    - multiline
      text
    - `inline code`
    -
      ```js
      console.log('hello');
      console.log('code block');
      ```
    - Math: $x = {-b \pm \sqrt{b^2-4ac} \over 2a}$
```

## Highlighting

<mark>Highlight</mark> important text with `mark`:

```html
<mark>Highlighted text</mark>
```

## Callouts

Use [callouts](https://docs.hugoblox.com/reference/markdown/#callouts) (aka _asides_, _hints_, or _alerts_) to draw attention to notes, tips, and warnings.

By wrapping a paragraph in `{{%/* callout note */%}} ... {{%/* /callout */%}}`, it will render as an aside.

```markdown
{{%/* callout note */%}}
A Markdown aside is useful for displaying notices, hints, or definitions to your readers.
{{%/* /callout */%}}
```

renders as

{{% callout note %}}
A Markdown aside is useful for displaying notices, hints, or definitions to your readers.
{{% /callout %}}

Or use the `warning` callout type so your readers don't miss critical details:

{{% callout warning %}}
A Markdown aside is useful for displaying notices, hints, or definitions to your readers.
{{% /callout %}}

## Did you find this page helpful? Consider sharing it 🙌
