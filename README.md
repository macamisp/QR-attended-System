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
└── README.md
```

- **`attendance_sheets/`**: This directory stores the generated Excel files for each batch.
- **`templates/`**: This directory contains the HTML templates for the web pages.
- **`app.py`**: This is the main Flask application file that contains the backend logic.
- **`requirements.txt`**: This file lists the Python libraries required to run the application.
- **`README.md`**: This file provides an overview of the project.

## Setup and Usage

### Prerequisites

- Python 3
- pip

### Installation

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/your-username/qr-code-attendance-system.git
    cd qr-code-attendance-system
    ```

2.  **Install the dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

### Running the Application

1.  **Start the Flask server:**

    ```bash
    python3 app.py
    ```

2.  **Access the application:**

    Open your web browser and navigate to `http://127.0.0.1:5000`.

### How to Use

1.  **Generate a QR Code:**
    -   Enter the batch number in the text field and click "Generate QR Code".
    -   A QR code will be displayed on the screen.

2.  **Mark Attendance:**
    -   Scan the QR code with a mobile device.
    -   This will open a web page with a form to enter the student ID.
    -   Enter the student ID and click "Mark Attendance".
    -   The attendance will be recorded in the corresponding Excel file in the `attendance_sheets` directory.

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue if you have any suggestions or find any bugs.
