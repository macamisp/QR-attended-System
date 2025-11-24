# QR Code Attendance System

This is a simple web-based attendance system that uses QR codes to streamline the process of marking attendance. The system is built with Flask and uses Excel files to store attendance data.

## Features

- **QR Code Generation:** Generate a unique QR code for each batch.
- **Attendance Marking:** Students can scan the QR code to access a page where they can enter their student ID to mark their attendance.
- **Batch-Specific Records:** Attendance is stored in separate Excel files for each batch.
- **IN/OUT Status:** The system automatically determines whether a student is checking in or out based on their previous entry for the day.
- **Data Integrity:** File locking is used to prevent data loss from concurrent requests.
- **Secure:** The application runs with debug mode disabled by default to prevent security vulnerabilities.

## Project Structure

```
.
├── attendance_sheets/
│   └── (Generated attendance files will be stored here)
├── templates/
│   ├── attendance.html
│   └── index.html
├── app.py
├── requirements.txt
├── Dockerfile
└── README.md
```

- **`attendance_sheets/`**: This directory stores the generated Excel files for each batch.
- **`templates/`**: This directory contains the HTML templates for the web pages.
- **`app.py`**: This is the main Flask application file that contains the backend logic.
- **`requirements.txt`**: This file lists the Python libraries required to run the application.
- **`Dockerfile`**: This file contains the instructions to build a Docker image of the application.
- **`README.md`**: This file provides an overview of the project.

## Setup and Usage

### Prerequisites

- Python 3
- pip

### Installation

1.  **Get the code:**

    Ensure you have the project files on your local machine.

2.  **Install the dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

### Running the Application

1.  **Start the Flask server:**

    ```bash
    gunicorn --workers 1 --bind 0.0.0.0:8000 app:app
    ```

2.  **Access the application:**

    Open your web browser and navigate to `http://127.0.0.1:8000`.

### How to Use

1.  **Generate a QR Code:**
    -   Enter the batch number in the text field and click "Generate QR Code".
    -   A QR code will be displayed on the screen.

2.  **Mark Attendance:**
    -   Scan the QR code with a mobile device.
    -   This will open a web page with a form to enter the student ID.
    -   Enter the student ID and click "Mark Attendance".
    -   The attendance will be recorded in the corresponding Excel file in the `attendance_sheets` directory.

## Deployment

This application can be easily deployed using Docker.

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/)

### Build the Docker Image

1.  **Navigate to the project directory.**

2.  **Build the image:**

    ```bash
    docker build -t qr-attendance-system .
    ```

### Run the Docker Container

1.  **Run the container:**

    ```bash
    docker run -d -p 8000:8000 -v "$(pwd)/attendance_sheets":/app/attendance_sheets qr-attendance-system
    ```

    This command will:
    -   Run the container in detached mode (in the background).
    -   Map port 8000 of the container to port 8000 on your local machine.
    -   Mount the `attendance_sheets` directory from your local machine into the container. This ensures that the attendance data is persisted even if the container is stopped or removed.

    **Note for Windows Users:** The `$(pwd)` syntax is for Linux and macOS. If you are using Windows Command Prompt, replace `$(pwd)` with the full path to your project directory (e.g., `C:\Users\YourUser\qr-code-attendance-system`).

2.  **Access the application:**

    Open your web browser and navigate to `http://localhost:8000`.

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue if you have any suggestions or find any bugs.
