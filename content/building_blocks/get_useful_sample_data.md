---
sidebar_label: Get useful sample data
filename: get_useful_sample_data.md
---
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';


<!-- TABS -->
# Get useful sample data


<Tabs>
    <TabItem value="Text" label="Text" default>
        ```python
        !curl -O https://superduper-public-demo.s3.amazonaws.com/text.json
        import json
        
        with open('text.json', 'r') as f:
            data = json.load(f)        
        ```
    </TabItem>
    <TabItem value="Text-Classification" label="Text-Classification" default>
        ```python
        !curl -O https://superduper-public-demo.s3.amazonaws.com/text_classification.json
        import json
        
        with open("text_classification.json", "r") as f:
            data = json.load(f)
        num_classes = 2        
        ```
    </TabItem>
    <TabItem value="PDF" label="PDF" default>
        ```python
        !curl -O https://superduper-public-demo.s3.amazonaws.com/pdfs.zip && unzip -o pdfs.zip
        import os
        
        data = [f'pdfs/{x}' for x in os.listdir('./pdfs') if x.endswith('.pdf')]        
        ```
    </TabItem>
    <TabItem value="Image" label="Image" default>
        ```python
        !curl -O https://superduper-public-demo.s3.amazonaws.com/images.zip && unzip images.zip
        import os
        from PIL import Image
        
        data = [f'images/{x}' for x in os.listdir('./images') if x.endswith(".png")][:200]
        data = [ Image.open(path) for path in data]        
        ```
    </TabItem>
    <TabItem value="Image-Classification" label="Image-Classification" default>
        ```python
        !curl -O https://superduper-public-demo.s3.amazonaws.com/images_classification.zip && unzip images_classification.zip
        import json
        from PIL import Image
        
        with open('images/images.json', 'r') as f:
            data = json.load(f)
        
        data = [{'x': Image.open(d['image_path']), 'y': d['label']} for d in data]
        num_classes = 2        
        ```
    </TabItem>
    <TabItem value="Video" label="Video" default>
        ```python
        !curl -O https://superduper-public-demo.s3.amazonaws.com/videos.zip && unzip videos.zip
        import os
        
        data = [f'videos/{x}' for x in os.listdir('./videos')]
        sample_datapoint = data[-1]
        
        from superduper.ext.pillow import pil_image
        chunked_model_datatype = pil_image        
        ```
    </TabItem>
    <TabItem value="Audio" label="Audio" default>
        ```python
        # !curl -O https://superduper-public-demo.s3.amazonaws.com/audio.zip && unzip audio.zip
        import os
        
        data = [f'audios/{x}' for x in os.listdir('./audio')]
        sample_datapoint = data[-1]        
        ```
    </TabItem>
</Tabs>
