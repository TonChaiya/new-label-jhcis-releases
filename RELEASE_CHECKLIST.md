# Release Checklist

ใช้รายการนี้ทุกครั้งก่อนเผยแพร่เวอร์ชันใหม่ เพื่อไม่ให้เอกสารล้าหลัง `latest.json`

- [ ] ยกเวอร์ชันใน source, Tray, Inno Setup และ `app-version.json`
- [ ] อัปเดตหัวข้อเวอร์ชันล่าสุดใน `README.md`
- [ ] เพิ่มรายละเอียดเวอร์ชันใหม่ด้านบนของ `CHANGELOG.md`
- [ ] ปรับ `UPDATE_GUIDE.md` หากขั้นตอนหรือไฟล์ที่ระบบรักษาไว้เปลี่ยน
- [ ] สร้าง Setup และ Update ZIP
- [ ] ตรวจว่าแพ็กเกจไม่มี config, settings, Log, Output หรือข้อมูลผู้ป่วย
- [ ] ตรวจ SHA-256 และอัปเดต `SHA256SUMS.txt`
- [ ] อัปโหลด GitHub Release และ assets ให้เสร็จก่อน
- [ ] เปลี่ยน `latest.json` หลัง assets พร้อมแล้ว
- [ ] ตรวจว่า README, `latest.json` และ GitHub Release ระบุเวอร์ชันเดียวกัน
