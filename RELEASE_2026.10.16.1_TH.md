# New Label JHCIS 2026.10.16.1 — คู่มือติดตั้งและอัปเดต

เอกสารภาษาไทย UTF-8 สำหรับ Release `v2026.10.16.1` ใน Repository `TonChaiya/new-label-jhcis-releases`

## สิ่งที่ปรับปรุง

- เพิ่ม Diagnostics, PHP/MySQL Preflight และ Safe Retry สำหรับการติดตั้งฐาน autoprintdb
- ตรวจ Schema Contract หลัก 9 ตารางและจัดทำ Repair Plan ก่อนซ่อม หากมี Conflict ที่ไม่ปลอดภัยจะหยุดพร้อม Log
- ใช้ Setup Lock รองรับการเรียกซ้ำและตรวจโครงสร้างจริงหลัง DDL ล้มเหลว ไม่สมมติว่า DDL Rollback สำเร็จ
- Installer ถือว่าฐานพร้อมเมื่อ Final Schema Verification ผ่านเท่านั้น หากไม่ผ่านจะไม่เปิด Tray อัตโนมัติ
- รวมระบบแก้จำนวน/วิธีใช้ยาและพิมพ์ซ้ำเฉพาะรายการจากรุ่นก่อน
- Controller, Updater, Installer และ Update ZIP เป็น Build ใหม่รุ่นเดียวกัน ไม่ฝัง Settings ของเครื่องพัฒนาใน EXE

## ไฟล์ดาวน์โหลดและการใช้งาน

### NewLabelJHCIS_Setup_2026.10.16.1.exe

ใช้ติดตั้งใหม่ หรือซ่อมเครื่องที่ระบบอัปเดตเดิมใช้งานไม่ได้

1. เตรียม Windows/Laragon พร้อม Apache, MySQL และ PHP ที่มี PDO MySQL ตามระบบเดิม ชุดนี้ไม่ได้รวม Laragon/PHP/MySQL
2. หากติดตั้งทับ ให้สำรองฐานข้อมูลและไฟล์ตั้งค่าไว้ก่อน และปิด Tray เดิมก่อนเริ่มติดตั้ง
3. เลือกโฟลเดอร์โปรเจกต์ให้ถูกต้อง กรอก Host, Port และบัญชี MySQL ให้ตรงเครื่อง ห้ามถือว่า phpMyAdmin เปิดได้แล้ว Installer จะเชื่อมต่อได้เสมอ
4. Config เดิมจะถูกเก็บไว้ ไม่เขียนทับด้วยค่าที่กรอกใหม่โดยอัตโนมัติ ตรวจ Log หากระบบแจ้งว่าค่าเดิมไม่ตรง
5. รอ Preflight, Setup และ Final Schema Verification หากล้มเหลว แม้ติดตั้งไฟล์แล้ว ฐานอาจยังไม่พร้อม ให้ตรวจตำแหน่ง Log ที่ Installer แจ้งก่อนเริ่มใช้งาน
6. ตรวจเครื่องพิมพ์ URL เครื่องแม่ และทดลองงานบนสำเนาก่อนนำไปใช้จริง

### NewLabelJHCIS_Update_2026.10.16.1.zip

ใช้ผ่าน Tray/หน้าเว็บที่เชื่อมกับ Tray รุ่นที่รองรับ Auto Update ไม่ใช่โปรแกรมติดตั้งที่เปิดด้วยการดับเบิลคลิก

1. ตรวจว่า Tray เปิดระบบตรวจอัปเดตและเข้าถึง Public Manifest ได้
2. กดตรวจอัปเดตจาก Tray หรือหน้าเว็บ แล้วรอดาวน์โหลดและตรวจขนาด/SHA-256
3. กดติดตั้งเมื่อพร้อม ระบบพักงานเดิม สำรองไฟล์ ติดตั้งแพ็กเกจเต็ม ตรวจ/ซ่อม Schema autoprintdb และเริ่มระบบกลับตามกลไกเดิม
4. ห้ามแตก ZIP ทับไฟล์โปรเจกต์ขณะที่ Tray/Worker ทำงาน หาก Updater เก่ารองรับแพ็กเกจไม่ได้ ให้ใช้ Setup แทนโดยสำรองข้อมูลก่อน
5. การดาวน์โหลดล้มเหลวหรือ Hash ไม่ตรงจะไม่เริ่มติดตั้งแพ็กเกจนั้น

ไฟล์ Config/Settings, Logs และ Output ของเครื่องเดิมอยู่ในรายการป้องกันของ Updater การอัปเดตไม่ได้ลบฐานเดิม แต่ Setup อาจเพิ่มโครงสร้าง autoprintdb ที่ขาด การคืนไฟล์โดย Updater ไม่ใช่การย้อน DDL หรือสำรองฐานข้อมูล

### SHA256SUMS_2026.10.16.1.txt

ตรวจไฟล์ที่ดาวน์โหลดด้วย PowerShell:

```powershell
Get-FileHash .\NewLabelJHCIS_Setup_2026.10.16.1.exe -Algorithm SHA256
Get-FileHash .\NewLabelJHCIS_Update_2026.10.16.1.zip -Algorithm SHA256
```

| ไฟล์ | ขนาด (bytes) | SHA-256 |
|---|---:|---|
| Setup EXE | 59746587 | `4867C33F678880BEE065DDC48FA748D092D244F415025CD28719DC773BC2DFD7` |
| Update ZIP | 81329881 | `6F44599EE7588F520C8BB257ABB927C3B2EEB18DFD921C934C24F1089B13BD35` |

## ผลตรวจและข้อจำกัด

- ผ่าน Tests คิวพิมพ์และจำนวน/วิธีใช้ด้วย SQLite in-memory, Preflight/Schema Recovery แบบ Mock, Installer Diagnostics Harness และ mPDF/FPDI
- ตรวจ Payload/Manifest รายไฟล์และตรวจว่า Executables ไม่มี Settings ของเครื่องพัฒนาฝังอยู่
- ยังไม่ได้ยืนยัน Full Installation บนเครื่อง 192.168.1.98 หรือทุกเวอร์ชัน PHP/MySQL/MariaDB
- Installer ยังไม่มีลายเซ็นดิจิทัล ให้ตรวจแหล่งดาวน์โหลดและ SHA-256 ก่อนใช้งาน
- เป็นชุดติดตั้งปกติตาม Pipeline เดิม ยังมี PHP/Python Source ที่อ่านได้ ไม่ใช่ Protected Source Build

การเผยแพร่ครั้งนี้ไม่เปลี่ยน Repository Visibility และไม่เชื่อมต่อหรือแก้ฐานข้อมูลจริงบนเครื่องพัฒนา
