
# ช่องโหว่ที่พบบ่อย (Common Vulnerabilities)

## Shellshock

- รู้จักกันในชื่อ ***bashdoor*** หรือ ***bash bug***
- ช่องโหว่การยกระดับสิทธิ์ที่อนุญาตให้รันคำสั่งโดยพลการ
- 📝 เกิดจากกลุ่มของข้อบกพร่องด้านความปลอดภัยในเชลล์ Bash ของ Unix
- รายการ CVE ที่เกี่ยวข้อง ได้แก่: • *CVE-[2014-6271](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-6271)*, *CVE-[2014-6277](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-6277)* • *CVE-[2014-6278](https://cve.mitre.org/cgi-bin/cvename.cgi?name=2014-6278)*, *CVE-[2014-7169](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-7169)* • *CVE-[2014-7186](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-7186)*, *CVE-[2014-7187](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-7187)*
- ทำได้โดยการจัดการรายการตัวแปรสภาพแวดล้อมแล้วทำให้ Bash รัน
- เมื่อเริ่มต้นตัววิเคราะห์ Bash จะรันสคริปต์ที่บันทึกเป็นตัวแปรสภาพแวดล้อม
- เช่น `$ env x='() { :;}; echo vulnerable' bash -c "echo this is a test"`
  - พิมพ์ก่อน `vulnerable` แล้ว `this is a test`
- ในการใช้ประโยชน์ต้องมีวิธีการสื่อสารกับ Bash
- มักใช้ประโยชน์จากเว็บไซต์ที่ใช้ CGI
  - CGI ย่อมาจาก "Common Gateway Interface"
  - ใน Apache ทำโดยใช้ [mod_cgi](https://httpd.apache.org/docs/2.4/mod/mod_cgi.html)
    - วิธีให้ Apache รันไฟล์สคริปต์และส่งผลลัพธ์ไปยังไคลเอนต์
    - Apache ส่งข้อมูลไปยังสคริปต์ CGI โดยใช้ตัวแปรสภาพแวดล้อม
  - เช่น หากคุณมี HTTP header ชื่อ `Sike` ในคำขอของคุณ คุณจะมีตัวแปรสภาพแวดล้อมชื่อ `HTTP_SIKE` ใน CGI ของคุณ
- ผลกระทบใหญ่
  - มีการรายงานการโจมตีหลายพันครั้งเมื่อมีการเปิดเผยข้อบกพร่องรวมถึงบอทเน็ตต่อ [กระทรวงกลาโหมของสหรัฐอเมริกา](https://en.wikipedia.org/wiki/Shellshock_(software_bug)#cite_note-IT-20140926-JS-10)
  - > "Shellshock ทำให้ Heartbleed ดูเล็กน้อย" - [ZDNet](https://www.zdnet.com/shellshock-makes-heartbleed-look-insignificant-7000034143/)

### การตรวจจับ Shellshock โดยใช้ Nmap

- สามารถใช้ [สคริปต์ Shellshock](
