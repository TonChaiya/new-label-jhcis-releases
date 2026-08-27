# New Label JHCIS Autoprint Releases

พื้นที่เผยแพร่ตัวติดตั้งและแพ็กเกจอัปเดตของระบบพิมพ์ฉลากยา New Label JHCIS

## เวอร์ชันล่าสุด

- เวอร์ชัน: `2026.08.27.1`
- Channel: `stable`
- วันที่เผยแพร่: 27 สิงหาคม 2026
- [ดาวน์โหลดจากหน้า Releases](https://github.com/TonChaiya/new-label-jhcis-releases/releases/tag/v2026.08.27.1)
- Setup SHA-256: `AD600C9CB7492AC85584D047479283D160F2939B7549B5E5377F89E8C83A5F63`
- Update SHA-256: `A2D7891EAFAE791D19AE6E90DEF779499035C074D8629678BF05A79350CFE492`

## สิ่งที่เปลี่ยนในเวอร์ชัน 2026.08.27.1

- ปรับหน้าเว็บและเมนูให้เป็นรูปแบบเดียวกันสำหรับเครื่องแม่และเครื่องลูกใน LAN
- เพิ่มรายละเอียด Visit พร้อมแก้ไข `visitdrug.dose` เฉพาะยา `drugtype` 01, 04 และ 10
- ค้นวิธีใช้ด้วย `doseprefix` แบบไม่สนช่องว่าง และบันทึกเฉพาะ `dosedescription`; ยังพิมพ์ข้อความเองได้
- ป้องกันแก้ไขผิด Visit/รหัสยา ด้วย Primary Key, transaction, row lock และประวัติ audit
- แก้การบันทึกภาษาไทยให้ใช้ `utf8 / utf8_general_ci` ตรงกับตาราง JHCIS
- เพิ่มพิมพ์ Auto แบบยาเดี่ยว และแก้ปุ่มคิวอัตโนมัติให้พิมพ์ยาทั้ง Visit โดยไม่ชนงานที่กำลังพิมพ์
- รวม Tray/Updater ใหม่ใน Update ZIP แบบระบบเต็ม โดยยังคงข้อมูลและค่าตั้งเดิม

อ่านรายละเอียดทุกรุ่นได้ที่ [CHANGELOG.md](CHANGELOG.md) และขั้นตอนใช้งานที่ [UPDATE_GUIDE.md](UPDATE_GUIDE.md)

คู่มือไฟล์ Setup/Update ของรุ่นนี้: [RELEASE_2026.08.27.1_TH.md](RELEASE_2026.08.27.1_TH.md)

## การรักษาข้อมูลเดิม

แพ็กเกจ Release ไม่มีรหัสผ่าน ข้อมูลผู้ป่วย Log หรือ Output จากเครื่องใช้งาน ระบบอัปเดตไม่เขียนทับไฟล์ตั้งค่าเฉพาะเครื่อง เช่น `config.php`, `autoprint_config.php` และ `settings.json`

การปรับ schema ทำผ่าน `Autoprint/setup_db.php` ในฐาน `autoprintdb` โดยไม่ลบข้อมูลเดิม และระบบจัดการคิวอัปเดตไม่แก้ฐาน `jhcisdb`

> ตัวติดตั้งปัจจุบันยังไม่มีลายเซ็นดิจิทัล กรุณาดาวน์โหลดจาก Repository นี้และตรวจสอบ SHA-256 ก่อนติดตั้ง
