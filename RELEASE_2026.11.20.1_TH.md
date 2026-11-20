# New Label JHCIS 2026.11.20.1 — รองรับจำนวนจ่ายยา 0

เอกสาร UTF-8 สำหรับ Release v2026.11.20.1 ใน Repository TonChaiya/new-label-jhcis-releases

## การปรับปรุง

- หน้า Autoprint/visit_details.php ใส่จำนวนจ่ายยาเป็น 0 ได้ โดยรับจำนวนเต็ม 0–999999 ไม่รับว่าง ติดลบ ทศนิยม หรือรูปแบบเลขยกกำลัง
- แก้ไขวิธีใช้ของยาที่จำนวนเป็น 0 ได้ และคงการตรวจข้อมูลเก่าเพื่อป้องกันแก้ทับกัน
- บันทึกเฉพาะ visitdrug.unit และ dose ของ pcucode + visitno + drugcode ที่เลือก ตามเกณฑ์ยา drugtype 01,04,10 เดิม
- บันทึกแล้วส่งพิมพ์เฉพาะฉลากที่แก้ และคงปุ่มพิมพ์ Auto ทีละรายการ ค่า 0 ไม่ได้สั่งลบ/ยกเลิกยา และไม่ได้สั่งข้ามการพิมพ์
- Worker/Renderer รองรับการแสดงจำนวน 0 อยู่แล้ว จึงไม่แก้ Logic ดังกล่าว ไม่เปลี่ยน Database Schema
- รวมฟังก์ชันหน้าแรก/คิว/การติดตั้งฐานข้อมูลของรุ่นก่อน พร้อม Build Controller, Updater, Installer และ ZIP ใหม่

## ดาวน์โหลดและใช้งาน

### NewLabelJHCIS_Setup_2026.11.20.1.exe

ใช้ติดตั้งใหม่หรือซ่อมเครื่องที่ Updater เดิมใช้งานไม่ได้

1. เตรียม Windows/Laragon, PHP พร้อม PDO MySQL, Apache และ MySQL ตามระบบเดิม ชุดนี้ไม่ได้รวม Laragon/PHP/MySQL
2. สำรองฐานและไฟล์ตั้งค่า ปิด Tray เดิมก่อนติดตั้งทับ เลือกโฟลเดอร์โปรเจกต์ให้ถูกต้อง
3. Config เดิมถูกเก็บไว้ ตรวจ Host/Port/บัญชีฐานข้อมูลและ Log ที่ Installer แจ้ง หาก Preflight หรือ Final Schema Verification ไม่ผ่าน อย่าเพิ่งเริ่มระบบงาน
4. หลังติดตั้ง เปิดหน้า Visit ใหม่ ตรวจจำนวน 0 และทดลองบนข้อมูลสังเคราะห์ในเครื่องแยกก่อนใช้จริง

### NewLabelJHCIS_Update_2026.11.20.1.zip

แพ็กเกจเต็มระบบสำหรับอัปเดตผ่าน Tray หรือหน้าเว็บที่เชื่อมกับ Tray รุ่นที่รองรับ ไม่ต้องแตก ZIP ทับเองขณะโปรแกรมทำงาน

1. กดตรวจอัปเดต รอ Tray ดาวน์โหลดและตรวจ SHA-256/ขนาด
2. กดติดตั้งเมื่อพร้อม ระบบหยุดองค์ประกอบเดิม สำรองไฟล์ ติดตั้งและตรวจฐานตามกลไกเดิม แล้วเริ่มระบบกลับ
3. Config/Settings, Logs และ Output อยู่ในรายการป้องกันของ Updater ฐานเดิมไม่ถูกลบ แต่ Setup ยังคงตรวจ/เพิ่มโครงสร้าง autoprintdb ที่ขาดตามรุ่นก่อน การคืนไฟล์ไม่ใช่การย้อน DDL หรือสำรองฐาน
4. เครื่องที่ Updater เก่าหรือเสียจนรับแพ็กเกจไม่ได้ ให้ใช้ Setup โดยสำรองข้อมูลก่อน

### SHA256SUMS_2026.11.20.1.txt

```powershell
Get-FileHash .\NewLabelJHCIS_Setup_2026.11.20.1.exe -Algorithm SHA256
Get-FileHash .\NewLabelJHCIS_Update_2026.11.20.1.zip -Algorithm SHA256
```

| ไฟล์ | ขนาด bytes | SHA-256 |
|---|---:|---|
| Setup EXE | 59726057 | `5BB9EB7BA4E7E624D163A792DB53691ADF83274BB76A0A1B8506D16096E851F3` |
| Update ZIP | 81337050 | `271B2FC9108D523B7A71678E43C2A645F2B24D08E578A42F1507B2142BF20CC6` |

## ผลทดสอบและข้อจำกัด

- ผ่าน Tests บันทึก 0, วิธีใช้เปลี่ยนเมื่อจำนวน 0, ค่าผิดรูปแบบ, ข้อมูลเก่าขัดกัน, รายการไม่ใช่ยา และการรักษายา/Visit/สถานบริการอื่นกับเวลาเดิม โดยใช้ฐานสังเคราะห์เท่านั้น
- ผ่าน HTTP บนสำเนาหน้าจริง/SQLite adapter และ Node VM สำหรับ JavaScript ไม่ใช่ Browser E2E หรือ MySQL concurrency test
- ผ่านการแสดง int/string 0 ใน Worker HTML เดิมและสร้าง PDF 1 หน้าด้วย mPDF/FPDI ไม่สั่งพิมพ์หรือเชื่อมฐานจริง
- Regression Tests ด้านคิว/หน้าแรก/Diagnostics/Preflight/Schema Recovery/PDF/Packaging ผ่าน ตรวจ Payload 749 ไฟล์และ Hash/Size รายไฟล์ ไม่มี Config จริง/Logs/Root Database Dump/Tests ในชุดติดตั้งตาม Policy
- ยังต้องทดลอง Full Installation/อัปเดตและเครื่องพิมพ์จริงบนเครื่องแยก ไม่อ้างว่าผ่านทุก PHP/MySQL/MariaDB
- ช่อง number ใช้เลขอารบิก `0` ตามเดิม ไม่ได้เพิ่มการแปลงเลขไทย `๐`
- Installer ยังไม่มีลายเซ็นดิจิทัล และเป็นชุดติดตั้งปกติที่มี PHP/Python Source ตาม Pipeline เดิม ให้ตรวจแหล่งดาวน์โหลดและ Hash

อ้างอิงพฤติกรรมเดิมจาก RELEASE_2026.10.01.1_TH.md และขั้นตอนเผยแพร่จาก RELEASE_CHECKLIST.md ไม่เปลี่ยน Repository Visibility
