
# เครื่องมือการแคร็กรหัสผ่าน (Password Cracking Tools)

- ดูเพิ่มเติม [เครื่องมือการแคร็กรหัสผ่านของเว็บเซิร์ฟเวอร์ | ภัยคุกคามและการโจมตีของเว็บเซิร์ฟเวอร์](./../12-web-servers/web-server-threats-and-attacks.md#web-server-password-cracking-tools)

## `crunch`

- สร้างพจนานุกรมรหัสผ่าน
- เช่น `crunch <min-length> <max-length> <character-pool> -o <file-name>`
- ความยาก/เวลาเพิ่มขึ้นแบบทวีคูณไม่ใช่เชิงเส้น
  - ใช้เวลานานขึ้นมากเมื่อเพิ่มตัวอักษรในรหัสผ่านทั้งหมด
  - เช่น `crunch 4 16 abcekfeafkapeo434@*.` สร้างหลายพันเพตะไบต์

## John the Ripper

- รู้จักกันในชื่อ • ***JtR*** หรือ ***`john`***
- 📝 ตรวจจับรหัสผ่าน OS อัตโนมัติตามการโจมตีพจนานุกรมหรือ brute-force
- ทดลองรหัสผ่านต่าง ๆ และเปรียบเทียบแฮชกับรหัสผ่าน OS
- รองรับ Windows, Linux และ macOS
- 📝 การใช้งาน:
  1. ดึงรหัสผ่าน OS ไปยังไฟล์
     - เช่น บน Linux John มีเครื่องมือ `unshadow` ที่สามารถใช้ได้: `unshadow /etc/passwd /etc/shadow > mypasswd`
  2. แคร็กรหัสผ่านไฟล์โดยใช้คำสั่งเริ่มต้น: `john mypasswd`
     - รหัสผ่านจะถูกบันทึกใน `$JOHN/john.pot`
     - คุณสามารถรัน `john --show mypasswd` เพื่อดูรหัสผ่านได้

## Hydra

- เครื่องมือแคร็กรหัสผ่านแบบขนานสำหรับโปรโตคอลเครือข่ายต่าง ๆ เช่น HTTP, Cisco, MySQl
- 💡 คุณสามารถใช้ [DVWA: damn vulnerable web app](http://www.dvwa.co.uk/) เพื่อการศึกษาและเรียนรู้การทดสอบการเจาะระบบ
- เช่น `hydra -L usernamelist.txt -P passlist.txt -e ns -F -t 1 -w 10 <host-ip-address> http-form-post "/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed" -v`
  - `-e ns`: ตัวเลือกเพิ่มเติม
    - `n`: ทดลอง null (สำหรับรหัสผ่านว่างเปล่า)
    - `s`: ทดลองรหัสผ่านเดียวกันกับชื่อผู้ใช้
  - `-t 1`: จำนวนงาน (ตามเธรด), ค่าเริ่มต้นคือ 16
    - ❗ ระวัง. การเชื่อมต่อมากเกินไปและเร็วเกินไป = ถูกตรวจจับทันที
  - `-w 10`: เวลารอ 10 ms
  - `<host-ip-address>`
    - โดยปกติผู้คนจะไปที่เป้าหมายโดยใช้พร็อกซีและตรวจสอบผลในพร็อกซี
      - เช่น [burp suite](./../05-vulnerabilities/vulnerability-analysis.md#burp-suite)
