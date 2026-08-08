# RE:IMAGINE — DENSO Eco Park

เว็บไซต์นี้แปลงมาจากไฟล์ดีไซน์ Stitch (`stitch_denso_eco_park_re_imagine.zip`) ให้กลายเป็นเว็บไซต์แบบ static HTML ที่ใช้งานได้จริง ทุกหน้าเชื่อมโยงกันด้วยเมนูเดียวกัน พร้อมนำขึ้น Vercel ได้ทันทีโดยไม่ต้องตั้งค่าอะไรเพิ่ม (ไม่มี build step)

## โครงสร้างเว็บไซต์ (8 หน้า, ลิงก์ถึงกันหมด)

| หน้า | ไฟล์ | สเต็ปในเส้นทาง Journey |
|---|---|---|
| หน้าแรก | `index.html` | Hero / ทางเข้า |
| Climate Time Machine | `climate-time-machine.html` | SEE |
| 7 Eco Learning Zones | `eco-learning-zones.html` | UNDERSTAND |
| Solar Learning Pavilion | `solar-pavilion.html` | EXPERIENCE |
| Future Comparison | `future-comparison.html` | CHOOSE |
| Climate Simulator | `climate-simulator.html` | SIMULATE |
| Impact & Learning Journey | `impact-journey.html` | IMPACT |
| Energy Walk | `energy-walk.html` | ACTION |

เมนูบน (Top Nav), แถบไอคอนด้านซ้าย (Journey rail) และเมนูมือถือ (hamburger) ถูก generate ให้เหมือนกันทุกหน้า และไฮไลต์หน้าปัจจุบันอัตโนมัติ — ปุ่ม CTA ต่าง ๆ เชื่อมไปหน้าที่เกี่ยวข้องจริง (เช่น "START YOUR JOURNEY" → Climate Time Machine, "APPLY MY SCENARIO" → Climate Simulator)

## ทดสอบก่อน deploy (ในเครื่อง)

ไม่ต้องติดตั้งอะไรเพิ่ม เปิดไฟล์ `index.html` ในเบราว์เซอร์ได้เลย หรือรันเซิร์ฟเวอร์เล็ก ๆ เพื่อให้ลิงก์ทำงานเหมือนบนเว็บจริง:

```bash
cd denso-eco-park-website
python3 -m http.server 8080
```

แล้วเปิด http://localhost:8080

## Deploy ขึ้น Vercel

ไม่ต้องมี `vercel.json` หรือ build command ใด ๆ — เป็น static site ล้วน ๆ

**วิธีที่ 1 — ผ่านเว็บ Vercel:**
1. ไปที่ https://vercel.com/new
2. เลือก "Deploy" แบบ Upload folder แล้วลากโฟลเดอร์นี้เข้าไป หรือ push ขึ้น GitHub แล้ว import repo
3. Framework Preset เลือก "Other" — Vercel จะเสิร์ฟไฟล์ static ให้เอง

**วิธีที่ 2 — ผ่าน CLI:**

```bash
npm i -g vercel
cd denso-eco-park-website
vercel --prod
```

## หมายเหตุสิ่งที่ยังไม่ได้ทำ (ถ้าต้องการให้ทำต่อ บอกได้)

- เนื้อหายังเป็นภาษาอังกฤษทั้งหมด (ตามต้นฉบับดีไซน์) ยังไม่ได้แปลเป็นไทย
- ลิงก์ footer (Privacy Policy, Terms of Service, Sustainability Report) ยังเป็นหน้า placeholder เพราะต้นฉบับไม่มีเนื้อหาจริงให้
- รูปพื้นหลังบางจุดใช้ URL รูปจาก Google (`lh3.googleusercontent.com`) ที่มากับไฟล์ export ของ Stitch — ถ้าต้องการความเสถียรระยะยาว แนะนำให้ดาวน์โหลดมาเก็บไว้ในโปรเจกต์เอง แล้วเปลี่ยน path เป็นไฟล์ local แทน
