
## การควบคุมความปลอดภัยของข้อมูล (Information Security Controls)

### 1. Preventive controls

- มาตรการป้องกันเพื่อป้องกันไม่ให้เกิดเหตุการณ์ความปลอดภัย
- 📝 เช่น การใช้ firewall การเข้ารหัสข้อมูล

### 2. Detective controls

- มาตรการตรวจจับเพื่อระบุเหตุการณ์ความปลอดภัย
- 📝 เช่น การใช้ IDS/IPS การตรวจสอบ log files

### 3. Corrective controls

- มาตรการแก้ไขเพื่อกู้คืนระบบหลังจากเกิดเหตุการณ์ความปลอดภัย
- 📝 เช่น การสำรองข้อมูล (backup and restore)

### Information Security Management Program

- กิจกรรมทั้งหมดที่องค์กรดำเนินการเพื่อปกป้องข้อมูลที่สำคัญ
- 📝 เช่น การสร้างนโยบายความปลอดภัย การฝึกอบรม การรายงาน

### Enterprise Information Security Architecture (EISA)

- กฎระเบียบโครงสร้างและพฤติกรรมขององค์กรในด้านความปลอดภัย กระบวนการ และพนักงาน
- 📝 รวมถึงข้อกำหนด กระบวนการ หลักการ และโมเดล
- เป้าหมาย:
  - การตรวจสอบเครือข่ายขององค์กรแบบเรียลไทม์
  - การตรวจจับและกู้คืนจากการละเมิดความปลอดภัย
  - การประเมินความเสี่ยงของทรัพย์สินไอที

### Security management framework

- การลดความเสี่ยงของระบบใดๆ
- 📝 การผสมผสานระหว่างนโยบาย ขั้นตอน แนวทาง และมาตรฐาน

### Defense in Depth

- หรือที่รู้จักกันในชื่อ **defence in depth**
- 📝 การใช้หลายชั้นในการป้องกัน
- เช่นเดียวกับเกมป้องกันป้อม
- มอบความซ้ำซ้อนในกรณีที่การควบคุมความปลอดภัยล้มเหลวหรือช่องโหว่ถูกใช้ประโยชน์
- ชั้นต่างๆ:
  1. **Policies, Procedures, Awareness**: การจัดประเภทข้อมูล การจัดการความเสี่ยง การตรวจสอบโค้ด การศึกษา...
  2. **Physical security**: บัตรประจำตัว CCTV รั้ว...
     - คณะกรรมการบำรุงรักษาควรได้รับการปกป้องในห้องเซิร์ฟเวอร์
     - ไม่ดีในโรงเรียน มหาวิทยาลัย ฯลฯ
  3. **Perimeter**: การเข้ารหัส ตัวตน...
     - อยู่หน้าวงเครือข่ายภายในที่มีการกรองการรับส่งข้อมูลเข้าและออก
  4. **Internal network**: การแบ่งเขตเครือข่าย ไฟร์วอลล์...
  5. **Host**: แอนตี้ไวรัส การอัปเดตความปลอดภัย...
     - อุปกรณ์แต่ละตัวที่มีความสามารถด้านเครือข่าย เช่น เซิร์ฟเวอร์ / พีซี
  6. **Services**: บันทึกการตรวจสอบ การพิสูจน์ตัวตน การอนุญาต การปฏิบัติในการเขียนโค้ด
     - แอปพลิเคชันที่ทำงานบนโฮสต์
  7. **Data**: การสำรองข้อมูล การเข้ารหัส...
