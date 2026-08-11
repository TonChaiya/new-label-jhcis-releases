# New Label JHCIS Autoprint Releases

พื้นที่เผยแพร่ตัวติดตั้งและแพ็กเกจอัปเดตของระบบพิมพ์ฉลากยา New Label JHCIS

## เวอร์ชันล่าสุด

- เวอร์ชัน: `2026.08.11.9.1`
- Channel: `stable`
- วันที่เผยแพร่: 11 สิงหาคม 2026
- [ดาวน์โหลดจากหน้า Releases](https://github.com/TonChaiya/new-label-jhcis-releases/releases/tag/v2026.08.11.9.1)
- Setup SHA-256: `CFC43993280BBD1E0754A0ED56C9246AF69D88D157F34584273B85A92C1B867C`
- Update SHA-256: `375E96BA09ACD183CBEEE2965D979CEFC99641D3F302BA6349379B91913E45D1`

## สิ่งที่เปลี่ยนในเวอร์ชัน 2026.08.11.9.1

- ลดขนาดตัวอักษรบรรทัด eGFR ของฉลาก Auto เป็น `12pt` ทุกโหมด
- คงการแก้ file lock และ Bootstrap Update จากเวอร์ชัน `.9`
- Update ZIP ไม่แทนที่ Controller เพื่อรองรับเครื่องที่เคยพบ `WinError 5`
- Setup ยังคงเป็นชุดเต็มสำหรับเครื่องใหม่หรือการติดตั้งทับ

อ่านรายละเอียดทุกรุ่นได้ที่ [CHANGELOG.md](CHANGELOG.md) และขั้นตอนใช้งานที่ [UPDATE_GUIDE.md](UPDATE_GUIDE.md)

## การรักษาข้อมูลเดิม

แพ็กเกจ Release ไม่มีรหัสผ่าน ข้อมูลผู้ป่วย Log หรือ Output จากเครื่องใช้งาน ระบบอัปเดตไม่เขียนทับไฟล์ตั้งค่าเฉพาะเครื่อง เช่น `config.php`, `autoprint_config.php` และ `settings.json`

การปรับ schema ทำผ่าน `Autoprint/setup_db.php` ในฐาน `autoprintdb` โดยไม่ลบข้อมูลเดิม และระบบจัดการคิวอัปเดตไม่แก้ฐาน `jhcisdb`

> ตัวติดตั้งปัจจุบันยังไม่มีลายเซ็นดิจิทัล กรุณาดาวน์โหลดจาก Repository นี้และตรวจสอบ SHA-256 ก่อนติดตั้ง
