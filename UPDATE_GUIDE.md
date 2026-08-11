# คู่มือการติดตั้งและอัปเดต

## เครื่องใหม่ที่มี Laragon อยู่แล้ว

1. ดาวน์โหลด `NewLabelJHCIS_Setup_<version>.exe` จากหน้า Releases
2. ตรวจสอบ SHA-256 ให้ตรงกับ README หรือ `SHA256SUMS_<version>.txt`
3. ปิด Tray รุ่นเดิมหากมี แล้วเปิดตัวติดตั้ง
4. กรอกข้อมูลฐาน JHCIS และ HCC ตามหน้าตัวติดตั้ง
5. เปิด Laragon และ Tray จากนั้นตรวจหน้า Debug และลองพิมพ์ฉลากหนึ่งรายการ

ตัวติดตั้งจะสร้างหรือปรับ schema ของ `autoprintdb` ผ่าน `setup_db.php` โดยไม่ลบข้อมูลเดิม

## เครื่องที่ติดตั้งระบบอยู่แล้ว

- Tray ตรวจอัปเดตทันทีตอนเปิด และตรวจซ้ำตามรอบที่กำหนด
- เมื่อดาวน์โหลดเสร็จ หน้าเว็บจะแสดง “อัปเดตตอนนี้” และ “ไว้ภายหลัง”
- หากอัปเดตตอนเริ่มโปรแกรม Worker จะยังไม่เริ่มจนกว่าจะติดตั้งหรือเลือกไว้ภายหลัง
- หากอัปเดตระหว่างทำงาน ระบบจะรอเฉพาะสถานะ `processing`, `ready`, `printing` ที่ยังไม่เก่า
- `pending` และ `waiting` จะดำเนินต่อหลัง Tray กลับมาทำงาน

## ไฟล์ที่ระบบรักษาไว้

- `config.php`
- `config.php.bak`
- `Autoprint/autoprint_config.php`
- `Autoprint/settings.json`
- `Autoprint/GUI Start .../settings.json`
- Log, Output, Update cache และข้อมูลเฉพาะเครื่อง

## เมื่ออัปเดตไม่สำเร็จ

ตรวจไฟล์ต่อไปนี้:

```text
C:\laragon\www\new_labelJHCIS\Autoprint\update\logs\updater.log
C:\laragon\www\new_labelJHCIS\Autoprint\update\last-update.json
```

ตั้งแต่เวอร์ชัน `2026.08.11.7` log จะระบุขั้นตอนและชื่อ path ที่ผิดพลาด หากเครื่องยังใช้ Updater รุ่นเก่ามากและ Repair Update ไม่ผ่าน ให้ใช้ Setup รุ่นล่าสุดติดตั้งทับ โดยไม่ถอนโปรแกรมหรือฐานข้อมูลเดิมก่อน
