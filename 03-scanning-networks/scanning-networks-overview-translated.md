
# ภาพรวมของการสแกนเครือข่าย (Scanning Networks Overview)

- กระบวนการรับข้อมูลเพิ่มเติมเกี่ยวกับโฮสต์ พอร์ต และบริการในเครือข่าย
- การสืบสวนที่ละเอียดขึ้น
- วัตถุประสงค์คือการระบุช่องโหว่ในช่องทางการสื่อสารและสร้างแผนการโจมตี
- ใช้เทคนิคต่างๆ เพื่อระบุโฮสต์ พอร์ต และบริการในเครือข่ายเป้าหมาย
- ใช้โดยผู้ดูแลระบบเพื่อตรวจสอบนโยบายความปลอดภัย การตรวจสอบสถานะการทำงาน เป็นต้น
- สามารถสร้างแพ็กเก็ตที่กำหนดเองโดยใช้เครื่องมือต่างๆ
  - เช่น [Colasoft Packet Builder](http://www.colasoft.com), [NetScanTools Pro](https://www.netscantools.com), [Packeth](http://packeth.sourceforge.net)

## ประเภทการสแกน

- **การสแกนพอร์ต (Port Scanning)**: เพื่อแสดงรายการพอร์ตและบริการที่เปิดอยู่
- **การสแกนเครือข่าย (Network Scanning)**: เพื่อแสดงรายการที่อยู่ IP
- **การสแกนช่องโหว่ (Vulnerability Scanning)**: เพื่อค้นหาการมีอยู่ของช่องโหว่ที่รู้จัก

## การสแกนในเครือข่าย IPv6

- IP รองรับที่อยู่มากขึ้น
  - พื้นที่ค้นหาที่ใหญ่ขึ้น
  - ยากและซับซ้อนกว่า IPv4
  - ยากขึ้นในการทำ ping sweeps
- รองรับโฮสต์จำนวนมากในซับเน็ต
  - การตรวจสอบใช้เวลานานขึ้น
- 💡 ผู้โจมตีควรหาที่อยู่จากบันทึก อีเมล ทราฟฟิก ฯลฯ เพื่อระบุที่อยู่

## พอร์ตที่พบบ่อยในการสแกน

- 📝 รายการหมายเลขพอร์ต TCP และ UDP

  | พอร์ต | โปรโตคอล | บริการ |
  | ---- |:--------:| ------- |
  | 21 | TCP | [FTP (File Transfer Protocol)](./../15-cryptography/encrypting-communication.md#ftp-file-transfer-protocol) |
  | 22 | TCP | [SSH (Secure Shell)](./../15-cryptography/tunneling-protocols.md#ssh-secure-shell) |
  | 23 | TCP | [Telnet](banner-grabbing.md#telnet) |
  | 25 | TCP | [SMTP (Simple Mail Transfer Protocol)](./../04-enumeration/enumeration-overview.md#smtp) |
  | 53 | TCP/UDP | [DNS (Domain Name Server)](./../04-enumeration/dns-enumeration.md#dns) |
  | 80 | TCP | HTTP (Hypertext Transfer Protocol) ❗ HTTP/3 จะรันบน UDP |
  | 123 | TCP | [NTP (Network Time Protocol)](./../04-enumeration/enumeration-overview.md#ntp) |
  | 443 | TCP/UDP | HTTPS | Hypertext Transfer Protocol Secure (HTTPS) |
