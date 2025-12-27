# ReadAI - AI Resume Checker

**ReadAI** is a professional iOS application designed to help users identify AI-generated content in resumes and documents. By leveraging OCR, PDF parsing, and the Sapling AI API, it provides a real-time probability score for text authenticity.

---

## 🚀 Key Features

* **Live Camera Scanning**: Uses `VisionKit` and `DataScannerViewController` to capture text directly from physical documents.
* **Multi-Format Support**:
    * **PDF/Text Files**: Extracts text from digital documents using `PDFKit`.
    * **Photo Library**: Processes saved images through the `PhotosPicker` and `Vision` OCR.
* **Real-Time AI Detection**: Connects to the Sapling AI API to distinguish between "Human Written" and "AI Generated" content.
* **SwiftData History**: Automatically persists every scan, including the file name, AI score, and result text, for future reference.
* **Intuitive UI**: Features a custom `ResultGauge` that visually maps AI probability scores.

---

## 🛠 Tech Stack

| Component | Technology |
| :--- | :--- |
| **Framework** | SwiftUI |
| **Persistence** | [cite_start]SwiftData [cite: 1] |
| **OCR/Vision** | Vision & VisionKit |
| **PDF Engine** | PDFKit |
| **Networking** | URLSession with JSON Serialization |

---

## 📁 Project Structure



* [cite_start]**`ReadAIApp.swift`**: Initializes the `sharedModelContainer` and sets the app entry point[cite: 1].
* **`MainDetectorView.swift`**: The primary dashboard managing all input methods and result triggers.
* **`DetectionViewModel.swift`**: The core logic layer handling OCR processing, PDF extraction, and API calls.
* **`ScannedResume.swift`**: The SwiftData model defining the schema for saved scan results.
* **`HistoryView.swift`**: Provides a list of all past scans sorted by date.
* **`DataScannerViewController.swift`**: A `UIViewControllerRepresentable` bridge for live text scanning.

---

## 🚦 Getting Started

### Prerequisites
* Xcode 15.0+
* iOS 17.0+ (Required for `DataScannerViewController` and `SwiftData`)
* Sapling AI API Key

### Setup
1.  **Clone the Repository**:
    ```bash
    git clone [repository-url]
    ```
2.  **API Configuration**: Ensure your API key is correctly set in `DetectionViewModel.swift`.
3.  **Permissions**: The app requires the following in `Info.plist`:
    * `NSCameraUsageDescription`: For live scanning.
    * `kTCCServiceMediaLibrary`: For file and photo access.

---

## 📝 Usage

1.  **Select Input**: Use the **Live Scan**, **Upload Photo**, or **Upload File** buttons on the main screen.
2.  **Analyze**: The app extracts text and communicates with the detection server.
3.  **Review Results**: View the result gauge. A score above **70%** triggers an "AI Generated" warning.
4.  **Check History**: Tap the clock icon in the toolbar to view previous scans stored in the database.

---

## 🛡 Performance & Privacy
* **Thread Safety**: UI updates are performed on the `Main` thread after background API responses.
* **Security**: Uses security-scoped resource markers for document picking to maintain iOS sandboxing standards.
