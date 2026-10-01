# New Label JHCIS Autoprint Releases

พื้นที่เผยแพร่ตัวติดตั้งและแพ็กเกจอัปเดตของระบบพิมพ์ฉลากยา New Label JHCIS

## เวอร์ชันล่าสุด

- เวอร์ชัน: `2026.10.01.1`
- Channel: `stable`
- วันที่เผยแพร่: 1 ตุลาคม 2026
- [ดาวน์โหลดจากหน้า Releases](https://github.com/TonChaiya/new-label-jhcis-releases/releases/tag/v2026.10.01.1)
- Setup SHA-256: `3BE6E746638062E285706A21F1AAB9783E551AACB5D6B39F839A918A926EDF0F`
- Update SHA-256: `6A85EEBAA4D76738054774FFFE78CA40446D4FBB4AD165006E88FECB3B81B826`

## สิ่งที่เปลี่ยนในเวอร์ชัน 2026.10.01.1

- หน้า Visit แก้ไขได้ทั้งจำนวนที่สั่งและวิธีใช้ยาเฉพาะรายการยา Auto print
- เปลี่ยนเฉพาะ `visitdrug.unit` และ `visitdrug.dose` ของ Visit/รหัสยาที่เลือก โดยตรวจข้อมูลเดิมก่อนบันทึกเพื่อป้องกันการแก้ทับกัน
- บันทึกแล้วพิมพ์ซ้ำเฉพาะฉลากที่เปลี่ยน และคงปุ่มพิมพ์ Auto ทีละรายการไว้
- รายการที่ไม่ใช่ `drugtype` 01, 04, 10 แสดงแบบอ่านอย่างเดียวและไม่ถูกอัปเดต
- รวมหน้าเว็บ ระบบ LAN ลูกประคบ Tray และ Updater จากรุ่นก่อนครบชุด
- Update ZIP เป็นชุดระบบเต็ม รองรับการข้ามหลายเวอร์ชัน และไม่เขียนทับ config, settings, log, output หรือฐานข้อมูลเดิม

อ่านรายละเอียดทุกรุ่นได้ที่ [CHANGELOG.md](CHANGELOG.md) และขั้นตอนใช้งานที่ [UPDATE_GUIDE.md](UPDATE_GUIDE.md)

คู่มือไฟล์ Setup/Update ของรุ่นนี้: [RELEASE_2026.10.01.1_TH.md](RELEASE_2026.10.01.1_TH.md)

## การรักษาข้อมูลเดิม

แพ็กเกจ Release ไม่มีรหัสผ่าน ข้อมูลผู้ป่วย Log หรือ Output จากเครื่องใช้งาน ระบบอัปเดตไม่เขียนทับไฟล์ตั้งค่าเฉพาะเครื่อง เช่น `config.php`, `autoprint_config.php` และ `settings.json`

การปรับ schema ทำผ่าน `Autoprint/setup_db.php` ในฐาน `autoprintdb` โดยไม่ลบข้อมูลเดิม และระบบจัดการคิวอัปเดตไม่แก้ฐาน `jhcisdb`

> ตัวติดตั้งปัจจุบันยังไม่มีลายเซ็นดิจิทัล กรุณาดาวน์โหลดจาก Repository นี้และตรวจสอบ SHA-256 ก่อนติดตั้ง
