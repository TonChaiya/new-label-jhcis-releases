# New Label JHCIS Autoprint Releases

พื้นที่เผยแพร่ตัวติดตั้งและแพ็กเกจอัปเดตของระบบพิมพ์ฉลากยา New Label JHCIS

## เวอร์ชันล่าสุด

- เวอร์ชัน: `2026.08.24.1`
- Channel: `stable`
- วันที่เผยแพร่: 24 สิงหาคม 2026
- [ดาวน์โหลดจากหน้า Releases](https://github.com/TonChaiya/new-label-jhcis-releases/releases/tag/v2026.08.24.1)
- Setup SHA-256: `F7E6C41B8E91E2F4FACB6204CA530A729F66B9462410C4619AAAA5F8DAC786CA`
- Update SHA-256: `B3739CADAC1F6ED40CD622FB5F9E586B05DF43857FA5F539C014F87505805638`

## สิ่งที่เปลี่ยนในเวอร์ชัน 2026.08.24.1

- เปลี่ยนชื่อไฟล์ Excel ของรายงานลูกประคบเป็น `รายงานการจ่ายลูกประคบ_YYYYMMDD_HHMMSS.xlsx`
- ใช้ header `filename*=UTF-8` สำหรับชื่อไฟล์ภาษาไทย และมีชื่อสำรองภาษาอังกฤษสำหรับเบราว์เซอร์เก่า
- รายงาน Excel, ข้อมูลในรายงาน และการกรองตามวันที่ยังทำงานเหมือนเดิม

อ่านรายละเอียดทุกรุ่นได้ที่ [CHANGELOG.md](CHANGELOG.md) และขั้นตอนใช้งานที่ [UPDATE_GUIDE.md](UPDATE_GUIDE.md)

คู่มือใช้งานไฟล์ที่ดาวน์โหลดจาก Release รุ่นก่อนโดยละเอียด: [RELEASE_2026.08.11.9.5_TH.md](RELEASE_2026.08.11.9.5_TH.md)

## การรักษาข้อมูลเดิม

แพ็กเกจ Release ไม่มีรหัสผ่าน ข้อมูลผู้ป่วย Log หรือ Output จากเครื่องใช้งาน ระบบอัปเดตไม่เขียนทับไฟล์ตั้งค่าเฉพาะเครื่อง เช่น `config.php`, `autoprint_config.php` และ `settings.json`

การปรับ schema ทำผ่าน `Autoprint/setup_db.php` ในฐาน `autoprintdb` โดยไม่ลบข้อมูลเดิม และระบบจัดการคิวอัปเดตไม่แก้ฐาน `jhcisdb`

> ตัวติดตั้งปัจจุบันยังไม่มีลายเซ็นดิจิทัล กรุณาดาวน์โหลดจาก Repository นี้และตรวจสอบ SHA-256 ก่อนติดตั้ง
