
# ภัยคุกคามและการโจมตีด้านความปลอดภัย (Security Threats and Attacks)

- ข้อมูลยิ่งมีค่ามากเท่าไร ภัยคุกคามและโอกาสในการโจมตีก็ยิ่งสูงขึ้นเท่านั้น

## ภัยคุกคามด้านความปลอดภัย

- 📝 **ภัยคุกคาม (Threat)** หมายถึงสิ่งใดก็ตามที่มีศักยภาพในการก่อให้เกิดความเสียหายต่อระบบ

### ประเภทของภัยคุกคาม

#### ภัยคุกคามทางเครือข่าย (Network Threats)

- **เครือข่าย (Network)** คือชุดของอุปกรณ์ที่เชื่อมต่อผ่านช่องทางการสื่อสารที่เกิดการแลกเปลี่ยนข้อมูลระหว่างอุปกรณ์
- ผู้โจมตีอาจแทรกซึมเข้าไปในช่องทางและขโมยข้อมูลที่ถูกแลกเปลี่ยน
- เช่น • [การโจมตีแบบปฏิเสธการให้บริการ (DoS)](./../13-web-applications/denial-of-service.md) • [การโจมตีด้วยรหัสผ่าน](./../06-system-hacking/cracking-passwords-overview.md) • การโจมตีด้วยกุญแจที่ถูกประนีประนอม, การโจมตีไฟร์วอลล์และ IDS • การโจมตี DNS และ ARP poisoning • การโจมตีแบบ man in the middle (MITM) • การสวมรอย • [การแย่งชิงเซสชัน](./../13-web-applications/session-hijacking.md) • การเก็บรวบรวมข้อมูล • การดักฟัง...

#### ภัยคุกคามโฮสต์ (Host Threats)

- การโจมตีที่พยายามเข้าถึงข้อมูลจากระบบ
- เช่น • [การโจมตีด้วยรหัสผ่าน](./../06-system-hacking/cracking-passwords-overview.md) • การเข้าถึงโดยไม่ได้รับอนุญาต • การทำโปรไฟล์ • [การโจมตีด้วยมัลแวร์](./../07-malware/malware-overview.md) • [การทำ footprinting](./../02-footprinting/footprinting-overview.md) • [การโจมตีแบบปฏิเสธการให้บริการ (DoS)](./../13-web-applications/denial-of-service.md) • การรันโค้ดโดยพลการ • การยกระดับสิทธิ์ • [การโจมตีแบบ backdoor](./../07-malware/malware-overview.md#backdoor) • [ภัยคุกคามด้านความปลอดภัยทางกายภาพ](./physical-security.md)

#### ภัยคุกคามแอปพลิเคชัน (Application Threats)

- การใช้ประโยชน์จากช่องโหว่ที่มีอยู่ในตัวแอปพลิเคชันเอง
  - เกิดจากการปฏิบัติการเขียนโค้ดที่ไม่ดี
  - โปรแกรมที่เร่งรีบมีข้อผิดพลาด เช่น ขาดการตรวจสอบความถูกต้องของข้อมูลนำเข้า
- สามารถพบได้ผ่านการย้อนรอยหรือการลองผิดลองถูก
- โค้ดขนาดใหญ่ที่ยากต่อการบำรุงรักษามีช่องโหว่มากขึ้น
- ส่วนใหญ่เกิดจากการตรวจสอบความถูกต้องของข้อมูลนำเข้าไม่เพียงพอ
- เช่น • [การฉีด SQL](./../14-sql-injection/sql-injection-overview.md) • cross-site scripting • [การแย่งชิงเซสชัน](./../13-web-applications/
