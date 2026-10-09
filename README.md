# drdo-ANPR-project

# ANPR and Smart Gate Logistics

An Automatic Number Plate Recognition (ANPR) and Smart Gate Logistics system developed to automate vehicle tracking. It leverages YOLOv8 for accurate license plate detection and OCR algorithms to read the plates, subsequently logging vehicle entry, exit, and waiting times into a structured database. Developed during my summer internship at the Defense Research and Development Organisation (DRDO).

## Features
- **Real-Time Plate Detection:** Uses a fine-tuned YOLOv8 model to detect Indian license plates in video streams.
- **Optical Character Recognition (OCR):** Utilizes EasyOCR coupled with custom image preprocessing layers (Grayscale, CLAHE, Gaussian Blur, Otsu Binarization) to accurately extract plate numbers.
- **Smart Tracking & Memory Management:** Implements an `IndianPlateMemoryManager` class that uses dynamic spatial ID recovery to track vehicles seamlessly across frames.
- **Automated Logistics Logging:** Automatically calculates Arrival Time, Departure Time, and Waiting Time based on video frame rates and exports the synchronized metrics to a CSV database.

## Tech Stack
- **Computer Vision & Deep Learning:** YOLOv8 (Ultralytics), OpenCV, EasyOCR
- **Data Processing:** Pandas, NumPy, SciPy
- **Environment:** Python 3.12

## Repository Structure
- `drdo-1phase.ipynb + drdo-2phase.ipynb`: The core pipeline containing YOLO tracking, EasyOCR integration, image preprocessing layers, and the algorithmic text stabilization logic.
- `best.pt`: Custom trained YOLOv8 model weights for license plate detection.
- `VIDEO.csv`: Sample generated output containing synchronized parking management database logs.

## Installation & Usage

1. Install the required dependencies:
   ```bash
   pip install ultralytics easyocr opencv-python pandas scipy

# To run the pipeline, ensure the input video is in the correct directory and execute the main processing loop. The script will output an annotated video and a CSV log.
# The system generates logs in the following format:
--- SYNCHRONIZED PARKING MANAGEMENT DATABASE ---
 Track_ID Vehicle_Number Arrival_Time Departure_Time Waiting_Time
        1     RJ19CA9632     03:00:00       03:00:08     00:00:04
