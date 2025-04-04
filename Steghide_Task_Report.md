# Steganography Task Report: Extracting Hidden Message

## **Secret Spy Message Challenge - Report**

This report documents the step-by-step process of solving **Challenge 1: The Secret Spy Message** and **Challenge 2: Hidden QR Code (Advanced Image Steganography)**. The tasks involve extracting hidden messages from images using steganography tools and decoding a QR code embedded within another image.

---

# **Challenge 1: The Secret Spy Message**
## **Task 1: Extracting a Hidden Message Using Steghide & Stegseek**

### **Objective**  
To extract a hidden message from an image (`sample.jpeg`) using `steghide` and brute-forcing the password with `stegseek`.

### **Step-by-Step Solution**

1. **Downloaded the Image File**  
   - The image was stored in a ZIP file at:  
     [https://www.dropbox.com/scl/fi/1ovp3i2b44hp7qom58383/sample.zip?rlkey=4yfdu8tyr5sog792qpavrmeu2&st=ekm1enbr&dl=0](https://www.dropbox.com/scl/fi/1ovp3i2b44hp7qom58383/sample.zip?rlkey=4yfdu8tyr5sog792qpavrmeu2&st=ekm1enbr&dl=0)  
   - Unzipped the file to obtain `sample.jpeg`.

2. **Install Stegseek**  
   - Stegseek is a tool for brute-forcing passwords in `steghide`-protected images.  
   - Downloaded from GitHub:  
     [https://github.com/RickdeJager/stegseek](https://github.com/RickdeJager/stegseek)  
   - Installed using:
     ```bash
     sudo apt install ./stegseek_0.6-1.deb  
     ```

3. **Run a Wordlist Attack**  
   - Used a common password list (e.g., `rockyou.txt`) to brute-force the password:
     ```bash
     time stegseek sample.jpeg rockyou.txt
     ```
   - Stegseek extracted the hidden file (`sample.jpeg.out`).

4. **View the Extracted Message**  
   - Open the extracted file:
     ```bash
     cat sample.jpeg.out
     ```
   - The hidden message was revealed.

5. **Submit the Response**  
   - Submitted the extracted content via the Google Form:  
     [https://docs.google.com/forms/d/e/1FAIpQLScPeTRSHloUYzJTJR_aJ6Nj69Y24u7UAcUgkkvsvWDREOw4Nw/viewform](https://docs.google.com/forms/d/e/1FAIpQLScPeTRSHloUYzJTJR_aJ6Nj69Y24u7UAcUgkkvsvWDREOw4Nw/viewform)


---

## **Task 2: Decoding a Base64-Encoded Image**

### **Objective:**  
To decode a Base64-encoded JPEG file (`sample-2.txt`) back into an image and extract hidden content.

#### **Step-by-Step Solution**

1. **Download the Base64-Encoded File**  
   - File link:  
     [https://www.dropbox.com/scl/fi/fkkch4ir2d08ft7ilz2cl/sample-2.txt?rlkey=17uceiu44g78jw5r6gb4608oj&st=7x7y0gd7&dl=0](https://www.dropbox.com/scl/fi/fkkch4ir2d08ft7ilz2cl/sample-2.txt?rlkey=17uceiu44g78jw5r6gb4608oj&st=7x7y0gd7&dl=0)  

2. **Decode Base64 Back to JPEG**  
   - Used the `base64` command to convert the file back to an image:
     ```bash
     base64 -d sample-2.txt > recovered.jpg
     ```
   - This generated `recovered.jpg`.

3. **Extract Hidden Content**  
   - Checked if the image contains hidden data using `steghide` or `stegseek` and if a password is required, used `stegseek` with a wordlist:
     ```bash
     stegseek recovered.jpg rockyou.txt
     ```

4. **Submit the Response**  
   - Submitted the decoded content via the same Google Form.

---


# **Challenge 2: Hidden QR Code (Advanced Steganography)**

### **Objective**  
Extract a hidden QR code from an image (`stego_image.png`) using **Stegsolve** and decode it.

### **Step-by-Step Solution**

1. **Download the Image**  
   - File link:  
     [https://www.dropbox.com/scl/fi/6zcun8ujnmg2wgwxwi5o4/stego_image.png.tar.gz?rlkey=f2oeewzwrcct056e3cxs565yx&st=mg59w6z8&dl=0](https://www.dropbox.com/scl/fi/6zcun8ujnmg2wgwxwi5o4/stego_image.png.tar.gz?rlkey=f2oeewzwrcct056e3cxs565yx&st=mg59w6z8&dl=0)  
   - Extract the `.tar.gz` file to get `stego_image.png`.

2. **Install Stegsolve**  
   - Downloaded Stegsolve (requires Java):  
     [https://github.com/zardus/ctf-tools/blob/master/stegsolve/install](https://github.com/zardus/ctf-tools/blob/master/stegsolve/install)  
   - Ran it:
     ```bash
     java -jar stegsolve.jar
     ```

3. **Analyze the Image in Stegsolve**  
   - Loaded `stego_image.png` in Stegsolve.  
   - Navigated through different **color planes** (Red, Green, Blue, Alpha).  
   - Looked for patterns resembling a **QR code** and found it in `Red Plane 5`.  

4. **Extract the QR Code**  
   - Once found, took a screenshot of the QR code.  
   - Save it as `extract_data.png`.  

5. **Decode the QR Code**  
   - Used `zbarimg`:
     ```bash
     zbarimg extract_data.png
     ```
   - The output revealed a hidden message.

6. **Submit the Response**  
   - Submitted the decoded QR code content via the Google Form.

---

## **Conclusion**
- **Task 1**: Successfully extracted hidden messages using `stegseek` and `base64` decoding.  
- **Task 2**: Extracted a QR code from an image using **Stegsolve** and decoded it.  
- All findings were submitted via the provided Google Form.  

This report ensures reproducibility and documents the methodology for solving the challenges.  

**GitHub Repository:**      
**Submitted by:** Dorcas Johnson    
**Date:** 4th April, 2025  

--- 
