# New Label JHCIS Autoprint Releases

พื้นที่เผยแพร่ตัวติดตั้งและแพ็กเกจอัปเดตของระบบพิมพ์ฉลากยา New Label JHCIS

## เวอร์ชันล่าสุด

- เวอร์ชัน: `2026.08.11.9`
- Channel: `stable`
- วันที่เผยแพร่: 11 สิงหาคม 2026
- [ดาวน์โหลดจากหน้า Releases](https://github.com/TonChaiya/new-label-jhcis-releases/releases/tag/v2026.08.11.9)
- Setup SHA-256: `7BD13F26E18F817AE783BCEF59EDD54C37DDA903FE90C08FD1D677E1E2955C4D`
- Update SHA-256: `C12E0EAA3DE75E61C74878D2EA9BD84BEF2DD1EDE867F873CC8C2885E95C6308`

## สิ่งที่เปลี่ยนในเวอร์ชัน 2026.08.11.9

- แก้ `WinError 5 Access is denied` ขณะแทนที่ `AutoprintController.exe`
- Updater รุ่นใหม่รอให้ PyInstaller หรือ Antivirus ปล่อย file handle สูงสุด 45 วินาทีก่อนลองแทนที่อีกครั้ง
- Update ZIP รอบนี้ไม่แทนที่ Controller เพื่อให้เครื่องที่ติด file lock สามารถติดตั้ง Updater รุ่นแก้ไขได้ก่อน
- รวมการปรับรูปแบบฉลาก Auto จากเวอร์ชัน `.8` ครบถ้วน
- Setup ยังคงเป็นชุดเต็มสำหรับติดตั้งเครื่องใหม่หรือใช้ติดตั้งทับ

อ่านรายละเอียดทุกรุ่นได้ที่ [CHANGELOG.md](CHANGELOG.md) และขั้นตอนใช้งานที่ [UPDATE_GUIDE.md](UPDATE_GUIDE.md)

## การรักษาข้อมูลเดิม

แพ็กเกจ Release ไม่มีรหัสผ่าน ข้อมูลผู้ป่วย Log หรือ Output จากเครื่องใช้งาน ระบบอัปเดตไม่เขียนทับไฟล์ตั้งค่าเฉพาะเครื่อง เช่น `config.php`, `autoprint_config.php` และ `settings.json`

การปรับ schema ทำผ่าน `Autoprint/setup_db.php` ในฐาน `autoprintdb` โดยไม่ลบข้อมูลเดิม และระบบจัดการคิวอัปเดตไม่แก้ฐาน `jhcisdb`

> ตัวติดตั้งปัจจุบันยังไม่มีลายเซ็นดิจิทัล กรุณาดาวน์โหลดจาก Repository นี้และตรวจสอบ SHA-256 ก่อนติดตั้ง
