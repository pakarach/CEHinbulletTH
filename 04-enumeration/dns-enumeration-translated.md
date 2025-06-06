
# การตรวจสอบ DNS (DNS Enumeration)

## DNS

- ย่อมาจาก "Domain Name System"
- ระบบการตั้งชื่อแบบลำดับชั้นและกระจายศูนย์
- ใช้สำหรับทรัพยากรที่เชื่อมต่อกับอินเทอร์เน็ตรวมถึงคอมพิวเตอร์และบริการ
- รันบนพอร์ต TCP/UDP 53

### บันทึก DNS (DNS Records)

- บันทึกฐานข้อมูลที่ใช้ในการแมป URL กับที่อยู่ IP
- เก็บไว้ในไฟล์โซนในเซิร์ฟเวอร์ DNS
  - เซิร์ฟเวอร์ DNS มี "ไฟล์โซน" สำหรับแต่ละโดเมน
  - ไฟล์โซนประกอบด้วย "บันทึกทรัพยากร" (RRs)
- ช่วยให้ผู้ใช้เชื่อมต่อเว็บไซต์ของตนกับโลกภายนอก
- 📝 บันทึก DNS ที่พบบ่อยได้แก่
  - **`A`**
    - ชี้โดเมนไปยังที่อยู่ IPv4 เช่น `11.22.33.44`
  - **`AAAA`**
    - ชี้โดเมนไปยังที่อยู่ IPv6 เช่น `FE80::0202:B3FF:FE1E:8329`
  - **`MX`**
    - บันทึก Mail eXchange ใช้ในการส่งอีเมลไปยังโดเมน
    - ดูเพิ่มเติม [บันทึก MX | Whois, GeoIpLocation และการสืบสวน DNS](./../02-footprinting/whois-geoiplocation-and-dns-interrogation.md#mx-records)
  - **`NS`**
    - ใช้ในการมอบหมายโดเมนหรือซับโดเมนไปยังชุดของเซิร์ฟเวอร์ชื่อ
  - **`SOA`**
    - มีข้อมูลในการควบคุมการโอนย้ายโซน
    - รวมถึงหมายเลขซีเรียล, ตราประทับเวลา, ที่อยู่อีเมลของผู้รับผิดชอบโซน..
    - เช่น

      ```txt

        $TTL 86400
        @   IN  SOA     ns.icann.org. noc.dns.icann.org. (
                2020080302  ;Serial
                7200        ;Refresh
                3600        ;Retry
                1209600     ;Expire
                3600        ;Minimum TTL
        )

      ```

  - **`CNAME`**
    - ลิงก์ซับโดเมนกับบันทึก A หรือ AAAA ที่มีอยู่ของโดเมน
    - เช่น `www.cloudarchitecture.io` ถึง `cloudarchitecture.io`
  - **`PTR`**
    - ตรงข้ามกับ `A`, ชี้ IP ไปยังโดเมน
    - มักใช้ในการตรวจสอบสแปมสำหรับโปรแกรมอีเมล
  - **`HINFO`**
    - ข้อมูลระบบรวมถึงประเภท CPU และ OS

## เทคนิคการตรวจสอบ DNS (DNS Enumeration Techniques)

- ตรวจสอบบันทึก NS ทั้งหมดสำหรับ [การโอนย้ายโซน](#zone-transfers)
- ตรวจสอบบันทึก DNS ทั่วไป [DNS Records](#dns-records) สำหรับโดเมนที่กำหนด
- ดำเนินการตรวจสอบบันทึก SRV ที่พบบ่อย
