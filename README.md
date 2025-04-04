# **Steganography Challenge Solutions**  
**Repository for extracting hidden messages from images using steganography tools.**  

---

## **📌 Overview**  
This repository contains solutions for three steganography challenges:  
1. **Secret Spy Message** – Extracting hidden data from an image using `steghide` and `stegseek`.  
2. **Base64-Encoded Image** – Decoding a Base64-encoded image and extracting hidden content.  
3. **Hidden QR Code** – Using `Stegsolve` to uncover a QR code embedded in an image.  

---

## **🛠️ Tools Required**  
- **Steghide** (`sudo apt install steghide`)  
- **Stegseek** ([GitHub](https://github.com/RickdeJager/stegseek))  
- **Base64** (Built-in on Linux/macOS)  
- **Stegsolve** ([Download](http://www.caesum.com/handbook/Stegsolve.jar))  
- **Zbar** (For QR decoding: `sudo apt install zbar-tools`)  
- **Wordlists** (e.g., `rockyou.txt` for brute-forcing passwords)  

---

## **📂 Repository Structure**  
```
/steganography-challenges  
│  
├── /Challenge_1  
│   ├── sample.jpeg           # Original image with hidden data  
│   ├── sample-2.txt           # Extracted message (after cracking)  
│   └── solution.md          # Step-by-step guide for Task 1 & 2  
│  
├── /Challenge_2  
│   ├── stego_image.png      # Image containing hidden QR code  
│   ├── extract_data.png     # Recovered QR code  
│   └── solution.md          # Steps to extract and decode QR  
│  
├── README.md                # This file  
└── LICENSE                  # Usage terms  
```

---

## **🚀 Quick Setup**  
1. **Install Dependencies**  
   ```bash
   sudo apt update && sudo apt install steghide zbar-tools default-jre
   ```
2. **Download Stegseek**  
   ```bash
   wget https://github.com/RickdeJager/stegseek/releases/download/v0.6/stegseek_0.6-1.deb
   sudo dpkg -i stegseek_0.6-1.deb
   ```
3. **Run Stegsolve (Java required)**  
   ```bash
   java -jar Stegsolve.jar
   ```

---

## **🔍 How to Use**  
### **Challenge 1: Secret Spy Message**  
1. Extract hidden data from `image.jpeg`:  
   ```bash
   stegseek sample.jpeg rockyou.txt
   ```
2. If successful, cat `sample.jpeg.out` for the hidden message.  

### **Challenge 2: Base64-Encoded Image**  
1. Decode the image:  
   ```bash
   base64 -d sample_2.txt > recovered.jpg
   ```
2. Extract hidden content:  
   ```bash
   steghide extract -sf recovered.jpg
   ```
   OR
   
   ```
   stegseek recovered.jpg rockyou.txt
   ```

### **Challenge 3: Hidden QR Code**  
1. Open `stego_image.png` in **Stegsolve**.  
2. Cycle through color planes to find the QR code.  
3. Decode it with:  
   ```bash
   zbarimg extract_data.png
   ```

---

## **📬 Submission**  
Submit your findings via the [Google Form](https://docs.google.com/forms/d/e/1FAIpQLScPeTRSHloUYzJTJR_aJ6Nj69Y24u7UAcUgkkvsvWDREOw4Nw/viewform).  

**Happy Hacking! 🕵️♂️**
