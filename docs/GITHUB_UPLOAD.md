# วิธีอัปโหลดขึ้น GitHub ให้รันได้ทันที

## 1) อัปโหลดไฟล์
อัปโหลดไฟล์/โฟลเดอร์ทั้งหมดใน ZIP นี้ไปที่ root ของ repo GitHub

ต้องเห็นโครงสร้างแบบนี้:

```text
.github/workflows/water-watch.yml
inburi_ai/
tests/
main_water.py
alert_water.py
requirements.txt
README.md
```

> สำคัญ: ต้องเป็น `.github/workflows/water-watch.yml` ไม่ใช่ไฟล์ชื่อ `.github\\workflows`

## 2) ตั้งค่า Secrets
ไปที่ GitHub repo → Settings → Secrets and variables → Actions → Secrets

เพิ่มอย่างน้อย:

```text
MAKE_WEBHOOK_URL = URL webhook จาก Make.com
```

ถ้าจะเปิด AI Council ให้เพิ่ม:

```text
GEMINI_API_KEY
ANTHROPIC_API_KEY
OPENAI_API_KEY
```

## 3) ตั้งค่า Variables
ไปที่ Settings → Secrets and variables → Actions → Variables

แนะนำ:

```text
DRY_RUN = false
SAFE_MODE = true
INBURI_BANK_LEVEL_MSL = 13.00
ALERT_COOLDOWN_MINUTES = 120
AI_COUNCIL_ENABLED = false
REQUEST_TIMEOUT_S = 20
```

ถ้าต้องการใช้ AI Council:

```text
AI_COUNCIL_ENABLED = true
```

## 4) ทดสอบรัน
ไปที่ Actions → Inburi Water Watch → Run workflow

ระบบจะ:

- ติดตั้ง dependencies
- รัน test
- สร้างรายงานน้ำ
- สร้าง PNG/SVG/JSON ใน artifact
- ส่งโพสต์ไป Make.com ถ้า `DRY_RUN=false` และมี `MAKE_WEBHOOK_URL`

## 5) ตารางรันอัตโนมัติ

- รายงานประจำวัน: 07:00, 13:00, 19:00 เวลาไทย
- แจ้งเตือนด่วน: ทุก 30 นาที

