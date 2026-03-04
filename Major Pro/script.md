## PAGE 1
- Dental radiographic imaging plays a very important role in modern dentistry. It helps dentists in diagnosis, treatment planning, and monitoring oral health.
- panoramic radiographs provide a complete view of the teeth and jaw structures in a single image.

- enumeration, which means the accurate identification and numbering of teeth. 
- This is essential for dental charting, disease detection, orthodontic planning, and surgical procedures.

- However, the traditional manual method of numbering teeth can be time-consuming and prone to errors, especially when teeth are missing, overlapping, or have anatomical variations.

- To address this problem, our project proposes a deep learning–based approach that performs automatic tooth segmentation and enumeration, and validates the results using the FDI numbering system to ensure accurate and clinically reliable identification of teeth.”

## PAGE 2
- The Fédération Dentaire Internationale, or FDI numbering system, is an internationally accepted standard used to identify and number human teeth.
- In this system, each tooth is represented by a two-digit number.
    - The first digit indicates the quadrant of the mouth:
        - 1 represents the upper right quadrant,
        - 2 represents the upper left,
        - 3 represents the lower left, and
        - 4 represents the lower right quadrant.
    - The second digit indicates the position of the tooth within that quadrant.
- The numbering starts from the midline of the mouth, where 1 represents the central incisor, and continues up to 8, which represents the third molar.

## PAGE 3
- Image segmentation is the process of dividing an image into meaningful regions so that important structures can be analyzed separately.
    - In the case of dental X-ray images, segmentation works by examining each pixel in the image and determining whether it belongs to a tooth or the background. This helps in clearly separating each tooth from surrounding structures.
- By grouping together all the pixels that belong to the same tooth, segmentation allows us to identify the shape and boundaries of each tooth more accurately.
- As shown in the figure on the right, each tooth is individually highlighted with different colors, demonstrating how segmentation isolates each tooth for better analysis.”


## PAGE 8
- First, there is a segmentation–enumeration gap.
Many existing studies achieve high accuracy in tooth segmentation, but accurate segmentation alone does not guarantee correct tooth numbering. In many cases, the actual identity and order of teeth are not properly enforced.

- Second, there is a lack of anatomical validation based on FDI rules.
Several approaches perform numbering but do not strictly follow anatomical constraints, such as correct quadrant identification, jaw separation, and left–right ordering, which may lead to incorrect dental charts.

- Third, many methods rely on heuristic enumeration approaches.
These approaches use techniques like bounding-box overlap or IoU matching, which may fail when teeth are overlapping, missing, or distorted in panoramic radiographs.

- Another important issue is missing tooth handling.
- Most existing methods do not explicitly detect or validate missing teeth, even though missing teeth are very common in real clinical scenarios.

- Finally, many studies focus only on pixel-level evaluation metrics, such as Dice score, IoU, precision, and recall.
- However, these metrics do not fully reflect clinical usefulness, since metrics like per-tooth numbering accuracy or complete dental chart correctness are rarely evaluated.
- These limitations highlight the need for a more reliable system that combines segmentation with anatomically consistent dental enumeration.”


## PAGE 9 :
- Most existing deep learning approaches for panoramic dental radiographs mainly focus on tooth detection or segmentation. While these methods can successfully identify the tooth regions, they do not always guarantee anatomically correct dental numbering.
- In particular, many models fail to ensure FDI-compliant dental enumeration, especially in challenging situations such as missing teeth, overlapping teeth, or irregular dental structures.
- Because of this limitation, there is a need for a more reliable and automated framework.

- Our work aims to address this challenge by developing a system that combines segmentation with anatomically validated dental enumeration.”

