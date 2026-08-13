# New Label JHCIS Autoprint Releases

พื้นที่เผยแพร่ตัวติดตั้งและแพ็กเกจอัปเดตของระบบพิมพ์ฉลากยา New Label JHCIS

## เวอร์ชันล่าสุด

- เวอร์ชัน: `2026.08.11.9.3`
- Channel: `stable`
- วันที่เผยแพร่: 11 สิงหาคม 2026
- [ดาวน์โหลดจากหน้า Releases](https://github.com/TonChaiya/new-label-jhcis-releases/releases/tag/v2026.08.11.9.3)
- Setup SHA-256: `8D9026711D52E094113DE0421BCB6132AD3C90FA4256E83580EE1401BECE97C0`
- Update SHA-256: `77F2FCD3E0244E724BFB0C7C811C8AC714EFB11C22A578688601BBFAE7BF3066`

## สิ่งที่เปลี่ยนในเวอร์ชัน 2026.08.11.9.3

- ทำ “รวม … ฉลาก” ให้หนาชัดขึ้นเหมือนข้อความวิธีใช้
- ใช้ฟอนต์ `THSarabunNewBold` และน้ำหนัก `900`
- คงตำแหน่งชิดขวาสุดและขนาด `12.5pt`; Compact/Dense ใช้ `12pt`
- คงรูปแบบส่วนหัวและ eGFR จากรุ่นก่อน

อ่านรายละเอียดทุกรุ่นได้ที่ [CHANGELOG.md](CHANGELOG.md) และขั้นตอนใช้งานที่ [UPDATE_GUIDE.md](UPDATE_GUIDE.md)

## การรักษาข้อมูลเดิม

แพ็กเกจ Release ไม่มีรหัสผ่าน ข้อมูลผู้ป่วย Log หรือ Output จากเครื่องใช้งาน ระบบอัปเดตไม่เขียนทับไฟล์ตั้งค่าเฉพาะเครื่อง เช่น `config.php`, `autoprint_config.php` และ `settings.json`

การปรับ schema ทำผ่าน `Autoprint/setup_db.php` ในฐาน `autoprintdb` โดยไม่ลบข้อมูลเดิม และระบบจัดการคิวอัปเดตไม่แก้ฐาน `jhcisdb`

> ตัวติดตั้งปัจจุบันยังไม่มีลายเซ็นดิจิทัล กรุณาดาวน์โหลดจาก Repository นี้และตรวจสอบ SHA-256 ก่อนติดตั้ง
