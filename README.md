# OBJECT DETECTION BY YOLO11s.

## YOLO 11.

**1) Introduction**


YOLOv11 is the latest generation in the YOLO (You Only Look Once) family of real-time object detection 

models, developed by Ultralytics. It’s designed to detect and classify objects in images or video streams 

extremely fast while keeping high accuracy—making it ideal for things like surveillance, autonomous 

driving, robotics, and mobile apps.

**2) Here’s the quick idea:**


•	Single-pass detection: Like earlier YOLO versions, YOLOv11 looks at the whole image once and predicts bounding boxes + classes in one shot. 

•	Improved speed vs accuracy: It refines the architecture to be lighter and more efficient than YOLOv8, especially on GPUs and edge devices. 

•	Better training flexibility: Supports detection, segmentation, pose estimation, and classification in one framework. 

•	Edge-friendly: Runs well on smaller hardware (Jetson, mobile, etc.). 
In short: YOLOv11 = faster + more accurate + more versatile real-time object detection.

If you tell me what you're using it for (e.g., drones, CCTV, Python project), I can explain it in that context.


### 3) Questions:
# Qno1 How to run Yolo 11 on our local computer?


**Ans** To run YOLOv11 on your local computer, the easiest way is using Ultralytics’ Python package. Here’s the simplest step-by-step.


**1. Install Python (if not already)**

Use Python 3.9–3.12 (recommended)

Check:

python --version


**2. Create a virtual environment (recommended)**

python -m venv yolo11

*Activate:*

Windows

yolo11\Scripts\activate

Mac/Linux

source yolo11/bin/activate

**3. Install YOLOv11**

pip install ultralytics

This installs YOLOv11 automatically.

**4. Run YOLOv11 on an image**

from ultralytics import YOLO

model = YOLO("yolo11n.pt")  # nano model (fastest)

results = model("image.jpg", show=True)

That’s it — it will open a window with detected objects.

**5. Run from command line (even easier)**

yolo detect predict model=yolo11n.pt source=image.jpg

**6. Use webcam (real-time detection)**

from ultralytics import YOLO

model = YOLO("yolo11n.pt")

model.predict(source=0, show=True)

0 = webcam

Model sizes

You can choose:

•	yolo11n.pt — fastest (low accuracy) 

•	yolo11s.pt — small 

•	yolo11m.pt — medium 

•	yolo11l.pt — large 

•	yolo11x.pt — best accuracy (slowest) 

GPU (optional but faster)

If you have NVIDIA GPU:

pip install torch torchvision --index-url https://download.pytorch.org/whl/cu121

YOLO will automatically use GPU.


# Qno2 What can we do with the help of YOLO 11?


**Ans** With the help of YOLO 11, we can do object detection, image segmentation, pose estimation, and image classification. We can perform all these tasks with YOLO 11.


# Qno3 How to setup environment on local pcs or laptops?


**Ans** Setting up a Python virtual environment on your local computer is a good habit — it keeps projects like YOLOv11 separate and avoids dependency conflicts. Here’s the simplest way.

**Step 1 — Install Python**

Download and install Python from Python official site.

During install, check "Add Python to PATH".

Check installation:

python –version

**Step 2 — Create a virtual environment**

Open terminal / CMD in your project folder:

python -m venv myenv

This creates a folder named myenv.

**Step 3 — Activate the environment**

Windows (CMD / PowerShell)

myenv\Scripts\activate

Mac / Linux

source myenv/bin/activate

When activated, you’ll see:

(myenv) C:\your\folder>

That means the environment is active.

**Step 4 — Install packages inside env**

Example:

pip install ultralytics

This installs packages only inside this environment.


# Qno4 How to run yolo v11 on computers locally and pretrained models?


**Ans** Running YOLOv11 locally is pretty straightforward once you know the pieces: install Python + 

Ultralytics, download a pretrained model, then run inference on images/video. Here’s the clean, working path.

**1. What “YOLOv11 locally” means**

You run object detection on your own PC using pretrained weights like:

•	yolo11n.pt (fastest, smallest) 

•	yolo11s.pt 

•	yolo11m.pt 

•	yolo11l.pt 

•	yolo11x.pt (most accurate, heavy) 

These come from the Ultralytics YOLO package.

**2. Run YOLOv11 with pretrained model (image)**

