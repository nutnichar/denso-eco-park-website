# RE:IMAGINE — DENSO Eco Park

เว็บไซต์ static HTML ของ DENSO Eco Park สร้างตาม **Digital Platform Specification** (ผัง 9 หน้า + Visual Design System) พร้อมนำขึ้น Vercel ได้ทันทีโดยไม่ต้องตั้งค่าอะไรเพิ่ม (ไม่มี build step)

## โครงสร้างเว็บไซต์ (9 หน้าตาม Site Map + 1 หน้าย่อย)

| หน้า | ไฟล์ | หมายเหตุ |
|---|---|---|
| Home | `index.html` | Hero + ทางเข้าเว็บ |
| Impact | `impact.html` | ข้อมูล Climate Change จริง พร้อม Source/Citation ครบทุกจุด |
| 7 Zones | `zones.html` | การ์ดสรุป 7 โซน |
| ↳ Zone 03 detail | `zone-03-energy.html` | Energy Dojo — รวม Solar Pavilion + Energy Walk (มี interactive demo) |
| Climate Time Machine | `climate-time-machine.html` | สไลด์ 1980→2050 พร้อมเลือก Scenario (Business as Usual / Climate Action) |
| Live Dashboard | `live-dashboard.html` | รวมข้อมูลพลังงาน/น้ำ/ขยะ/คาร์บอน/สปีชีส์ ทุกตัวเลขติดป้าย "Simulation" |
| My Impact | `my-impact.html` | Personal Climate Action Card — **UI เท่านั้น** ยังไม่ต่อระบบ QR/บัญชีจริง |
| Eco Habit | `eco-habit.html` | Checklist พฤติกรรมที่บ้าน บันทึกด้วย localStorage ในเครื่องผู้ใช้เท่านั้น |
| Online Learning | `online-learning.html` | บทเรียนสั้น 7 บท ผูกกับแต่ละโซน |
| Climate Challenge | `climate-challenge.html` | Badge + Leaderboard — **UI เท่านั้น** ยังไม่ต่อระบบ sign-in/คะแนนจริง |

เมนูบน, แถบไอคอนซ้าย (Journey rail) และเมนูมือถือ (hamburger) generate ให้เหมือนกันทุกหน้า ไฮไลต์หน้าปัจจุบันอัตโนมัติ ใช้ไอคอนชุดเดียวกันทั้งเว็บ (Material Symbols Outlined)

## ทำตาม Checklist ของสเปกแล้ว

- [x] ครบ 9 หน้าตาม Site Map (+ 1 หน้าย่อยรายละเอียดโซน)
- [x] สีหลัก `#DC0032` (DENSO Red) ใช้สม่ำเสมอทั้งเว็บ เป็นสีเดียวที่ใช้เน้น
- [x] ไอคอนทุกหน้าเป็นชุดเดียวกัน (Material Symbols Outlined)
- [x] ตัวเลขที่ยังไม่มีข้อมูลจริงติดป้าย "Simulation" ทุกจุด (Live Dashboard, My Impact, Climate Time Machine ช่วงปี 2027–2050)
- [x] หน้า Impact มี Source/Citation ครบ (ลิงก์ไปแหล่งข่าวจริงทุกจุด)
- [x] ไม่มีลักษณะคล้าย Government Website, การ์ดต่อหน้าไม่แน่นเกินไป, Animation น้อย
- [x] ทดสอบบนมือถือแล้ว (มือถือ ≤767px ใช้เมนู hamburger)
- [ ] **Hero ใช้ภาพจริงของ Eco Park/โรงงาน** — ยังรอไฟล์รูปจากผู้ใช้ ตอนนี้ใช้ gradient สี DENSO Red แทนชั่วคราว (ดูหัวข้อถัดไป)

## สิ่งที่ยังไม่เสร็จ / รอดำเนินการต่อ

1. **รูปภาพจริง** — หน้า Home และ Zone detail ต่าง ๆ ยังใช้ gradient สีแทนภาพถ่ายจริงของ Eco Park อยู่ ส่งไฟล์รูปมาแล้วจะเปลี่ยนให้ทันที
2. **My Impact / Climate Challenge** — ตามที่ตกลงกันไว้ สร้างหน้า UI ไว้ครบแล้วแต่ยังไม่ต่อระบบบัญชีผู้ใช้/QR/leaderboard จริง (ต้องมี backend เพิ่มเติม)
3. **Zone 01, 02, 04, 05, 06, 07** — มีการ์ดสรุปและคำอธิบายเพิ่มเติมในหน้า `zones.html` แล้ว แต่ยังไม่มีหน้ารายละเอียดแยกแบบ Zone 03 (ถ้าต้องการเพิ่มบอกได้)
4. เนื้อหาเว็บเป็นภาษาอังกฤษทั้งหมด ยังไม่ได้แปลไทย

## ทดสอบก่อน deploy (ในเครื่อง)

```bash
cd denso-eco-park-website
python3 -m http.server 8080
```

แล้วเปิด http://localhost:8080

## Deploy ขึ้น Vercel

ไม่ต้องมี `vercel.json` หรือ build command ใด ๆ — เป็น static site ล้วน ๆ เชื่อมกับ GitHub repo `nutnichar/denso-eco-park-website` ไว้แล้ว push ขึ้น `main` เมื่อไหร่ Vercel deploy ให้อัตโนมัติ

## Sources อ้างอิงในหน้า Impact

- WMO — "WMO confirms 2024 as warmest year on record at about 1.55°C above pre-industrial level" (ม.ค. 2025)
- Copernicus Climate Change Service
- UNICEF Thailand
- ThaiCyclopedia — Thai Floods 2024
- Krungsri Research — Drought and Flood Risk 2024
- DENSO Group Sustainability Report (ตัวเลข resource recycling rate 99.96% เป็นข้อมูลระดับกลุ่มบริษัท ไม่ใช่ตัวเลขเฉพาะไซต์พาร์คนี้)
