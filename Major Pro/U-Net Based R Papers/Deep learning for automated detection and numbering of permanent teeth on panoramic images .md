## Deep learning for automated detection and numbering of permanent teeth on panoramic images 

Dentomaxillofacial Radiology, Volume 51, Issue 2, 1 February 2022, 20210296, https://doi.org/10.1259/dmfr.20210296

> https://academic.oup.com/dmfr/article/51/2/20210296/7261254?login=true

[text](<Deep learning for automated detection and numbering of permanent teeth on panoramic images _ Dentomaxillofacial Radiology _ Oxford Academic.pdf>)

### SUMMARY :
In total, 591 digital OPGs were collected from patients older than 18 years. Three qualified dentists performed individual teeth labelling on images to generate the ground truth annotations. A three-step procedure, relying upon CNNs, was proposed for automated detection and classification of teeth. Firstly, U-Net, a type of CNN, performed preliminary segmentation of tooth regions or detecting regions of interest (ROIs) on panoramic images. Secondly, the Faster R-CNN, an advanced object detection architecture, identified each tooth within the ROI determined by the U-Net. Thirdly, VGG-16 architecture classified each tooth into 32 categories, and a tooth number was assigned. A total of 17,135 teeth cropped from 591 radiographs were used to train and validate the tooth detection and tooth numbering modules. 90% of OPG images were used for training, and the remaining 10% were used for validation. 10-folds cross-validation was performed for measuring the performance. The intersection over union (IoU), F1 score, precision, and recall (i.e. sensitivity) were used as metrics to evaluate the performance of resultant CNNs.



> The ROI detection module had an IoU of 0.70. The tooth detection module achieved a recall of 0.99 and a precision of 0.99. The tooth numbering module had a recall, precision and F1 score of 0.98.