yolo predict model=yolo11n.pt source=img.jpg

It will:

•	auto download pretrained model 

•	detect objects 

•	save output in runs/detect/predict 

**3. Python code version**

from ultralytics import YOLO

**load pretrained model**

model = YOLO("yolo11n.pt")

**run inference**

results = model("image.jpg", show=True)

**save results**

results[0].save("output.jpg")

**4. Run on webcam**

yolo predict model=yolo11n.pt source=0

or Python:

from ultralytics import YOLO

model = YOLO("yolo11n.pt")

model.predict(source=0, show=True)

**5. Run on video**

yolo predict model=yolo11n.pt source=video.mp4

**6. Run on folder of images**

yolo predict model=yolo11n.pt source=images/

**7. Available pretrained models**

Common ones:

yolo11n.pt   (nano - fastest)

yolo11s.pt   (small)

yolo11m.pt   (medium)

yolo11l.pt   (large)

yolo11x.pt   (extra large - best accuracy)

They automatically download first time you run them.

**8. GPU acceleration (important)**

If you have NVIDIA GPU:

Install CUDA PyTorch:

pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121

Then run:

model = YOLO("yolo11n.pt")

model.to("cuda")

**9. Where pretrained models come from**

They’re trained on:

•	COCO dataset (80 classes) 

•	People, cars, phones, animals, etc. 

*Example detections:*

•	person 

•	car 

•	truck 

•	dog 

•	phone 

•	laptop 

**10. Check YOLOv11 is working**

Run:

yolo

You should see CLI help.

**11. Folder structure after running**

project/
 ├── image.jpg
 ├── runs/
     └── detect/
          └── predict/
               └── image.jpg

               
# Qno5 What is the image classification?


**Ans** Image classification means:

The model looks at the whole image and predicts one label for it.

Example:
•	input → picture of a cat 

•	output → "cat" 

No boxes, no locations — just what is in the image.

Compared to others (very important)

**1. Image Classification**

•	One label for entire image 

•	Example: "dog" 

•	No bounding box 

