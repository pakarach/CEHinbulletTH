
# เครื่องมือค้นหาและทรัพยากรออนไลน์ (Search Engines and Online Resources)

- เช่น ข้อมูลเกี่ยวกับพนักงานขององค์กรเป้าหมาย อินทราเน็ต หน้าเข้าสู่ระบบ...
- แหล่งข้อมูลรวมถึง • เว็บไซต์โซเชียลเน็ตเวิร์ก • บริการค้นหาคน • บริการแจ้งเตือน • บริการทางการเงิน • เว็บไซต์งานที่แสดงรายละเอียดโครงสร้างพื้นฐานของเป้าหมาย สถานที่ตั้งทางกายภาพ และรายละเอียดพนักงาน • Deep และ Dark Web

## การแฮ็กกูเกิล (Google Hacking)

- เกี่ยวข้องกับการใช้ชุดตัวดำเนินการค้นหา (**dorks**) และสร้างคำค้นหาที่ซับซ้อน
- 📝 รูปแบบของ [passive reconnaissance](./footprinting-overview.md#passive-footprinting)
- dorks ที่พบบ่อย:

  | Dork | ความหมาย | ตัวอย่าง |
  | ---- | ---------- | ------- |
  | **`site`** | เฉพาะจากโดเมนที่ระบุ | `azure site:cloudarchitecture.io` |
  | **`inurl`** | เฉพาะหน้าที่มีคำค้นหาใน URL | `inurl: cloudarchitecture` |
  | **`intitle`** | เฉพาะหน้าที่มีคำค้นหาในชื่อเรื่อง | `intitle: cloud architecture` |
  | **`cache`** | เวอร์ชันที่แคชของหน้าที่ค้นหา | `cache:cloudarchitecture.io` |
  | **`link`** | เฉพาะหน้าที่มี URL ที่ค้นหา ถูกยกเลิก | `link:cloudarchitecture.io` |
  | **`filetype`** | เฉพาะผลลัพธ์สำหรับประเภทไฟล์ที่ระบุ | `filetype:sql` |

- 📝 ปกติจะรวม dork `filetype` และ `site` ตามที่เห็นใน [metagoofil](#metagoofil)
- ตัวดำเนินการคำค้นหาใน Google

  | ตัวดำเนินการ | ความหมาย | ตัวอย่าง |
  | ---- | ---------- | ------- |
  | **`OR`**, **`|`** | X หรือ Y แต่ไม่ทั้งคู่ | `jobs OR gates`, `jobs | gates` |
  | **`AND`** | ผลลัพธ์ที่เกี่ยวข้องกับทั้ง X และ Y เป็นค่าเริ่มต้นของ Google | `jobs AND gates` |
  | **`-`** | ไม่รวมคำหรือวลี | `jobs ‑apple` |
  | **`*`** | ไวลด์การ์ดที่ตรงกับคำหรือวลีใด ๆ | `"Google * my life"` > google changed my life, google runs my life... |
  | **`(`**, **`)`** | กลุ่มหลายคำ | `(iPad OR iPhone) apple` |

- เช่น การค้นหารหัสผ่าน: `intext:"please change your" password | code | login file:pdf | doc | txt | docx -github`
  - **`intext`**: ในข้อความของเว็บไซต์
  - **`"please change your" password"`**: การวาง
