
# การปกปิดร่องรอย (Covering Tracks)

- พยายามซ่อนการมีอยู่ของผู้โจมตีในระบบเพื่อให้ระบบดูไม่ถูกโจมตี
- เพื่อหลีกเลี่ยงการถูกตรวจจับ ผู้โจมตีต้อง
  - แก้ไขบันทึกของระบบและลบกิจกรรมของพวกเขาระหว่างการโจมตี
  - ตรวจสอบให้แน่ใจว่ากิจกรรมในอนาคตจะไม่ถูกบันทึก
- คุณสามารถลดความเสียหายได้โดยลดรอยเท้า เช่น ทำให้การเข้าถึงของคุณปลอมแปลงเป็นกระบวนการที่ถูกต้อง
- 💡 มีกลยุทธ์การออกก่อนที่จะบุกรุกโดยการรู้ประเภทระบบปฏิบัติการ, ประเภทบันทึก, นโยบาย (เช่น การแจ้งเตือนบันทึกที่เปลี่ยนแปลง) และแอปพลิเคชันที่รันอยู่
  - เช่น หากคุณรู้ประเภทระบบปฏิบัติการ คุณสามารถรู้ทั่วไปว่าระบบปฏิบัติการเก็บบันทึกที่ไหน (เช่น `/var/log/`)
  - ❗ ไม่มีวิธีทั่วไปในการค้นหาว่าบันทึกทั้งหมดอยู่ที่ไหนในระบบ
- สิทธิ์ของไฟล์บันทึก
  - ข้อผิดพลาดทั่วไปและใหญ่: สิทธิ์ไฟล์บันทึกไม่ดี
    - อนุญาตให้เข้าถึงจากผู้ใช้หลายคนที่ไม่ควร
  - เช่น ในการอ่านข้อความระบบ คุณต้องกลายเป็น root `sudo tail /var/log/messages`
- ประวัติเทอร์มินัล
  - อาจทิ้งร่องรอยไว้ที่นี่สำหรับคำสั่งที่คุณรัน
  - ที่ที่ดีในการเรียนรู้เกี่ยวกับผู้ใช้ (บางครั้งพวกเขาเขียนรหัสผ่านโดยผิดพลาด)
  - คุณสามารถรัน `history` เพื่อรับประวัติ
    - ใน (fedora) บันทึกใน `home/<username>/.bash_history`

## บันทึกความปลอดภัย

### บันทึกความปลอดภัยของ Windows

- บันทึกเหตุการณ์ถูกเก็บไว้ใน `C:\Windows\System32\winevt\Logs`
- สามารถใช้เครื่องมือ OS "Windows Event Viewer" เพื่อเรียกดูบันทึก
- บันทึกถูกจัดหมวดหมู่เป็นแอปพลิเคชัน, ความปลอดภัย และระบบ

### บันทึกความปลอดภัยของ Linux

- ที่เก็บบันทึกไฟล์รวมศูนย์อยู่ในไดเร็กทอรี `/var/log`
  - ดูเพิ่มเติม [ไดเร็กทอรี Linux | พื้นฐาน Linux](./linux-basics.md#linux-folders)
- 📝 ไดเร็กทอรีบันทึกรวมถึง
  - `/var/log/messages` | `/var/log/syslog` (ตาม Debian)
    - บันทึกกิจกรรมระบบทั่วไป
  - `/var/log/auth.log` (Debian และ Ubuntu) | `/var/log/secure` (RedHat และ CentOS)
    - เหตุการณ์ที่เกี่ยวข้องกับการยืนยันตัวตน/การอนุญาต
    - เช่น บันทึก [SSH](./../15-cryptography/tunneling-protocols.md#ssh-secure-shell)
  - • `/var/log/utmp` • `/var/log/wtmp` • `/var/log/btmp` | `/var/log/faillog`
