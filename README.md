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

Code:

from tensorflow.keras.models import load_model
# TensorFlow is required for Keras to work
import cv2  # Install opencv-python
import numpy as np

# Disable scientific notation for clarity
np.set_printoptions(suppress=True)

# Load the model
model = load_model("keras_Model.h5", compile=False)

# Load the labels, stripping any newline characters
class_names = [line.strip() for line in open("labels.txt", "r").readlines()]

# CAMERA can be 0 or 1 based on default camera of your computer
camera = cv2.VideoCapture(0)




while True:
    # Grab the webcamera's image.
    ret, image = camera.read()

    # Resize the raw image into (224-height,224-width) pixels
    image = cv2.resize(image, (224, 224), interpolation=cv2.INTER_AREA)

    # Show the image in a window
    cv2.imshow("Webcam Image", image)

    # Make the image a numpy array and reshape it to the model's input shape.
    image = np.asarray(image, dtype=np.float32).reshape(1, 224, 224, 3)

    # Normalize the image array
    image = (image / 127.5) - 1

    # Predicts the model
    prediction = model.predict(image)
    index = np.argmax(prediction)
    class_name = class_names[index]
    confidence_score = prediction[0][index]

    # Print prediction and confidence score
    print("Class:", class_name, end="")  # Removed slicing to print the full class name
    print("Confidence Score:", str(np.round(confidence_score * 100))[:-2], "%")

    # Listen to the keyboard for presses.
    keyboard_input = cv2.waitKey(1)

    # 27 is the ASCII for the esc key on your keyboard.
    if keyboard_input == 27:
        break

camera.release()
cv2.destroyAllWindows()

When developing a facial recognition project in PyCharm, several types of errors may arise. These errors can stem from various aspects of the project, including code logic, library usage, system setup, and environment configuration. Below is a list of common expected errors and how to address them:

1. Library Installation Errors
Error: ModuleNotFoundError: No module named 'cv2' or similar for other libraries like numpy, tensorflow, keras, mysql.connector.
Cause: Required libraries are not installed in the Python environment.
Solution: Install the missing library using PyCharm’s terminal or Python interpreter settings:


pip install opencv-python-headless numpy tensorflow keras mysql-connector-python

2. Incorrect Model Path
Error: OSError: Unable to open file (file not found or unable to open the file)
Cause: The specified path for the model file (keras_Model1.h5) or label file (labels1.txt) is incorrect or the file is missing.
Solution: Verify the file paths and ensure the files exist in the specified locations.

3. Camera Access Issues
Error: Error: Camera not accessible. or cv2.VideoCapture(0) failed to open camera.
Cause: The camera may be in use by another application, or the system doesn't have the necessary permissions.
Solution: Ensure no other application is using the camera and that PyCharm has the necessary permissions to access hardware.

4. Database Connection Errors
Error: mysql.connector.errors.InterfaceError: 2003: Can't connect to MySQL server on 'localhost' (10061)
Cause: MySQL server is not running or incorrect connection parameters.
Solution: Verify the MySQL server is running, and the connection parameters (host, user, password, database) are correct.

5. TensorFlow Errors
Error: Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX AVX2
Cause: TensorFlow is optimized for certain CPU instructions that are not available.
Solution: Install a version of TensorFlow compatible with your system's hardware or ignore the warning if it doesn't affect performance.

6. Model Prediction Errors
Error: ValueError: Input to model has incorrect shape
Cause: The input image is not preprocessed correctly to match the expected input shape of the model.
Solution: Ensure the image is resized and reshaped correctly before feeding it into the model.

7. File I/O Errors
Error: FileNotFoundError: [Errno 2] No such file or directory: 'labels1.txt'
Cause: Missing or incorrect file path.
Solution: Check if the file exists in the specified directory and the path is correct.

8. Python Version Compatibility
Error: SyntaxError: invalid syntax or unexpected behavior in some libraries.
Cause: Incompatibility between the Python version used and the installed libraries.
Solution: Ensure that you are using a compatible version of Python for the libraries in use, often Python 3.x for modern libraries.

9. Logical Errors in Code
Error: Code executes without runtime errors but produces incorrect results.
Cause: Incorrect implementation of logic, such as wrong attendance conditions or model prediction handling.
Solution: Debug the code using PyCharm’s debugging tools to step through and inspect variable states and logic flow.

10. Resource Management Issues
Error: Camera or database connection not being released properly, leading to locks or crashes.
Cause: Resources not being released correctly after use.
Solution: Use try-finally blocks or context managers to ensure resources are released properly:

Code:
try:
    # Code to access camera or database
finally:
    camera.release()
    conn.close()

By anticipating these errors and applying the suggested solutions, you can streamline the development process and reduce troubleshooting time for your facial recognition project in PyCharm.





