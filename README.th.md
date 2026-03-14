# คู่มือควบคุมหุ่นยนต์ V7RC สำหรับ AI Agent

Repository นี้จัดทำขึ้นเพื่อให้ AI Agent สามารถควบคุมหุ่นยนต์ในระบบ V7RC ได้อย่างปลอดภัยและมีมาตรฐาน

สิ่งที่เพิ่มจาก V7RC Protocol เดิม:
- การแมปฮาร์ดแวร์ของหุ่นยนต์
- นิยาม motion intent
- กฎความปลอดภัยสำหรับ AI Agent
- แนวทางเชื่อมต่อกับ OpenClaw
- robot profile แบบ YAML

## ภาษา

| ภาษา | ไฟล์ |
|---|---|
| English | `README.md` |
| 繁體中文 | `README.zh-TW.md` |
| 简体中文 | `README.zh-CN.md` |
| 日本語 | `README.ja.md` |
| ภาษาไทย | `README.th.md` |
| Bahasa Melayu | `README.ms.md` |

## โครงสร้าง

- `docs/` เอกสารอ่านสำหรับคน แยกตามภาษา
- `profiles/` YAML สำหรับ AI Agent / โปรแกรม
- `schemas/` JSON Schema สำหรับตรวจสอบ
- `examples/` ตัวอย่าง prompt และคำสั่ง
- `assets/` แผนภาพและไฟล์เสริม

## โปรไฟล์ที่มี

- `mecanum_basic`
- `tank_basic`

## โปรโตคอลต้นทาง

Official V7RC Protocol:
- https://github.com/v7rc/V7RC-Protocol

## License

MIT
