
# ภาพรวมการตรวจสอบ (Enumeration Overview)

- การเข้าใช้งานระบบและสอบถามข้อมูล
- ใช้ในการค้นหาช่องโหว่และใช้ประโยชน์จากมัน
- ข้อมูลที่รวบรวมได้รวมถึงตารางการกำหนดเส้นทาง, ผู้ใช้และกลุ่ม, ชื่อเครื่อง, ทรัพยากรเครือข่าย

## พอร์ตและบริการที่พบบ่อยในการตรวจสอบ

- 📝 รายการบริการและพอร์ตที่พบบ่อยที่สุดในการตรวจสอบ

  | พอร์ต | โปรโตคอล | บริการ |
  | ---- | ---- | ------- |
  | 25 | TCP | [SMTP (Simple Mail Transfer Protocol)](#smtp-enumeration) |
  | 53 | TCP/UDP | [DNS (Domain Name System)](./dns-enumeration.md) |
  | 135 | TCP/UDP | Microsoft RPC Endpoint Mapper |
  | 137 | UDP | [NetBIOS Name Service](#netbios-enumeration) |
  | 139 | TCP | [SMB over NetBIOS](#netbios-enumeration) |
  | 161 | UDP | [SNMP (Simple Network Management Protocol)](#snmp-enumeration) |
  | 162 | TCP/UDP | [SNMP Trap](#snmp-enumeration) |
  | 389 | TCP/UDP | [LDAP](#ldap-enumeration) |
  | 445 | TCP/UDP | SMB over TCP |
  | 465 | TCP | [SMTP over TLS](#smtp-enumeration) |
  | 500 | UDP | ISAKMP/[IKE](./../15-cryptography/tunneling-protocols.md#ike-internet-key-exchange) |
  | 514 | UDP | Syslog, ใช้สำหรับบันทึกระบบ |
  | 587 | TCP | [SMTP over **optionally*** STARTTLS](#smtp-enumeration) |
  | 1433 | TCP/UDP | Microsoft SQL Server |
  | 3268 | TCP/UDP | Global Catalog Service |
  | 5060, 5061 | TCP/UDP | SIP (Session Initiation Protocol) |

- อ่านเพิ่มเติมที่ [รายการพอร์ต IANA](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.txt)
- ดูเพิ่มเติม • [การตรวจสอบพอร์ต | การวิเคราะห์มัลแวร์](./../07-malware/malware-analysis.md#port-monitoring) • [พอร์ตที่พบบ่อยในการสแกน | การสแกนเครือข่าย](./../03-scanning-networks/scanning-networks-overview.md#common-ports-to-scan)

## เทคนิคการตรวจสอบ (Enumeration Techniques)

- การดึงชื่อผู้ใช้โดยใช้อีเมล
  - เช่น หากอีเมลคือ tom.john@smith.com แสดงว่า tom.john น่าจะเป็นชื่อผู้ใช้
- ดึงข้อมูลโดยใช้รหัสผ่านเริ่มต้น
  - การระบุระบบปฏิบัติการจะบอกรหัสผ่านเริ่มต้น
