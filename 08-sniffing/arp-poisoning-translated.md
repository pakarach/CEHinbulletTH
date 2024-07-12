
# การโจมตีด้วย ARP Poisoning (ARP poisoning)

## ARP

- ARP ย่อมาจาก "Address Resolution Protocol"
- 📝 รับผิดชอบการแปลงที่อยู่ IP เป็นที่อยู่ MAC
- สามารถใช้เพื่อขอรับที่อยู่ MAC ของอุปกรณ์บนเครือข่าย
- แพ็กเก็ตประกอบด้วย `ARP_REQUEST` และ `ARP_REPLY`
- คำสั่ง
  - `arp -a`: แสดงแคช ARP ปัจจุบัน
  - `arp -d *`: ล้างแคช ARP

### ตาราง ARP (ARP table)

- ใช้เพื่อแมปที่อยู่ MAC กับที่อยู่ IP
- อินเทอร์เฟซเครือข่ายทุกตัวมีตาราง ARP ของตัวเอง
- 📝 หากไม่มีรายการ ARP:
  1. คอมพิวเตอร์ A ส่งคำขอ ARP ออกอากาศในเครือข่ายถามหาที่อยู่ MAC จากที่อยู่ IP เฉพาะ
  2. คอมพิวเตอร์ B ตอบกลับที่อยู่ MAC และ IP ของตน
  3. คอมพิวเตอร์ A แทรกข้อมูลนั้นลงในตาราง ARP ของตนเพื่อใช้ในอนาคต

## การโจมตีด้วย ARP poisoning

- รู้จักกันในชื่อ • ***ARP spoofing*** • ***ARP spoofing*** • ***ARP cache poisoning*** • ***ARP poison routing*** • ***ARP cache flooding*** • ***ARP flooding***.
- การโจมตี Man in the middle ระหว่างเหยื่อและสวิตช์
- ส่งคำขอและการตอบกลับที่ปลอมแปลงแคช ARP ของเครื่องเป้าหมาย
- ใช้ประโยชน์จาก ARP ที่ไม่ตรวจสอบความถูกต้องของอุปกรณ์
- หากแคช ARP เต็ม พฤติกรรมที่แตกต่างกันสามารถสังเกตได้ขึ้นอยู่กับผู้ผลิต/การใช้งาน:
  - อาจ [บังคับให้สวิตช์ทำงานในโหมดปลอดภัย](https://www.trendmicro.com/vinfo/se/threat-encyclopedia/archive/security-advisories/arp%20flooding%20attack)
    - ทำตัวเป็นฮับ i.e. ส่งแพ็กเก็ตไปยังโฮสต์ทั้งหมด
    - พฤติกรรมเดียวกันนี้สามารถเห็นได้ใน [MAC flooding](./sniffing-attacks-overview.md#mac-flooding-attack)
  - ใน [Linux](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/net/core/neighbour.c#n388) อาจ:
    - ลบรายการที่เก่าที่สุด/ไม่ใช้งานออกจากตาราง (โดย garbage collector)
    - ปฏิเสธรายการใหม่

### ขั้นตอนการโจมตีด้วย ARP poisoning

1. **รวบรวมข้อมูล**
   1. รับที่อยู่ IP ของเหยื่อ เช่น `192.168.122.183`
      - เช่น ผ่าน [การค้นหาโฮสต์โดยใช้ `nmap`](./../03-scanning-networks/scanning-tools.md#-p-ping-host-discovery-options) เช่น `nmap -sn 192.168.0.0/24`
   2. รับที่อยู่เกตเวย์เริ่มต้นของเหยื่อ เช่น `192.168.122.1`
      - เช่น ผ่าน `ip route`
   3. รับที่อยู่ MAC ของเหยื่อ เช่น `00:05:ea:aa:bb:cc`
      - เช่น ผ่าน `arp-scan -l`
   4. รับที่อยู่ MAC ของเกตเวย์ เช่น `00:05:ea:dd:cc:bb`
      - เช่น ผ่าน `arp-scan -l`
2. **ติดตั้งเครื่องมือที่จำเป็น**
   - บน Debian / Ubuntu
     - `sudo apt install ettercap-graphical wireshark`
3. **กำหนดค่าการส่งต่อแพ็กเก็ต IP**
   - อนุญาตให้แพ็กเก็ต IP ส่งต่อจากโฮสต์หนึ่งไปยังอีกโฮสต์หนึ่ง
     - `echo 1 > /proc/sys/net/ipv4/ip_forward`
     - คำสั่ง `sysctl` (เชื่อถือได้มากกว่า)
       - `sysctl -w net.ipv4.ip_forward=1`
   - สามารถทำได้ใน Windows เช่นกัน
     - ผ่านรีจิสทรี (ค่าดั้งเดิม: `0x0` `0x1`)
       - `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\IPEnableRouter`
