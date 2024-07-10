
# เทคนิคการสแกน (Scanning Techniques)

- ใช้เพื่อ
  - ระบุพอร์ตที่เปิด i.e. **การสแกนพอร์ต (Port Scanning)**
  - ระบุโฮสต์หรืออุปกรณ์ที่ทำงานอยู่ i.e. **การค้นหาโฮสต์ (Host Discovery)**
- เทคนิคเดียวกันสามารถใช้ได้ทั้งการสแกนพอร์ตและการสแกนโฮสต์
  - แต่ต้องใช้เครื่องมือหรือคำสั่งต่างกัน
  - ดู: คำสั่ง Nmap [port scanning](./scanning-tools.md#-s-port-scan-options) vs [host discovery](./scanning-tools.md#-p-ping-host-discovery-options)

## เทคนิคตามโปรโตคอล

### การสแกน ICMP (Scanning ICMP)

- รู้จักกันในชื่อ **การสแกน ping** หรือ **การสแกน ICMP**
- โดยทั่วไปใช้เพื่อเช็คว่าโฮสต์ทำงานอยู่หรือมีข้อผิดพลาด
- 💡 📝 ประหยัดเวลาก่อนการรันการสแกนพอร์ต
- ❗ คำขอ ICMP ขาเข้ามักถูกปิดโดยไฟร์วอลล์
- บน Network Layer 3 ดังนั้นจึงไม่มีการนามธรรมของพอร์ตเช่น TCP/UDP (Transport Layer 4)
- ใน Nmap คำสั่ง ping เริ่มต้นด้วย `-P*` เช่น `-PE` สำหรับ `ICMP Echo`
- **เวลาเดินทางรอบ (Round-trip time)**
  - เวลาที่ใช้ในการเดินทางของแพ็กเก็ต
- หากถูกบล็อก มักจะไม่ตอบสนองหรือบางครั้งข้อผิดพลาด ICMP เช่น ประเภท 3 รหัส 13 (destination unreachable: communication administratively prohibited)

#### การสแกน Broadcast ICMP Ping

- ส่งแพ็กเก็ตไปยังทุกที่อยู่ที่เป็นไปได้ในเครือข่าย
- เช่น `ping -b 192.168.135.255` (subnet broadcast)
  - ping ไปที่ `192.168.129.19`, `192.168.129.20`, `192.168.129.21`...
  - หรือ broadcast ทั้งหมดผ่าน `ping -b 192.168.129.255`
    - โฮสต์ที่ทำงานอยู่จะเติมตาราง arp ท้องถิ่น สามารถดูได้โดยใช้ `arp -a`
- โดยปกติจะถูกทิ้งและเป็นวิธีที่ไร้ประโยชน์
- ดูเพิ่มเติม [การโจมตี Smurf | Denial of Service](./../13-web-applications/denial-of-service.md#smurf-attack)

#### ประเภทแพ็กเก็ต ICMP Ping

- **Echo**
  - ส่ง `ICMP ECHO` (ประเภท 8) คาดหวังการตอบกลับ `ICMP ECHO`
  - รู้จักกันในชื่อ ***การสแกน ICMP Echo*** หรือ [***ICMP Ping Sweep***](#icmp-ping-sweep)
  - 📝 **เครื่องมือ**
    - Nmap: `-PE`
    - hping: `hping3 -1 <target>`
- **Timestamp**
  - ส่ง `ICMP TIMESTAMP` (ประเภท 13)
  - **เครื่องมือ**
    - Nmap: `-PP`
    - hping: `hping3 -1 <target> --icmptype 13`
- **Address Mask**
  - ส่ง `ICMP ADDRESS MASK` (ประเภท 17)
