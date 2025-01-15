 This is a simple face recognition project using google teachable machine model. 
Project Overview The facial recognition project aims to implement a system that can identify and verify individuals based on their facial features. This system leverages machine learning algorithms, computer vision techniques, and a database to manage and track attendance or access control efficiently. It finds applications in areas such as security systems, attendance monitoring, and user authentication. 

Key Components Image Acquisition: 
Camera Integration: Captures real-time images or video streams using a webcam or IP camera. 

Image Preprocessing: Enhances captured images by resizing, normalizing, and adjusting for optimal input to the facial recognition model. 

Face Detection and Recognition: Face Detection: Identifies the presence of a face in the captured images using pre-trained models such as Haar Cascades, DLIB, or MTCNN. 

Face Recognition: Matches the detected face against a database of known faces using a deep learning model, such as those based on Convolutional Neural Networks (CNNs). 

Model Training and Deployment: Model Training: Uses a labeled dataset of faces to train a recognition model. Models like OpenCV’s FaceRecognizer, or deep learning frameworks like TensorFlow or Keras, can be used.

Model Deployment: Deploys the trained model for real-time recognition. The model classifies faces in the video feed into known or unknown categories.

Database Integration: Database Connection: Integrates with a relational database (e.g., MySQL) to store and retrieve user information and attendance records. 

Attendance Management: Automatically logs attendance by inserting records into the database upon successful recognition. 

User Interface: Graphical User Interface (GUI): Provides a visual interface for users to interact with the system, view attendance logs, and manage user data. Real-Time Feedback: Displays recognition results and status messages to users during operation. 

Technical Workflow Initialization: Load the pre-trained facial recognition model and associated label data. Establish a connection to the MySQL database for storing attendance records.

Real-Time Face Recognition: Continuously capture frames from the camera. Preprocess each frame and pass it through the face detection and recognition pipeline. Compare detected faces with stored profiles and determine the identity. 

Attendance Logging: For recognized individuals, check if attendance has already been marked for the current day. If not, insert a new record into the database with the person’s name, date, and time. 

Error Handling and Feedback: Provide real-time feedback in case of errors, such as database connection failures or low confidence in recognition results. Allow for manual intervention if required, such as overriding attendance entries or managing user profiles. 

Challenges and Considerations: Accuracy: Ensuring high accuracy in various lighting conditions and angles. Security: Securing the system to prevent unauthorized access and data breaches.

Performance: Optimizing the system for real-time processing without significant delays. Ethical Concerns: Addressing privacy issues and obtaining user consent for data collection and usage. 

Applications: Access Control: Automated door entry systems for secure access to buildings or rooms. Attendance Systems: Non-intrusive attendance tracking in schools, workplaces, and events. 

Surveillance: Monitoring and identifying individuals in public spaces for security purposes. This facial recognition project demonstrates a practical application of AI and computer vision, highlighting the integration of various technologies to solve real-world problems.

Step 1: Search in web browser google teachable machine
![image](https://github.com/user-attachments/assets/6bb6b365-486c-4022-8b40-83c149f6b134)
Step 2: Click on teachable Machine
![image](https://github.com/user-attachments/assets/4d0ff6b6-de54-476f-903b-3fce5ded1c66)
Step 3: Next click on Get Started
![image](https://github.com/user-attachments/assets/39aca9f4-7d6d-4961-afdb-00f75aa01c93)
Step 4: Click on imagr model
![image](https://github.com/user-attachments/assets/22906c1e-2d1c-41cb-b836-511ef22b832c)
Step 5: Click on Standard image option 
![image](https://github.com/user-attachments/assets/811703bf-5d4c-4ae8-a6e8-061b9bd641c4)
Step 6: Create your model in class1 as "your name" and class2 "unknown"
![Screenshot (108)](https://github.com/user-attachments/assets/34e529a3-3660-49e5-8bda-ad32c5a0e824)
Step 7: Train your model
![Screenshot (109)](https://github.com/user-attachments/assets/3067d280-b292-40b7-888a-8452918b828c)
Step 8: Export your model
Step 9: Download your "opencv keras model in "tensorflow"
![image](https://github.com/user-attachments/assets/37cb267a-9bc2-4ff9-acdc-2930014f4f29)
Step 10: Place the converyed keras file in projectb directory as "keras.h5" and "labels.txt" in pycharm.
![image](https://github.com/user-attachments/assets/c185b079-8c62-446d-bc27-ddf2d88f3ad3)
Step 11: Now create a file pycharm as "main.py" and enter code.
![image](https://github.com/user-attachments/assets/a81badfb-f1ed-4f18-ab54-f1279acf1f5b)
Step 12: Run code

Step13: expected output may display by opening the web camera of your system and show the "confidence score1" of your model



