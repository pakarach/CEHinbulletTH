
# พื้นฐานของ Linux

- ดูเพิ่มเติม ไฟล์บันทึกของ Linux

## ไดเร็กทอรีของ Linux

- `/`: Root
- `/var`: Variable Data / Log Files
  - ดูเพิ่มเติม [บันทึกความปลอดภัยของ Linux | Covering tracks](./covering-tracks.md#linux-security-logs)
- `/bin`: Binaries / User Commands
- `/sbin`: Sys Binaries / Admin Commands
- `/root`: Home dir for root user
- `/boot`: Store kernel
- `/proc`: Direct access to kernel
- `/dev`: Hardware storage devices
- `/mnt`: Mount devices
- `/etc`: Contain all your system configuration files in it e.g.
  - [ไฟล์โฮสต์](./../10-social-engineering/social-engineering-types.md#pharming)
  - [การตั้งค่าไฟร์วอลล์](./../11-firewalls-ids-and-honeypots/firewall-overview.md#firewalld)
  - [ไฟล์รหัสผ่าน](./cracking-passwords-overview.md#linux-passwords)
  - `/etc/sudoers` ที่ควบคุม
    - ใครสามารถรันคำสั่งอะไรในฐานะผู้ใช้ใดในเครื่องใด
    - สิ่งพิเศษเช่นต้องการรหัสผ่านสำหรับคำสั่งเฉพาะหรือไม่
- ดูเพิ่มเติม [การอำพรางเส้นทาง | Evading IDS](./../11-firewalls-ids-and-honeypots/evading-ids.md#path-obfuscation)

## สิทธิ์ของไฟล์ใน Linux

- กำหนดผ่านการใช้ค่าไบนารีสำหรับแต่ละกลุ่ม `rwx`
- การอ่านอย่างเดียวเทียบเท่ากับ 4, การเขียนคือ 2 และการรันคือ 1
- เพื่อสะสมสิทธิ์ ให้บวกตัวเลข
  - 4 คือการอ่านอย่างเดียว
  - 6 คือการอ่านและเขียน
  - 7 คือการอ่าน เขียน และรัน
- ลำดับ
  - ตัวเลขแรกสอดคล้องกับผู้ใช้
  - ตัวที่สองกับกลุ่ม
  - ตัวที่สามกับคนอื่น ๆ
- เช่น `chmod 744 anyfile`
  - ให้สิทธิ์ทั้งหมดกับผู้ใช้ การอ่านอย่างเดียวสำหรับกลุ่ม การอ่านอย่างเดียวสำหรับคนอื่น ๆ

## รันกระบวนการในพื้นหลัง

- การใช้ `&` จะทำให้โปรแกรมรันในพื้นหลัง
- ทำให้มีประโยชน์สำหรับโปรแกรมที่ไม่ต้องการอินพุตเท่านั้น
- โปรแกรมจะสิ้นสุดหากคุณออกจากระบบ
- โปรแกรมสามารถนำมาด้านหน้าได้โดยใช้ `fg <job-number>`

## 📝 คำสั่ง Linux ที่พบบ่อย

- `adduser` / `addgroup`: เพิ่มผู้ใช้ใหม่และกลุ่มไปยังระบบ
- `apropos`: ค้นหาชื่อและคำอธิบายของหน้า man ที่มีอยู่ทั้งหมดอย่างรวดเร็ว
- `ar`: สร้าง แก้ไข
