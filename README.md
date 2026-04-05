# ARTIS Telegram Bot ☀️

## ไฟล์ทั้งหมด
```
artis-bot/
├── index.js      ← Code หลัก
├── package.json  ← Dependencies
├── vercel.json   ← Config สำหรับ Vercel
└── README.md     ← ไฟล์นี้
```

---

## ขั้นตอน Deploy (น้อง Dev ทำ)

### 1. เพิ่ม User ใน WHITELIST
เปิด index.js แก้ตรงนี้

```javascript
const WHITELIST = {
  123456789: { name: 'Art', role: 'admin', verified: true },
  987654321: { name: 'Dev1', role: 'dev', verified: false },
  555555555: { name: 'Ops1', role: 'ops', verified: false },
};
```

หา User ID ได้โดยส่งข้อความหา @userinfobot ใน Telegram

### 2. Push ขึ้น GitHub
```bash
git init
git add .
git commit -m "ARTIS Bot v1.0"
git remote add origin https://github.com/[username]/artis-bot.git
git push -u origin main
```

### 3. Deploy บน Vercel
1. ไปที่ vercel.com → New Project
2. Import GitHub repo artis-bot
3. ใส่ Environment Variables:

```
TELEGRAM_BOT_TOKEN = [Token จาก @BotFather]
CLAUDE_API_KEY     = [Claude API Key]
ARTIS_PIN          = [PIN ที่ต้องการ เช่น 2024]
```

4. กด Deploy → รอ 1-2 นาที
5. Copy URL ที่ได้ เช่น https://artis-bot.vercel.app

### 4. ตั้ง Webhook
เปิด browser แล้วไปที่ URL นี้ (แก้ให้ตรง)

```
https://api.telegram.org/bot[TELEGRAM_BOT_TOKEN]/setWebhook?url=https://artis-bot.vercel.app
```

ถ้าขึ้น {"ok":true} แปลว่าสำเร็จแล้ว

### 5. ทดสอบ
เปิด Telegram → หา Bot ที่สร้างไว้ → พิมพ์ /start

---

## Role Permissions

| Role  | ใช้ได้ |
|-------|--------|
| admin | ทุกอย่าง |
| dev   | DEV, SA, INFRA, JIGSAW |
| ops   | PAYO, JUNE, SCT, DECISION |

---

## Trigger Examples

```
DECISION × SCT — ควรรับ partner ญี่ปุ่นไหม?
BA × PAYO — เขียน user story สำหรับระบบสั่งซื้อ
PEOPLE × ทีม — ประเมินพนักงานคนนี้
DEV × Jigsaw — review code นี้ให้หน่อย
```

---

*ARTIS Bot v1.0 ☀️*
