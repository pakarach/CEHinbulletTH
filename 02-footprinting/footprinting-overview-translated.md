
# ภาพรวมของการทำ Footprinting

- รู้จักกันในชื่อ **fingerprinting** หรือ **reconnaissance**
- 📝 การรวบรวมข้อมูลเกี่ยวกับระบบเป้าหมาย
- เช่น ซอฟต์แวร์ โปรโตคอลเครือข่าย ระบบปฏิบัติการ หรืออุปกรณ์ฮาร์ดแวร์
- เป้าหมายสุดท้ายคือการหาวิธีเจาะเข้าสู่ระบบ
- 🤗 มักจะเสนอเป็นบริการแยกต่างหากที่บริษัทซื้อเพื่อตรวจสอบการรั่วไหลและดูว่ามีข้อมูลอะไรอยู่บ้าง
- ดูเพิ่มเติม • [Reconnaissance | ขั้นตอนการแฮ็ก](./../01-introduction/hacking-stages.md#1-reconnaissance) และ • [การรวบรวมข้อมูล | ขั้นตอนการทดสอบการเจาะระบบ](./../01-introduction/penetration-testing-phases.md#information-gathering)

## ประเภทของการทำ Footprinting

### การทำ Footprinting แบบ Passive

- รู้จักกันในชื่อ **passive reconnaissance**, **passive fingerprinting** หรือ **passive information gathering**
- 📝 ไม่มีการติดต่อโดยตรงกับเป้าหมาย
- อาศัยข้อมูลที่เปิดเผยต่อสาธารณะ
- ตรวจจับได้ยากที่สุด
- เช่น • ข่าวสาร • ประกาศรับสมัครงาน • ฐานข้อมูล [WHOIS](./whois-geoiplocation-and-dns-interrogation.md#whois) • บันทึกของรัฐบาล • การกรองเอกสาร • [การค้นหาข้อมูลจากถังขยะ | วิศวกรรมสังคม](./../10-social-engineering/social-engineering-types.md#dumpster-diving) • [การวิเคราะห์การแข่งขัน](#competitive-intelligence) • การค้นหาเบราว์เซอร์ • การค้นหาแผนที่ • การค้นหา DNS • การค้นหา Facebook/Twitter

#### ข้อมูลข่าวกรองจากแหล่งที่เปิดเผย (Open-source intelligence - OSINT)

- 📝 การรวบรวมและวิเคราะห์ข้อมูลที่รวบรวมจากแหล่งข้อมูลสาธารณะหรือเปิดเผย
- ❗ "Open-source" ไม่เกี่ยวข้องกับซอฟต์แวร์โอเพ่นซอร์สหรือข่าวกรองร่วมกัน
- หมวดหมู่: • สื่อ • อินเทอร์เน็ต • ข้อมูลรัฐบาลสาธารณะ • สิ่งพิมพ์ทางวิชาชีพและวิชาการ • ข้อมูลทางการค้า • วรรณกรรมสีเทา
- [awesome-osint | รายการเครื่องมือ](https://github.com/jivoi/awesome-osint), [OsintFramework | แผนภาพเครื่องมือ](https://osintframework.com/)

#### ข้อมูลข่าวกรองการแข่งขัน (Competitive intelligence)

- รู้จักกันในชื่อ **การวิเคราะห์การแข่งขัน**
- การประเมินจุดแข็งและจุดอ่อนของคู่แข่งปัจจุบันและคู่แข่งที่มีศักยภาพ
- เครื่องมือรวมถึง
  - สถิติการเข้าชม: [Alexa](https://alexa.com)
  - ข่าวสาร: [Google finance](https://fina
