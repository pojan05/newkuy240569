# Production Checklist

- [ ] โฟลเดอร์ `.github/workflows/` มีไฟล์ `water-watch.yml`
- [ ] ไม่มีไฟล์ `.env` ใน repo public
- [ ] ตั้ง `MAKE_WEBHOOK_URL` ใน GitHub Secrets แล้ว
- [ ] ตั้ง `DRY_RUN=false` ใน GitHub Variables แล้ว ถ้าต้องการโพสต์จริง
- [ ] ตั้ง `INBURI_BANK_LEVEL_MSL=13.00` แล้ว
- [ ] เปิด Actions และลอง Run workflow 1 รอบ
- [ ] ตรวจ artifact ใน Actions ว่ามี JSON/PNG/SVG
- [ ] ตรวจ Make.com ว่าได้รับ payload และโพสต์ได้จริง
