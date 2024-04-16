# Posture_Correction
The program uses MediaPipe's Pose estimation capabilities to analyze the person's posture by examining the alignment of specific body parts. 

# Libraries and Initialization:
### MediaPipe and OpenCV: 
These libraries are crucial for the program. OpenCV is used for image processing and GUI operations, while MediaPipe provides robust tools for pose estimation.
### MediaPipe Pose:
Initialized with static_image_mode=True and model_complexity=2, settings optimal for image analysis (as opposed to real-time video), providing more accurate pose detection.
### Function Definitions:
calculate_angle(a, b, c):

### Purpose:
Calculates the angle between three points, which are inputs as 2D coordinates representing (x, y) positions. This is used to determine the geometric relationship between different body landmarks.
### Method: 
Utilizes the arctangent function to find the angle at point b, formed between lines ab and bc. The calculation accounts for any angle over 180 degrees, converting it to a more intuitive measure (e.g., turning 270 degrees into 90 degrees).

### Image Loading and Processing:
The function starts by loading an image from the provided image_path and converting it to RGB for MediaPipe processing.
### Pose Detection:
MediaPipe processes the image and extracts pose landmarks, which are predefined points on the body that the model has been trained to recognize.
# Points for Posture Analysis:
### Ear:
Represents the top of the head, used as the uppermost point in posture evaluation.
### Shoulder:
Serves as a midpoint in the upper body, crucial for evaluating the tilt and alignment of the torso.
### Hip:
Acts as a lower reference point, essential for assessing the curvature and alignment of the spine in a seated posture.
### Angle Calculation:
The angle between the ear, shoulder, and hip is calculated using the calculate_angle function. This angle helps to assess the spinal alignment and the tilt of the head relative to the shoulders.
### Posture Evaluation:
The angle is then used to determine posture quality:
#### Good Posture: Defined as an angle greater than 160 degrees, suggesting a relatively straight back and proper head alignment.
#### Bad Posture: An angle less than 160 degrees indicates potential slouching or improper head tilt, which can lead to strain or discomfort.
### Annotation:
The image is annotated with the calculated angle and the determined posture status, providing visual feedback on the posture analysis