**2. Object Detection (what you're using with YOLO)**

•	Finds multiple objects 

•	Draws bounding boxes 

•	Example: "person", "car", "dog" with rectangles 

**3. Segmentation**

•	Pixel-level detection 

•	Colors exact shape of object 

Simple visual idea

Image classification:

[ image of street ]

Prediction: "street"

Object detection:

[ person ] [ car ] [ dog ]

   box        box     box

Your code using YOLOv8 = Object Detection, not classification.

If you want classification, code looks like:

from ultralytics import YOLO

import cv2

model = YOLO("yolov8n-cls.pt")   # classification model

img = cv2.imread("image.jpg")

results = model(img)

print(results[0].probs.top1)

print(results[0].names[results[0].probs.top1])

This prints only one class.

So:

•	YOLO detect boxes → Object Detection 

•	YOLO cls model → Image Classification


# Qno6 What is the computer vision?


**Ans** Computer Vision is a field of Artificial Intelligence that teaches computers to see, understand, and interpret images or videos the way humans do.

In simple words:

It’s how a machine “looks at pictures or videos and understands what’s inside them.”

What it allows computers to do

  Computer vision can help a system:

•	recognize objects (car, person, dog) 

•	detect faces (face unlock on phones) 

•	read text in images (OCR like scanning documents) 

•	track movement in videos (security cameras) 

•	understand scenes (road, sky, buildings) 

Simple example

If you show an image:

A photo of a street with cars and people

A computer vision model might output:

•	Person → detected 

•	Car → detected 

•	Traffic light → detected 

How it works (basic idea)

**1**	Input: image or video 

**2**	Processing: AI model analyzes patterns (edges, shapes, colors) 

**3**	Output: labels, boxes, or decisions 

Real-world uses

•	 Face unlock in smartphones 

•	 Self-driving cars 

•	 Medical X-ray detection 

•	 Amazon Go cashier-less stores 

•	YOLO object detection (what you're using) 


# Qno7 What what we can do in the field in computer vision?


**Ans** Computer Vision is a field of Artificial Intelligence that teaches computers to see, understand, and interpret images or videos the way humans do.

In simple words:

 It’s how a machine “looks at pictures or videos and understands what’s inside them.”
 
 What it allows computers to do

Computer vision can help a system:

•	recognize objects (car, person, dog) 

•	detect faces (face unlock on phones) 

•	read text in images (OCR like scanning documents) 

•	track movement in videos (security cameras) 

•	understand scenes (road, sky, buildings) 

Simple example

If you show an image:

A photo of a street with cars and people

A computer vision model might output:

•	Person → detected 

•	Car → detected 

•	Traffic light → detected 

 How it works (basic idea)

**1**	Input: image or video 

**2**	Processing: AI model analyzes patterns (edges, shapes, colors) 

**3**	Output: labels, boxes, or decisions 
 
 Real-world uses

•	 Face unlock in smartphones 

•	 Self-driving cars 

•	 Medical X-ray detection 

•	 Amazon Go cashier-less stores 

•	 YOLO object detection (what you're using) 

**1** Software Development (Apps & Websites)

You build things people use every day.

•	Websites (like YouTube, Amazon) 

•	Mobile apps (Android / iOS) 

•	Desktop software 

 Example:

•	WhatsApp, Instagram, banking apps 

Skills:

•	Python / JavaScript / Java 

**2** Artificial Intelligence (AI)

You make computers “think smart”.

•	Chatbots (like ChatGPT) 

•	Image recognition (YOLO, face detection) 

•	Recommendation systems (Netflix, YouTube) 

 Example:

•	Your YOLO object detection project is AI 

Skills:

•	Python, Machine Learning, Deep Learning 

**3** Computer Vision

You make computers see and understand images/videos

•	Object detection (YOLO) 

•	Face recognition 

•	Self-driving cars 

•	Medical imaging 

 Example:

•	CCTV detecting people 

•	Car detecting pedestrians 

 **4** Data Science

You work with data to find patterns and predictions.

•	Business analytics 

•	Stock prediction 

•	Customer behavior 

 Example:

•	Netflix recommending movies 

Skills:
•	Python, Pandas, Statistics 

**5** Networking & Cybersecurity

You protect computers and data.

•	Hacking protection 

•	Cyber attacks prevention 

•	Network security 

 Example:

•	Banks protecting accounts from hackers 

**6** Game Development

You build games.

•	PC games 

•	Mobile games 

•	3D simulations 

 Example:

•	PUBG, GTA, Free Fire 

**7** Hardware / Robotics

You work with physical machines.

•	Robots 

•	IoT devices 

•	Automation systems 

 Example:

•	Smart home systems 

•	Factory robots 

 Simple summary

Computer field = many paths:

•	 Build apps → Software Dev 

•	 Make AI → Machine Learning 

•	 Make machines see → Computer Vision 

•	 Work with data → Data Science 

•	 Secure systems → Cybersecurity 

•	 Build games → Game Dev


# Qno8 If you want to create your own custom object detection model, how do you prepare its dataset?


**Ans** To create your custom object detection model, dataset preparation has 4 main steps:


**1** Collect Images

You need images containing the objects you want to detect.

Example:

•	cars 

•	helmets 

•	people 

•	animals 

Dataset example:

images/

   img1.jpg
   
   img2.jpg
   
   img3.jpg

Rules:

•	different angles 

•	different lighting 

•	different sizes 

•	different backgrounds 

More variety = better model

**2** Annotate (Draw Bounding Boxes)

You must draw boxes around objects and assign labels.

Example:

[ person ]  ← box

[ helmet ]  ← box

Tools for annotation:

•	LabelImg 

•	CVAT 

•	Roboflow 

This creates label files like:

img1.txt

img2.txt

YOLO label format:

class x_center y_center width height

Example:

0 0.52 0.41 0.33 0.44

3. Folder Structure (YOLO format)

dataset/

 ├── images/
 │   ├── train/
 │   └── val/
 │
 └── labels/
     ├── train/
     └── val/

Example:

images/train/img1.jpg

labels/train/img1.txt

Names must match.

**4** Create data.yaml

path: dataset

train: images/train

val: images/val

names:

  0: person
  
  1: helmet
  
  2: car

Minimum Dataset Size

•	small test → 50 images 

•	okay model → 200 images 

•	good model → 500+ images 

•	strong model → 2000+ images 

Final Training Command

yolo detect train data=data.yaml model=yolov8n.pt epochs=50

Full Pipeline

**1**	Collect images 

**2**	Draw bounding boxes 

**3**	Save YOLO labels 

**4**	Split train / val 

**5**	Create data.yaml 

**6**	Train model


# Qno9 How to use costume dataset for training a model?


**Ans** Here is the correct minimal workflow to train a model using your custom dataset with YOLOv8.

**1** Dataset Structure (REQUIRED)

dataset/
│
├── images/
│   ├── train/
│   │   ├── img1.jpg
│   │   ├── img2.jpg
│   │
│   └── val/
│       ├── img3.jpg
│       ├── img4.jpg
│
└── labels/
    ├── train/
    │   ├── img1.txt
    │   ├── img2.txt
    │
    └── val/
        ├── img3.txt
        ├── img4.txt

Image name and label name must be same

img1.jpg → img1.txt

**2** Create data.yaml

path: dataset

train: images/train

val: images/val

names:

  0: person
  
  1: helmet
  
  2: car

**3** Train Model (Python)

from ultralytics import YOLO

model = YOLO("yolov8n.pt")

model.train(
    data="data.yaml",
    epochs=50,
    imgsz=640,
    batch=8
)

**4** Or Train Using Command Line

yolo detect train data=data.yaml model=yolov8n.pt epochs=50 imgsz=640

**5** Output Model Location

After training:

runs/detect/train/weights/best.pt

Use it like:

from ultralytics import YOLO

model = YOLO("runs/detect/train/weights/best.pt")

**6** Label Format (YOLO)

Each .txt file:

class x_center y_center width height

Example:

0 0.52 0.44 0.31 0.28

That's it.

This is the complete correct way to train using custom dataset.


# Qno10 How to perform object detection?


**Ans** To perform object detection using YOLO, you just need 3 steps:

**1** Load Model

from ultralytics import YOLO

model = YOLO("yolov8n.pt")

**2** Run Detection (image / video / webcam)

Image

import cv2

from ultralytics import YOLO

model = YOLO("yolov8n.pt")

img = cv2.imread("image.jpg")

results = model(img)

print(results)

Video (Object Detection)

from ultralytics import YOLO

import cv2

model = YOLO("yolov8n.pt")

cap = cv2.VideoCapture("video.mp4")

while True:
    ret, frame = cap.read()
    if not ret:
        break

   results = model(frame)

   annotated = results[0].plot()

   cv2.imshow("Detection", annotated)

   if cv2.waitKey(1) & 0xFF == 27:
        break

cap.release()

cv2.destroyAllWindows()

**3** Access Detection Data (boxes, class, confidence)

for r in results:

  for box in r.boxes:
    
  cls = int(box.cls[0])
        
  conf = float(box.conf[0])
        
  print(cls, conf)

What Object Detection Gives You

For each object:

•	Class name (person, car, dog) 

•	Confidence score 

•	Bounding box coordinates 

Example output:

person 0.92

car 0.88

dog 0.76

Use Your Custom Model

model = YOLO("best.pt")

Everything else stays same.

So object detection pipeline:

**1**	Load model 

**2**	Pass image/frame 

**3**	Get boxes + labels 

**4**	Draw or use result


# Qno11 How to perform custom dataset for training object detection?


**Ans** To prepare a custom dataset for object detection, follow these exact steps.

**1** Collect Images

Collect images that contain your objects.

Example:

•	helmets 

•	cars 

•	persons 

Put them in a folder:

images/
   img1.jpg
   img2.jpg
   img3.jpg

Use:

•	different angles 

•	different lighting 

•	different backgrounds 

•	different object sizes 

**2** Annotate Images (Draw Bounding Boxes)

You must draw bounding boxes around objects and assign labels.

Use tools like:

•	LabelImg 

•	CVAT 

•	Roboflow 

Example annotation:

[ person ] 

[ helmet ]

This creates label files:

img1.txt

img2.txt

**3** YOLO Label Format

Each .txt file contains:

class x_center y_center width height

Example:

0 0.50 0.42 0.30 0.28

1 0.32 0.61 0.20 0.25

Numbers are normalized (0–1).

**4** Dataset Folder Structure (IMPORTANT)

dataset/
│
├── images/
│   ├── train/
│   └── val/
│
└── labels/
    ├── train/
    └── val/

Example:

dataset/
 ├── images/train/img1.jpg
 ├── labels/train/img1.txt

Image and label names must match.

**5** Create data.yaml

path: dataset

train: images/train

val: images/val

names:

  0: person
  
  1: helmet
  
  2: car

**6** Train Model

from ultralytics import YOLO

model = YOLO("yolov8n.pt")

model.train(
    data="data.yaml",
    epochs=50,
    imgsz=640
)

Full Pipeline

**1**	Collect images 

**2**	Annotate bounding boxes 

**3**	Save YOLO labels 

**4**	Split train / val 

**5**	Create data.yaml 

**6**	Train model 

That's the complete custom object detection dataset preparation workflow.


# Qno12 How to train object detection model?


**Ans** To train an object detection model (YOLOv8), use this exact process.

**1** Dataset Structure

dataset/
│
├── images/
│   ├── train/
│   └── val/
│
└── labels/
    ├── train/
    └── val/
Example:

images/train/img1.jpg

labels/train/img1.txt

**2** Create data.yaml

path: dataset

train: images/train

val: images/val

names:
  0: person
  1: helmet
  2: car

**3** Train Model (Python)

from ultralytics import YOLO

model = YOLO("yolov8n.pt")

model.train(

  data="data.yaml",
    
  epochs=50,
  
  imgsz=640,
  
  batch=8)

**4** Train (Command Line)

yolo detect train data=data.yaml model=yolov8n.pt epochs=50 imgsz=640

**5** Training Output

After training finishes:

runs/detect/train/weights/best.pt

This is your trained object detection model.

**6** Use Trained Model

from ultralytics import YOLO

import cv2

model = YOLO("runs/detect/train/weights/best.pt")

img = cv2.imread("test.jpg")

results = model(img)

cv2.imshow("result", results[0].plot())

cv2.waitKey(0)

Training Flow

**1**	Prepare dataset 

**2**	Create data.yaml 

**3**	Load YOLO model 

**4**	Run .train() 

**5**	Get best.pt 

**6**	Use your model


# Qno13 how to perform inference using trained model?


**Ans** To perform inference using your trained YOLO model (best.pt), just load the model and pass an image/video.

**1** Inference on Image

from ultralytics import YOLO

import cv2

model = YOLO("runs/detect/train/weights/best.pt")

img = cv2.imread("test.jpg")

results = model(img)

annotated = results[0].plot()

cv2.imshow("Result", annotated)

cv2.waitKey(0)

cv2.destroyAllWindows()

**2** Inference on Video

from ultralytics import YOLO

import cv2

model = YOLO("runs/detect/train/weights/best.pt")

cap = cv2.VideoCapture("video.mp4")

while True:

ret, frame = cap.read()
    
if not ret:
    
   break

results = model(frame)
    
annotated = results[0].plot()
    
cv2.imshow("Detection", annotated)
    
   if cv2.waitKey(1) & 0xFF == 27:
        break

cap.release()

cv2.destroyAllWindows()

**3** Inference using Webcam

from ultralytics import YOLO

import cv2

model = YOLO("best.pt")

cap = cv2.VideoCapture(0)

while True:

ret, frame = cap.read()
    
if not ret:
    
  break



results = model(frame)
    
annotated = results[0].plot()
    
cv2.imshow("Webcam", annotated)
    
if cv2.waitKey(1) & 0xFF == 27:
    
   break

cap.release()

cv2.destroyAllWindows()

**4** Get Detection Values

for r in results:

for box in r.boxes:
    
cls = int(box.cls[0])
        
conf = float(box.conf[0])
        
print(cls, conf)

That’s it:

**1**	Load best.pt 

**2**	Pass image/frame 
**3**	Show results[0].plot()


# Qon14 What kind of dataset is required for object detection?


**Ans** For object detection, you need a dataset with images + bounding box labels.

That’s the key requirement.

Required Dataset for Object Detection

Each image must have:

•	the object class name 

•	bounding box around object 

•	coordinates of box 

Example:

Image:

image1.jpg

Label:

image1.txt

Label content (YOLO format):

0 0.52 0.41 0.30 0.44

1 0.33 0.65 0.20 0.25

This means:

•	class 0 → person 


•	class 1 → helmet 

•	numbers → bounding box location 

Dataset Structure

dataset/
│
├── images/
│   ├── train/
│   └── val/
│
└── labels/
    ├── train/
    └── val/
Example:

images/train/img1.jpg

labels/train/img1.txt

Names must match.

Types of Objects You Can Train

Your dataset can contain:

•	People detection 

•	Car detection 

•	Helmet detection 

•	Animal detection 

•	Weapon detection 

•	Custom objects (anything) 

Object detection works for any object if labeled properly.

Dataset Requirements

Your dataset should have:

•	multiple images 

•	different backgrounds 

•	different lighting 

•	different angles 

•	multiple object sizes 

•	multiple objects per image (optional) 

Minimum Dataset Size

•	Testing → 50 images 

•	Small model → 200 images 

•	Good model → 500+ images 

•	Strong model → 2000+ images 

Example Object Detection Dataset

Image:

•	2 persons 

•	1 car 


Label file:

person box

person box

car box

Each object → one bounding box.

So the required dataset type is:

Images + bounding boxes + class labels


# Qno15 How many types of model detection in yolo program?


**Ans** There are the many types of model detection in yolo program.

Here are popular object detection model names. These are widely used in computer vision.

Two-Stage Object Detection Models

   (accurate but slower)
•	R-CNN 

•	Fast R-CNN 

•	Faster R-CNN 

•	Mask R-CNN 

•	Cascade R-CNN 

One-Stage Object Detection Models

   (fast and real-time)
•	YOLO 

•	SSD 

•	RetinaNet 

•	EfficientDet 

•	CenterNet 

Modern / Newer Models

•	DETR 

•	Deformable DETR 

•	DINO 

•	RT-DETR 

Most commonly used in practice

   Top ones you’ll see most:

•	YOLO 

•	Faster R-CNN 

•	SSD 

•	RetinaNet 

•	EfficientDet 

•	DETR


# Qno16 If we want to detect multiple objects classvise  track them, and count them, how will we do it?


**Ans** Detect, Track, and Count Multiple Objects Class-wise

To detect multiple objects, track them, and count them class-wise, we follow a step-by-step approach:

**1** Object Detection

First, we use an object detection model like YOLO to detect different classes of objects (such as cars, people, bikes) in each frame of a video.

The model gives:

•	Bounding boxes 

•	Class labels 

•	Confidence scores 

**2** Object Tracking

Next, we apply a tracking algorithm like DeepSORT.

This assigns a unique ID to each detected object and keeps track of it across frames.

This step helps us:

•	Know which object is which 

•	Avoid counting the same object multiple times 

**3** Class-wise Separation

Each detected object already has a class label (e.g., person, car).

We group objects based on their class so we can count them separately.

**4** Counting Mechanism

To count objects, we define a rule such as:

•	A virtual line or region in the frame 

•	When an object crosses the line, it is counted 

For each object ID:

•	If it crosses the line once → increase count 

•	Maintain separate counters for each class 

Example:

•	Cars count = 10 

•	People count = 5 

**5** Final Output

The system shows:

•	Tracked objects with IDs 

•	Class labels 

•	Total count of each class 

Conclusion (Short Form)

We use YOLO for detection, DeepSORT for tracking, and a line-crossing method to count objects separately for each class.

Simple Flow

Detection → Tracking → Assign IDs → Class grouping → Counting


# Qno17 What is the bot sort algoruithm?


**Ans** BoT-SORT is a multi-object tracking algorithm.

It is used after object detection to track objects across video frames.
So:

•	YOLO → detects objects 

•	BoT-SORT → tracks them (keeps same ID) 

What BoT-SORT does

  Example video:

Frame 1:

Person → ID 1

Car    → ID 2

Frame 2:

Person → ID 1  (same person tracked)

Car    → ID 2  (same car tracked)

It keeps consistent IDs for moving objects.

What "BoT-SORT" means

BoT-SORT = Bag of Tricks SORT

It is an improved version of:

•	SORT 

•	Deep SORT 

BoT-SORT improves both.

How BoT-SORT works (simple)

It combines:

•	object detection (YOLO boxes) 

•	motion prediction (Kalman filter) 

•	appearance matching (ReID features) 

•	IOU matching 

Then assigns IDs.

When you use BoT-SORT

Use it when you need:

•	people counting 

•	vehicle tracking 

•	CCTV tracking 

•	multi-object tracking 

•	line crossing detection 

YOLO + BoT-SORT Example

from ultralytics import YOLO

model = YOLO("yolov8n.pt")

results = model.track(
    source="video.mp4",
    tracker="botsort.yaml",
    show=True
)

This will:

•	detect objects 

•	assign IDs 

•	track across frames 

Output example

Person ID:1

Person ID:2

Car ID:3

IDs stay same while moving.

So in one line:

BoT-SORT = algorithm used to track detected objects in video


# Qno18 What is the object tracking?


**Ans** Object tracking means:

Following a detected object across multiple frames in a video and keeping its identity (ID).

Simple idea

Imagine a video:

Frame 1:

•	Person → ID 1 

Frame 2:

•	Same person moves → still ID 1 

Frame 3:

•	Still same person → ID 1 

This is tracking — not just detecting, but remembering the object.

Difference from Object Detection

•	Object Detection → finds objects in a single frame 

•	Object Tracking → follows those objects over time 

Example:

Detection:

Frame 1 → person, car

Frame 2 → person, car

Tracking:

Frame 1 → person(ID 1), car(ID 2)

Frame 2 → person(ID 1), car(ID 2)

How it works (simple)

Tracking systems use:

•	object detection (like YOLO) 

•	motion prediction 

•	matching objects between frames 

Common tracking algorithms:

•	SORT 

•	Deep SORT 

•	BoT-SORT 

Real-world uses

•	CCTV surveillance 

•	counting people or vehicles 

•	sports analytics 

•	self-driving cars 

•	face tracking 

Example (YOLO + Tracking)

from ultralytics import YOLO

model = YOLO("yolov8n.pt")

results = model.track(

   source="video.mp4",
    
   tracker="botsort.yaml",
    
   show=True
)

Final definition

tracking = detecting objects and keeping their identity across frames in a video

# Qno19 How to perform object tracking?

**Ans** Object tracking is a really fun and practical area of computer vision—it’s what lets systems 
follow a moving person, car, ball, or any object across video frames. The “how” depends a bit on your goal (accuracy vs. speed vs. simplicity), but here’s a clear way to approach it.

**1. Understand the pipeline**

At its core, object tracking usually follows this loop:

**1**	Detect the object (in the first frame or every frame) 

**2**	Assign an ID to the object 

**3**	Track its movement across subsequent frames 

**4**	Update its position as it moves 

**2. Choose your approach**

  **A. Traditional Tracking (fast, simpler)**

   These don’t require heavy AI models:

•	KCF (Kernelized Correlation Filter) 

•	CSRT (more accurate, slower) 

•	MOSSE (very fast, less accurate) 

You can use them directly with OpenCV.

Example (Python + OpenCV):

import cv2

tracker = cv2.TrackerCSRT_create()

video = cv2.VideoCapture("video.mp4")

ret, frame = video.read()

bbox = cv2.selectROI(frame, False)

tracker.init(frame, bbox)

while True:
    ret, frame = video.read()
    if not ret:
        break

   `success, bbox = tracker.update(frame)`
   
  if success:
     x, y, w, h = [int(v) for v in bbox]
     cv2.rectangle(frame, (x,y), (x+w,y+h), (0,255,0), 2)
     cv2.imshow("Tracking", frame)
    if cv2.waitKey(1) & 0xFF == 27:
        break

**B. Deep Learning-Based Tracking (more powerful)**

These combine detection + tracking:

•	YOLO (for detection) + SORT/DeepSORT (for tracking) 

•	Siamese networks (like SiamMask, SiamRPN) 

Workflow:

•	Detect objects using YOLO 

•	Pass detections to a tracker like DeepSORT 

•	Maintain consistent IDs across frames 

**3** Single vs Multi-object tracking

•	Single object tracking → easier (OpenCV trackers) 

•	Multi-object tracking (MOT) → needs: 

o	Detection every frame 

o	ID assignment (tracking-by-detection) 

**4** Key challenges to handle

•	Occlusion (object gets hidden) 

•	Lighting changes 

•	Fast motion / motion blur 

•	Similar-looking objects 

Deep learning trackers handle these better than classical ones.

**5** Tools & libraries

•	OpenCV → easiest starting point 

•	PyTorch / TensorFlow → for deep learning models 

•	Pretrained YOLO models → quick setup 

**6** What should you start with?

•	If you're a beginner → start with OpenCV CSRT tracker 

•	If you want real-world accuracy → YOLO + DeepSORT 

•	If you're building research-level systems → Siamese trackers 


# Qno20 How much there we have object tracking algorithms?


**Ans** There is no fixed number of object tracking algorithms. In fact, there are many (dozens) of algorithms, and new ones are still being developed.

We usually group them into categories instead of counting them.

**1. Traditional (Classical) Tracking Algorithms**

These are simpler and faster, often used with OpenCV:

•	KCF (Kernelized Correlation Filter) 

•	CSRT (more accurate) 

•	MOSSE (very fast) 

•	MedianFlow 

•	TLD (Tracking-Learning-Detection) 

•	Boosting Tracker 

•	MIL (Multiple Instance Learning) 

Around 6–10 common classical trackers

**2. Deep Learning-Based Tracking Algorithms**

These are modern and more powerful:

•	Using detection + tracking: 

o	YOLO + SORT 

o	YOLO + DeepSORT 

•	Siamese-based trackers: 

o	SiamFC 

o	SiamRPN 

o	SiamMask 

Around 10–20+ popular deep learning trackers

**3. Multi-Object Tracking (MOT) Algorithms**

Used when tracking multiple objects:

•	SORT 

•	DeepSORT 

•	ByteTrack 

•	FairMOT 

Around 5–10 well-known methods

Final Answer (simple form)

There is no exact number of object tracking algorithms, but there are more than 20–30 commonly used 

algorithms, and they are mainly divided into classical methods and deep learning-based methods.


# Qno21 when to use wich tracking algorithm?


**Ans** We don’t pick a tracker randomly. The choice depends on speed, accuracy, number of objects, and environment.

**1. Use Classical Trackers (Simple & Fast)**

(using OpenCV)

Use when:

•	You are tracking only one object 

•	You need real-time performance 

•	System is low-power (basic PC, embedded system) 

Which one to choose:

•	MOSSE → when you need very high speed 

•	KCF → when you want balance of speed + accuracy 

•	CSRT → when you need high accuracy (slower) 

**2. Use Detection + Tracking (Modern Approach)**

(using YOLO + trackers like SORT/DeepSORT)

Use when:

•	You have multiple objects 

•	Objects may enter/leave the scene 

•	You need object IDs (who is who) 

Which one to choose:

•	YOLO + SORT → faster, but less accurate 

•	YOLO + DeepSORT → more accurate, keeps identity better 

**3. Use Deep Learning Trackers (Advanced Cases)**

Use when:

•	Objects are moving fast 

•	There is occlusion (objects get hidden) 

•	Environment is complex (crowds, lighting changes) 

Examples:

•	SiamRPN 

•	SiamMask


# Qno22 How to perform instance segmentation on custom data set?


**Ans** Instance segmentation is a technique used to detect objects in an image and also identify the exact pixels belonging to each object.

To perform instance segmentation on a custom dataset, the following steps are used:

**1. Collect the Dataset**

First, we collect images related to our problem (for example, cars, people, fruits, etc.). The dataset should have enough variation in lighting, angles, and backgrounds.

**2. Annotate the Images**
 
Next, we label the objects in each image. In instance segmentation, we draw masks (pixel-wise labels) around each object instead of just bounding boxes.

Tools like LabelMe or CVAT are commonly used.

**4. Prepare the Dataset**

After annotation, we convert the data into a required format (such as COCO format). Then we split the dataset into:

•	Training set 

•	Validation set 

**5. Choose a Model**

We select an instance segmentation model such as:

•	Mask R-CNN (most common) 

•	YOLOv8 segmentation version 

**6. Train the Model**

We train the model using frameworks like:

•	PyTorch 

•	TensorFlow 

During training, the model learns:

•	Object detection 

•	Object classification 

•	Pixel-wise masks 

**7. Evaluate the Model**

After training, we test the model on validation data using metrics like accuracy or mAP (mean Average Precision).

**8. Perform Inference**

Finally, we use the trained model on new images. The model will:

•	Detect objects 

•	Draw bounding boxes 

•	Generate masks for each object 

Conclusion (Short Form)

Instance segmentation on a custom dataset involves collecting data, annotating masks, preparing the dataset, training a model like Mask R-CNN, and then using it to predict objects with pixel-level accuracy.
