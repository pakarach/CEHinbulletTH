
# โปรโตคอล AAA

- AAA ย่อมาจาก (Authentication, Authorization, Accounting)
- กลุ่มของโปรโตคอลที่จัดการการเข้าถึงเครือข่าย
- บางครั้งโปรโตคอลเหล่านี้ถูกใช้ร่วมกับ
  - [Point-to-Point Protocol (PPP)](./../15-cryptography/tunneling-protocols.md#ppp-point-to-point-protocol)
  - [Extensible Authentication Protocol (EAP)](#extensible-authentication-protocol-eap)
  - Protected Extensible Authentication Protocol (PEAP)
  - [Lightweight Directory Access Protocol (LDAP)](./../04-enumeration/enumeration-overview.md#ldap)
- โปรโตคอลที่ใช้บ่อยที่สุดคือ [RADIUS](#radius) และต่อมาคือ [Diameter](#diameter) ในขณะที่ระบบเก่าจะใช้ [TACACS](#tacacs) และ [TACACS+](#tacacs-tacacs-plus)

## RADIUS

- ย่อมาจาก **R**emote **A**uthentication **D**ial **I**n **U**ser **S**ervice
- 📝 ใช้บ่อยโดย ISP (Internet Service Providers) และองค์กรในการควบคุมการเข้าถึง
- ใช้หลักในการจัดการการเข้าถึงอินเทอร์เน็ตหรือเครือข่ายอื่น ๆ
  - เครือข่ายสามารถใช้เทคโนโลยีเครือข่ายหลากหลาย รวมถึงโมเด็มอนาล็อก, DSL, WLANs, และ VPNs
- พื้นฐานจาก UDP (User Datagram Protocol)
- ยืดหยุ่นและสามารถขยายได้ เสนอวิธีการยืนยันตัวตนหลายวิธี
- ต้องการการตั้งค่าเซิร์ฟเวอร์ RADIUS ด้านหลัง
  - มักรวมกับ AD (active directory)

### Extensible Authentication Protocol (EAP)

- กรอบการทำงานการยืนยันตัวตนที่ใช้โดย [Enterprise WPA operation mode](./wireless-networks-overview.md#enterprise)
- แข็งแกร่งเมื่อใช้กับ TLS (EAP-TLS)
  - มีความปลอดภัยสูงขึ้นเมื่อโฮสต์ใบรับรองฝั่งลูกค้าในสมาร์ทการ์ด
- ขยายและแทนที่ [Point-to-Point Protocol (PPP)](./../15-cryptography/tunneling-protocols.md#ppp-point-to-point-protocol)

#### EAP Transport Layer Security (EAP-TLS)

- มาตรฐานที่ปลอดภัยโดยใช้โปรโตคอล TLS
- ต้องการการยืนยันตัวตนแบบสองทาง
  - ที่ซึ่งใบรับรองฝั่งลูกค้าสามารถเก็บในสมาร์ทการ์ดได้

## Diameter

- ผู้สืบทอดของ RADIUS
- ไม่เข้ากันโดยตรงกับรุ่นก่อนหน้า
- การรักษาความปลอดภัยถูกจัดการโดย
