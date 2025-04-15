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
   - Opened the extracted file:
     ```bash
     cat sample.jpeg.out
     ```
   - The hidden message was `"If you can see this message then you are good. Buy a bottle of wine and chill. Cheers from Ephraim."` revealed.

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

 - Stegseek extracted the hidden file (`recovered.jpg.out`).

4. **View the Extracted Message**  
   - Opened the extracted file:
     ```bash
     cat recovered.jpg.out
     ```
   - The hidden message `"If you are hear, then you are just getting started. Drink cold water and continue."` was revealed.
  

5. **Submit the Response**  
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
   - The output revealed a hidden message `"You are one step closer to your journey."`.

6. **Submit the Response**  
   - Submitted the decoded QR code content via the Google Form.

---

## **Conclusion**
- **Task 1**: Successfully extracted hidden messages using `stegseek` and `base64` decoding.  
- **Task 2**: Extracted a QR code from an image using **Stegsolve** and decoded it.  
- All findings were submitted via the provided Google Form.  

This report ensures reproducibility and documents the methodology for solving the challenges.  

**GitHub Repository:** [https://github.com/deejonsen/Steghide_Task.md/blob/main/Steghide_task_Report.md](https://github.com/deejonsen/Steghide_Task.md/blob/main/Steghide_Task_Report.md)     
**Submitted by:** Dorcas Johnson    
**Date:** 4th April, 2025  

--- 


![Screenshot 2025-04-15 180344](https://github.com/user-attachments/assets/95b067ce-0216-49ab-b915-516d1f96ad6f)
![Screenshot 2025-04-15 180314](https://github.com/user-attachments/assets/23dbf0fa-228d-4db5-8a58-d02322548b29)
![Screenshot 2025-04-15 180502](https://github.com/user-attachments/assets/cbd4d3ce-0479-40e1-84bc-67343e030cb7)
![Screenshot 2025-04-15 180503](https://github.com/user-attachments/assets/d7c26300-5257-4f95-a165-4014a4f3cdd1)
![Screenshot 2025-04-15 180604](https://github.com/user-attachments/assets/30748acd-375c-4a1f-9f3b-feb126408e81)
![Screenshot 2025-04-15 180833](https://github.com/user-attachments/assets/6ccf2ee9-1f16-4d1d-b29b-baec96a3a57f)
![Screenshot 2025-04-15 181332](https://github.com/user-attachments/assets/02a85460-981e-4fe9-b1ed-a88f3682b5ba)
![Screenshot 2025-04-15 180539](https://github.com/user-attachments/assets/d475b361-2909-4f35-b656-9096d77dac77)
![Screenshot 2025-04-15 180918](https://github.com/user-attachments/assets/03f63d7b-4adc-4d0d-8f3e-450e386d0df8)
![Screenshot 2025-04-15 181033](https://github.com/user-attachments/assets/9a792f29-f4e1-443c-8c6e-872acb8b5fe0)
![Screenshot 2025-04-15 181425](https://github.com/user-attachments/assets/3b54fe5a-cd8f-4ea4-82b3-0a47a765a645)
![Screenshot 2025-04-15 1813322](https://github.com/user-attachments/assets/8a957d42-ac0b-4cb8-8787-56b8e46f3166)
![Screenshot 2025-04-15 181050](https://github.com/user-attachments/assets/9da4162a-1a7b-4abf-9604-8694409ee7c4)
![Screenshot 2025-04-15 181221](https://github.com/user-attachments/assets/20e3012f-fece-4c3a-ada6-d7257316b154)
![Screenshot 2025-04-15 181256](https://github.com/user-attachments/assets/1f7a607d-e50a-4417-b483-438f4f7da107)
![Screenshot 2025-04-15 181412](https://github.com/user-attachments/assets/f031c5ee-b7d4-4b11-931b-90e7122b07b7)
![Screenshot 2025-04-15 181444](https://github.com/user-attachments/assets/23cb63ac-35cb-46fd-b927-71cc8eeb55de)

