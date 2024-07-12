
# เครื่องมือดักฟัง (Sniffing tools)

- รู้จักกันในชื่อ • **sniffer** • **packet analyzer** • **protocol analyzer** • **network analyzer**
- 💡 ไม่เพียงแค่ใช้ในการแฮ็ก แต่ยังใช้ในการแก้ไขปัญหา เช่น โดยผู้ดูแลระบบ

## Cain and Abel

- รู้จักกันในชื่อ **Cain & Abel** หรือ **Cain**
- 📝 กู้คืนรหัสผ่านหลายประเภทโดยการดักฟังเครือข่าย
- 📝 สามารถทำได้อีกด้วย
  - ARP poisoning
  - การดักฟัง
  - การบันทึกการสนทนา VoIP
  - การแคร็กรหัสผ่าน เช่น การโจมตีพจนานุกรม, brute-force ฯลฯ
- ดูเพิ่มเติม • [Cain and Abel | ภัยคุกคามและการโจมตีเครือข่ายไร้สาย](./../09-wireless-networks/wireless-threats-and-attacks.md#cain-and-abel) • [Cain and Abel | ภัยคุกคามและการโจมตีเซิร์ฟเวอร์เว็บ](./../12-web-servers/web-server-threats-and-attacks.md#cain-and-abel) • [ขั้นตอนการโจมตีด้วย ARP poisoning |  ARP poisoning](arp-poisoning.md#arp-poisoning-attack-steps)

## libpcap

- 📝 ไลบรารีการจับแพ็กเก็ตชั้น 2 สำหรับ Linux/macOS
  - ดู [การเปิดใช้งานโหมด promiscuous](#turning-on-promiscuous-mode) สำหรับทางเลือกของ Windows
- 📝 ใช้โดย sniffer ส่วนใหญ่รวมถึง • [Wireshark](#wireshark) • [Snort](./../11-firewalls-ids-and-honeypots/intrusion-detection-system-(ids)-overview.md#snort) • [tcpdump](#tcpdump) • [TCPflow](#tcpflow) • [Cain and Abel](#cain-and-abel) • [Kismet](#kismet) • [Nmap](./../03-scanning-networks/scanning-tools.md#nmap)
- พัฒนาและดูแลโดย [tcpdump](#tcpdump)

## TCPflow

- [โอเพ่นซอร์ส](https://github.com/simsong/tcpflow) TCP/IP packet demultiplexer.
- เก็บข้อมูลในลักษณะที่ทำให้สะดวกสำหรับการดีบักและการวิเคราะห์
- คล้ายกับ [tcpdump](#tcpdump) แต่สร้างไฟล์แยกสำหรับแต่ละทิศทาง ทำให้อ่านง่ายขึ้น
- ใช้ `libpcap`

## tcpdump

- 📝 เครื่องมือบรรทัดคำสั่งที่แสดงทราฟฟิก TCP ทั้งหมดจากทุกอินเทอร์เฟซแบบเรียลไทม์
- มีในตัวสำหรับทุกระบบ Unix มีโคลนสำหรับ Windows ชื่อ [WinDump](https://www.winpcap.org/windump/)
- พัฒนาและดูแล [**`libpcap`**](#libpcap)
- ดูเพิ่มเติม [`man page | tcpdump.org`](https://www.tcpdump.org/manpages/tcpdump.1.html)

## Wireshark

- 📝 
