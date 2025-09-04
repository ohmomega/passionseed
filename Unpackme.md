# Unpackme - Write up

[English Version](#english-version) | [🇹🇭 ภาษาไทย](#ภาษาไทย)


## English Version

**Credit:**[picoCTF -Unpackme](https://play.picoctf.org/practice/challenge/313?difficulty=2&page=1&retired=0&search=unpackme&solved=0)

<img width="958" height="453" alt="Screenshot 2025-09-03 201321" src="https://github.com/user-attachments/assets/af062a25-9037-49c2-8556-27ef9e9d1f56" />

Hints:1.What is UPX?

---

## Description
This challenge is called Unpackme, which means the executable file is packed and we need to unpack it to find the flag.

We will use Webshell for this challenge.

For those who don’t know, a Webshell is a tool that runs on a web server. It can be written in PHP, ASP, JSP, Python, or even Shell script. Its purpose is to allow anyone who can access it to execute commands on the server.

In short, it’s like a Terminal but accessed through a web browser.

Here is the symbol of a Webshell:<img width="111" height="60" alt="image" src="https://github.com/user-attachments/assets/de8cc36e-5bdb-475f-b9c9-b67f128e8b98" />

---

Step 1: Download the file to Webshell

Copy the URL from the challenge and use wget in the Webshell to download the file.

<img width="962" height="552" alt="image" src="https://github.com/user-attachments/assets/f14c61cb-d1c9-439e-81c9-1f8ccc7cde52" />

wget https://artifacts.picoctf.net/c/205/unpackme-upx

wget is a command that fetches files from the internet and saves them to your current folder.
---
Step 2: Make the file executable

Before running, you need to give the file execute permission:

chmod u+x ./unpackme-upx
---
Step 3: Run the program

Run the file:

./unpackme-upx

It will ask:

What's my favorite number?

If you enter the wrong number, it will reply:

Sorry, that's not it!
---
Step 4: Find the correct number

We can use a reverse engineering tool like Ghidra to open the binary.
You will find a line like:

if (local_44 == 0xb38cb)


This shows that the correct number is hexadecimal 0xb38cb.
Convert it to decimal → 754635, then enter it in the program to get the flag.

---

Step 5: Enter the correct number
./unpackme-upx
What's my favorite number? 754635
picoCTF{up><_m3_f7w_5769b54e}

You will get the flag 

---

## Summary command
./filename - Run an executable file in the current folder.

chmod - Change file permissions, e.g., make a file executable.

wget - Open-source utility to download files from the web (HTTP/HTTPS/FTP).

---
may the force be with you

---

## ภาษาไทย

[English Version](#english-version) | [🇹🇭 ภาษาไทย](#ภาษาไทย)

**เครดิต:**[picoCTF -Unpackme](https://play.picoctf.org/practice/challenge/313?difficulty=2&page=1&retired=0&search=unpackme&solved=0)

<img width="958" height="453" alt="Screenshot 2025-09-03 201321" src="https://github.com/user-attachments/assets/af062a25-9037-49c2-8556-27ef9e9d1f56" />

คำใบ้: 1.What is UPX?

---

## คำอธิบาย
โจทย์นี้ชื่อว่า Unpackme หมายความว่าไฟล์ executable ถูก pack เอาไว้ เราต้องคลายไฟล์ออกมาเพื่อหา flag

---
เราจะใช้ webshell : ในการโจทย์ข้อนี้ สำหรับใครที่ไม่รู้จัก Webshell ก็คือ ที่รันบนเว็บเซิร์ฟเวอร์

เขียนขึ้นด้วยภาษาเว็บ เช่น PHP, ASP, JSP, Python, หรือแม้แต่ Shell script

หน้าที่ของมันคือ เปิดช่องทางให้ใครก็ตามที่เข้าถึงมัน สามารถสั่งคำสั่งบนเครื่องเซิร์ฟเวอร์ได้

เอาแบบสั้นๆเข้าใจง่ายมันคือ Terminal แต่ไปเปิดผ่านเว็บเบราว์เซอร์ 

นี่คือสัญลักษณ์ของ Webshell: <img width="111" height="60" alt="image" src="https://github.com/user-attachments/assets/de8cc36e-5bdb-475f-b9c9-b67f128e8b98" />


ขั้นที่ 1. เราจะโหลดไฟล์เข้าไปใน webshell โดยคัดลอกลิงค์ ตามรูป
<img width="962" height="552" alt="image" src="https://github.com/user-attachments/assets/f14c61cb-d1c9-439e-81c9-1f8ccc7cde52" />

พอเราได้ลิงค์มาแล้ว เข้าไปที่ webshell 
ใช้ wget เพื่อดาวน์โหลดไฟล์จาก URL ของ challenge

wget https://artifacts.picoctf.net/c/205/unpackme-upx

wget เป็นคําสั่งเพื่อดึงไฟล์จากอินเทอร์เน็ตไปยังโฟลเดอร์ปัจจุบันของคุณ

---

ขั้นตอนที่ 2: ให้สิทธิ์รันไฟล์

ก่อนรันต้องใช้คำสั่งเพิ่มสิทธิ์:

chmod u+x ./unpackme-upx

---

ขั้นตอนที่ 3: รันไฟล์

เมื่อรันไฟล์:

./unpackme-upx


มันจะถามว่า:

What's my favorite number?


ถ้าใส่เลขผิด มันจะตอบ:

Sorry, that's not it!

---

ขั้นตอนที่ 4:หารหัส
เราสามารถใช้ เครื่องมือ reverse engineering เช่น Ghidra เปิดไฟล์ binary แล้วจะเจอบรรทัดประมาณ:

if (local_44 == 0xb38cb)

แสดงว่าเลขที่ถูกต้องเป็น hexadecimal 0xb38cb
แปลงเป็น decimal → 754635 แล้วนำไปกรอกโปรแกรมเพื่อรับ flag

---

ขั้นตอนที่ 5:ใส่เลขที่ถูกต้อง 
เราจะใส่เลขที่ถูกต้องต่อการได้ธงมา 754635

./unpackme-upx
What's my favorite number? 754635
picoCTF{up><_m3_f7w_5769b54e}

ก็จะได้ flag มา

---


## สรุปคำสั่ง
./filename - รันไฟล์โปรแกรมที่อยู่ในโฟลเดอร์ปัจจุบัน

chmod - เปลี่ยนสิทธิ์ของไฟล์ เช่น ให้สามารถรันได้

wget - ดาวน์โหลดไฟล์จากเว็บผ่าน HTTP, HTTPS หรือ FTP

---

ขอพลังจงสถิตอยู่กับท่าน

