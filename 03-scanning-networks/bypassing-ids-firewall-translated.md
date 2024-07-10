
# การหลีกเลี่ยง IDS และไฟร์วอลล์ (Bypassing IDS and Firewall)

- อ่านเพิ่มเติมที่ [การตรวจจับระบบตรวจจับการบุกรุก | Nmap](https://Nmap.org/book/subvert-ids.html#avoid-ids)
- ดูเพิ่มเติม • [การหลีกเลี่ยง IDS](../11-firewalls-ids-and-honeypots/evading-ids.md) และ [การหลีกเลี่ยงไฟร์วอลล์](../11-firewalls-ids-and-honeypots/evading-firewalls.md)

## การแยกแพ็กเก็ต (Packet Fragmentation)

- รู้จักกันในชื่อ ***การสแกนแยกส่วน IP*** หรือ ***การแยกส่วน IP***
- 📝 การแยกส่วนหัว TCP เป็นแพ็กเก็ตที่เล็กลงหลายส่วนเมื่อส่ง
- เซิร์ฟเวอร์จะประกอบกลับเมื่อได้รับแพ็กเก็ตทั้งหมด
- โดยปกติจะถูกละเว้นโดย IDS เนื่องจากการประมวลผลต้องการทรัพยากรคอมพิวเตอร์จำนวนมาก
- สามารถแยกส่วน IP datagram ได้ทุกชนิด: รวมถึง UDP, TCP, ICMP ฯลฯ
- ดูเพิ่มเติม [session splicing](./../11-firewalls-ids-and-honeypots/evading-ids.md#session-splicing) สำหรับ HTTP header variant
- เครื่องมือ
  - [Nmap](https://Nmap.org/book/man-bypass-firewalls-ids.html): ธง `-f` เช่น `nmap -f <ip-or-host>`
    - แยกแพ็กเก็ตเป็น 8 ไบต์หรือน้อยกว่าหลังจากหัวข้อ IP
    - หรือใช้ตัวเลือก `--mtu` เพื่อกำหนดไบต์ เช่น `--mtu 16`
  - [`fragroute`](https://tools.kali.org/information-gathering/fragroute)
    - การใช้งาน: `fragroute <domain-name>`
    - สกัดกั้น แก้ไข และเขียนทราฟฟิกที่ออกใหม่โดยใช้การแยกส่วน

## การกำหนดเส้นทางแหล่งที่มา (Source Routing)

- รู้จักกันในชื่อ ***การกำหนดเส้นทางแบบพาธ*** (path addressing)
- ระบุเส้นทางที่แพ็กเก็ตที่ผิดรูปจะใช้เพื่อไปยังโฮสต์เป้าหมาย
- ใช้เพื่อข้ามเส้นทาง (เราเตอร์/เกตเวย์) ที่มีไฟร์วอลล์
  - ไม่สนใจสิ่งที่ตารางเส้นทางกล่าว
- ❗ เกือบจะถูกบล็อกเสมอ
- ทำได้โดยการแก้ไขฟิลด์ที่อยู่ IP ในฟิลด์ตัวเลือก IP
  - ![IP datagram](img/ip-datagram.png)
- ใช้ Nmap:
  - **การกำหนดเส้นทางหลวม** (Loose Routing)
    - ระบุแพ็กเก็ตให้กำหนดเส้นทางแหล่งที่มาแบบหลวมผ่านจุดทาง IP ที่กำหนด
    - เช่น `--ip-options "L 192.168.0.7 192.168.30.9"`
  - **การกำหนดเส้นทางเข้มงวด** (Strict Routing)
    - คุณจะต้องระบุทุก ๆ ฮ็อปตามเส้นทาง
    - เช่น `--ip-options "S 192.168.0.7 192.168.0.9 .. 192.168.30.9"`
- ดูเพิ่มเติม [การปลอมแปลงที่อยู่ IP ผ่านการกำหนดเส้นทางแหล่งที่มา | Session Hijacking](#session-hijacking)
