# โปรไฟล์พื้นฐาน Tank


## Metadata
- profile_name: tank_basic
- robot_type: tank_drive
- transport: BLE

## ลำดับความสำคัญ
1. CMD
2. SRT
3. SRV
4. SS8

## โมเดลการเคลื่อนที่
- Channel1: เลี้ยวซ้าย / ขวา
- Channel2: เดินหน้า / ถอยหลัง
- Channel3: สำรอง
- Channel4: สำรอง หรือ yaw trim ตาม firmware
- neutral_value: 1500
- safe_range: 1200-1800
- hard_range: 1000-2000
