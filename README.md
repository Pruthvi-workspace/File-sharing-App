<h1 align="center">📁 Python File Sharing App with QR Code</h1>
<h3 align="center">Share files across devices using HTTP server & QR code</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8%2B-blue" />
  <img src="https://img.shields.io/badge/Port-8010-secure-green" />
  <img src="https://img.shields.io/badge/Feature-QR_Generation-yellow" />
</p>

---

## 🌟 Key Features
- **Instant HTTP Server** - Share files via local network
- **QR Code Access** - Scan-to-connect functionality
- **Cross-Platform** - Works on Windows/mobile browsers
- **Secure Port** - Uses non-standard port 8010
- **OneDrive Integration** - Direct access to desktop files

---

## 🛠 Tech Stack
![Python](https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white)
![Local Server](https://img.shields.io/badge/-HTTP_Server-black?logo=windows-terminal&logoColor=white)



## 📥 Installation
```bash
pip install pyqrcode pypng socketserver
```

## 🚀 Quick Start
1. Clone repository
```bash
git clone https://github.com/yourusername/file-share-app.git
```
2. Run main.py
```bash
cd file-share-app && python main.py
```
3. Scan QR code or visit `http://[YOUR-IP]:8010`

![QR Code Workflow](https://via.placeholder.com/600x200?text=QR+Code+→+Browser+Access)

## 🧠 How It Works
### Core Components
1. **Network Configuration**
   ```python
   PORT = 8010  # Secure non-standard port
   s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
   s.connect(("8.8.8.8", 80))
   IP = "http://" + s.getsockname()[0] + ":" + str(PORT)
   ```
   
2. **File Access Setup**
   ```python
   desktop = os.path.join(os.environ['USERPROFILE'], 'OneDrive')
   os.chdir(desktop)  # Access OneDrive files
   ```

3. **QR Generation**
   ```python
   url = pyqrcode.create(IP)
   url.svg("myqr.svg", scale=8)  # High-resolution QR
   ```

## 🗂 Project Structure
```
file-share-app/
├── main.py             # Main application logic
├── myqr.svg            # Generated QR code
├── requirements.txt    # Dependency list
└── README.md           # Documentation
```

## 🔐 Security Note
**Why Port 8010?**  
- Avoids common port conflicts
- Not typically scanned by malware
- TCP protocol ensures reliable transfer

## 🚧 Future Roadmap
- [ ] File encryption support
- [ ] Transfer progress indicator
- [ ] User authentication system
- [ ] Mobile app integration

