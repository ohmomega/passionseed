# Invisible WORDs - Write up

[English Version](#english-version) | [🇹🇭 ภาษาไทย](#ภาษาไทย)


## English Version

**Credit:**[picoCTF -Invisible WORDs](https://play.picoctf.org/practice/challenge/354?difficulty=3&page=1&search=Invisible%20WORDs)

<img width="624" height="657" alt="Screenshot 2025-09-04 100654" src="https://github.com/user-attachments/assets/40431e81-8751-4b0c-bfb9-570568777d9d" />

Hints: 1. Something doesn't quite add up with this image...

2.How's the image quality?

---
## Description
This challenge is called Invisible WORDs. The idea is that there is hidden text inside an image (output.bmp) that we need to extract to get the flag.

We will use Webshell for this challenge.

For those who don’t know, a Webshell is a tool that runs on a web server. It can be written in PHP, ASP, JSP, Python, or even Shell script. Its purpose is to allow anyone who can access it to execute commands on the server.

In short, it’s like a Terminal but accessed through a web browser.

Here is the symbol of a Webshell: <img width="111" height="60" alt="image" src="https://github.com/user-attachments/assets/de8cc36e-5bdb-475f-b9c9-b67f128e8b98" />

---
Step 1: Download the file

Copy the URL from the challenge and use wget in the Webshell to download the file:

wget https://raw.githubusercontent.com/ohmomega/passionseed/refs/heads/main/invisiblewords.py (Download the code file or do it yourself)

wget https://artifacts.picoctf.net/c/401/output.bmp (Load image file)

wget fetches files from the internet to your current folder.

---

SStep 2: Check the script (optional)

cat invisiblewords.py

You can see that the script extracts hidden data from a BMP file.

---

Step 3: Run the Python script

python3 invisiblewords.py output.bmp

This creates output.zip from the hidden data in output.bmp

---

Step 4: Inspect the ZIP

file output.zip

Shows that the file is a ZIP archive.

---

Step 5: Extract hidden files

binwalk -e output.zip

cd _output.zip.extracted

ls

You will see files like 0.zip and ZnJhbmtlbnN0ZWluLXRlc3QudHh0.

---

Step 6: Find the flag

grep pico ZnJhbmtlbnN0ZWluLXRlc3QudHh0

The flag is:

picoCTF{w0rd_d4wg_y0u_f0und_5h3113ys_m4573rp13c3_a11dd85d}

---

## Summary command

binwalk -e - Extract embedded files from binary or ZIP.

cat - Show file content.

file - Check the type of a file.

grep - Search for text patterns inside files.

ls - List files in the current folder.

python3 - Run Python 3 scripts.

wget - Download files from the web (HTTP/HTTPS/FTP).

---

may the force be with you

---

## ภาษาไทย

[English Version](#english-version) | [🇹🇭 ภาษาไทย](#ภาษาไทย)

**เครดิต:**[picoCTF -Invisible WORDs](https://play.picoctf.org/practice/challenge/354?difficulty=3&page=1&search=Invisible%20WORDs)

<img width="624" height="657" alt="Screenshot 2025-09-04 100654" src="https://github.com/user-attachments/assets/40431e81-8751-4b0c-bfb9-570568777d9d" />

คำใบ้: 1. Something doesn't quite add up with this image...
2.How's the image quality?

---
## คำอธิบาย
โจทย์นี้ชื่อ Invisible WORDs หมายความว่ามีข้อความซ่อนอยู่ในรูปภาพ (output.bmp) เราต้องดึงข้อความซ่อนออกมาเพื่อหา flag

---

เราจะใช้ webshell : ในการโจทย์ข้อนี้ สำหรับใครที่ไม่รู้จัก Webshell ก็คือ ที่รันบนเว็บเซิร์ฟเวอร์

เขียนขึ้นด้วยภาษาเว็บ เช่น PHP, ASP, JSP, Python, หรือแม้แต่ Shell script

หน้าที่ของมันคือ เปิดช่องทางให้ใครก็ตามที่เข้าถึงมัน สามารถสั่งคำสั่งบนเครื่องเซิร์ฟเวอร์ได้

เอาแบบสั้นๆเข้าใจง่ายมันคือ Terminal แต่ไปเปิดผ่านเว็บเบราว์เซอร์ 

นี่คือสัญลักษณ์ของ Webshell: <img width="111" height="60" alt="image" src="https://github.com/user-attachments/assets/de8cc36e-5bdb-475f-b9c9-b67f128e8b98" />

---

ขั้นตอนที่ 1: ดาวน์โหลดสคริปต์

wget https://raw.githubusercontent.com/ohmomega/passionseed/refs/heads/main/invisiblewords.py (โหลดไฟล์โค้ดหรือเอาทำเองก็ได้)

wget https://artifacts.picoctf.net/c/401/output.bmp (โหลดไฟล์ภาพ)

wget คือคำสั่งดึงไฟล์จากอินเทอร์เน็ตไปยังโฟลเดอร์ปัจจุบัน

---

ขั้นตอนที่ 2: ตรวจสอบสคริปต์ (ไม่บังคับ)

cat invisiblewords.py

เพื่อดูว่าสคริปต์นี้ทำการดึงข้อมูลที่ซ่อนอยู่ในไฟล์ BMP

---

ขั้นตอนที่ 3: รันสคริปต์ Python

python3 invisiblewords.py output.bmp

จะสร้างไฟล์ output.zip จากข้อมูลที่ซ่อนอยู่ใน output.bmp

---

ขั้นตอนที่ 4: ตรวจสอบไฟล์ ZIP

file output.zip

จะแสดงว่าไฟล์เป็น ZIP archive

---

ขั้นตอนที่ 5: แตกไฟล์ซ่อน

binwalk -e output.zip

cd _output.zip.extracted

ls

คุณจะเห็นไฟล์ เช่น 0.zip และ ZnJhbmtlbnN0ZWluLXRlc3QudHh0

---

ขั้นตอนที่ 6: หา flag

grep pico ZnJhbmtlbnN0ZWluLXRlc3QudHh0

Flag คือ:

picoCTF{w0rd_d4wg_y0u_f0und_5h3113ys_m4573rp13c3_a11dd85d}

---

## สรุปคำสั่ง

binwalk -e - แยกไฟล์ที่ซ่อนไว้ใน binary หรือ ZIP.

cat - แสดงเนื้อหาไฟล์.

file - ตรวจสอบประเภทไฟล์.

grep - ค้นหาข้อความหรือ pattern ในไฟล์.

ls - แสดงรายชื่อไฟล์ในโฟลเดอร์ปัจจุบัน.

python3 - รันสคริปต์ Python 3.

wget - ดาวน์โหลดไฟล์จากเว็บ

---

ขอพลังจงสถิตอยู่กับท่าน

---

