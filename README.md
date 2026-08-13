# New Label JHCIS Autoprint Releases

พื้นที่เผยแพร่ตัวติดตั้งและแพ็กเกจอัปเดตของระบบพิมพ์ฉลากยา New Label JHCIS

## เวอร์ชันล่าสุด

- เวอร์ชัน: `2026.08.11.9.2`
- Channel: `stable`
- วันที่เผยแพร่: 11 สิงหาคม 2026
- [ดาวน์โหลดจากหน้า Releases](https://github.com/TonChaiya/new-label-jhcis-releases/releases/tag/v2026.08.11.9.2)
- Setup SHA-256: `507FAA7E09E524931F2DC4D5F303156FD52A7B1A35F017384931DD255169EE78`
- Update SHA-256: `C012A871C7041F9BD08FF387631599574E6A6B7EA1663250FFA48998FB3757DB`

## สิ่งที่เปลี่ยนในเวอร์ชัน 2026.08.11.9.2

- ย้าย “รวม … ฉลาก” ไปบรรทัดเดียวกับวันที่และเบอร์โทร
- ทำตัวหนาเฉพาะข้อความ “รวม … ฉลาก”
- ลดวันที่และเบอร์โทรเป็น `11pt` เท่าชื่อหน่วยบริการ
- โหมด Compact/Dense ใช้ `10.5pt`
- คง eGFR ที่ `12pt` และระบบ Bootstrap Update จากรุ่นก่อน

อ่านรายละเอียดทุกรุ่นได้ที่ [CHANGELOG.md](CHANGELOG.md) และขั้นตอนใช้งานที่ [UPDATE_GUIDE.md](UPDATE_GUIDE.md)

## การรักษาข้อมูลเดิม

แพ็กเกจ Release ไม่มีรหัสผ่าน ข้อมูลผู้ป่วย Log หรือ Output จากเครื่องใช้งาน ระบบอัปเดตไม่เขียนทับไฟล์ตั้งค่าเฉพาะเครื่อง เช่น `config.php`, `autoprint_config.php` และ `settings.json`

การปรับ schema ทำผ่าน `Autoprint/setup_db.php` ในฐาน `autoprintdb` โดยไม่ลบข้อมูลเดิม และระบบจัดการคิวอัปเดตไม่แก้ฐาน `jhcisdb`

> ตัวติดตั้งปัจจุบันยังไม่มีลายเซ็นดิจิทัล กรุณาดาวน์โหลดจาก Repository นี้และตรวจสอบ SHA-256 ก่อนติดตั้ง
