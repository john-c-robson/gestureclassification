# GUI Gesture Classifier README

The GUI Gesture Classifier is a 3 part Python application that uses computer vision and a trained CNN model to count the number of fingers a user is holding up in front of a camera. This project is implemented using Python, tkinter, OpenCV, and the MediaPipe library. It's a fun and interactive way to count fingers in real-time and display the count on the screen.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [How It Works](#how-it-works)

## Introduction

The Finger Counter is a Python program that leverages the power of computer vision to recognize and count fingers. It captures video from your computer's camera, processes it in real-time, and overlays the count of fingers on the screen. It's a simple yet interesting project that can be used for various applications like gaming, virtual interfaces, or educational purposes.

## Features

- Real-time finger counting using a webcam.
- Visual feedback with finger overlays and finger count display.
- Data storage: Saves finger position data to a CSV file.
- Easy-to-use and customizable.

## How It Works

### 1 FingerCounter - DatasetGeneration

- Import all the required libaries

- Load in the handDetector Class which will be used to detect if there is a hand, the number of hands present and finally overlay the landmark locations on the presented hand.

- Load the method finger_counter used to provide a logical classification of current held up fingers determind by x and y positioning of finger tips compaired to finger knuckles. While this is running, if a hand is detected, the x and y position of all landmarks are saved into memory.

- Method storelmtomemory is called by the previous method when a positive detection is made and saves landmark information into memory. Method writememorytocsv waits for the "." key to be pressed, which will then create a csv file with the current date time containing all the landmark data that was previously saved into memory.

### 2 Build a model

- Import all the required libaries

- Loads in the dataset created by the previous notebook, and prepairs the data for with keras.

- Creates a CNN model with 4 layers with a softmax activation used to provide a classification. Upon completion the model will both display visual metrics regarding its performance, aswell as save the model for use in the next notebook.

### 3 GUI Detector

- Ensures dependacies are installed.

- Imports all required libaries and loads in the previously trained CNN model created in "2 Build a model" notebook.

- Loads in the handDetector class used in "1 FingerCounter - DatasetGeneration" notebook. This will be used with the live video capture to match the previous collected data.

- Loads in the modelprediction method which sanitises the live feed to match the models format.

- Loads in the numberoffingers method which works similarly to that used in data capture. This will be used to display the if the classification made by the model is correct or not.

- Loads in the modelpredict method used to provide the number of fingers predicted by the model.

- Loads in the show_frames method which is called each frame to provide both the overlay to the camera feed.

- The black box tests were used to ensure that both the logical classification and the CNN model were able to correctly classify the said number of fingers correctly before the application runs.

- The main method positions all the front end components and calls all the methods to begin the classifications.
