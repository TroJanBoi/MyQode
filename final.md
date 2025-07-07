# Final

## 🟡 1. เริ่มต้นโปรแกรม
  ```blocks
  when program begin
    forever
  ```
  - เมื่อเปิดเครื่อง โปรแกรมจะเริ่มทำงานทันที
  - คำสั่ง `forever` ทำให้โค้ดข้างในทำงานวนลูปไปเรื่อย ๆ ตลอดเวลา

## 🟦 2. เดินตรงเมื่ออยู่บนเส้นดำ (Line Follower)
  ```blocks
  if line follower left = dark AND right = dark
  → run forward at speed 70
  ```
  - เซ็นเซอร์ซ้าย–ขวาตรวจจับเส้นสีดำทั้งคู่ → วิ่งตรงด้วยความเร็วปกติ

## 🟦 3. เลี้ยวขวา
  ```blocks
  if left = dark AND right = bright
  → set onboard motor M1 clockwise, speed 30
  ```
  - หมุนมอเตอร์ M1 (ขวา) ช้า ๆ → ทำให้เลี้ยวขวา

## 🟦 4. เลี้ยวซ้าย
  ```blocks
  if left = bright AND right = dark
  → set onboard motor M2 clockwise, speed 30
  ```
  - หมุนมอเตอร์ M2 (ซ้าย) ช้า ๆ → ทำให้เลี้ยวซ้าย

## 🟩 5. ขึ้นเนิน
  ```blocks
  if gyro sensor X > 10
  → run forward at speed 90
  ```
  - ถ้าหุ่นเอียงไปด้านหลัง (ขึ้นเนิน) → เพิ่มความเร็วเพื่อปีนเนินได้ง่ายขึ้น

## 🟩 6. ลงเนิน
  ```blocks
  if gyro sensor X < -10
  → run forward at speed 30
  ```
  - ถ้าหุ่นเอียงไปด้านหน้า (ลงเนิน) → ลดความเร็วเพื่อความปลอดภัยและไม่เร็วเกินไป

## 🟩 7. ทางขรุขระ
  ```blocks
  if abs of (gyro sensor X) > 3 OR abs of (gyro sensor Y) > 3
  → run forward at speed 20
  ```
  - 💡 ใช้ abs (ค่าสัมบูรณ์) เพราะเราสนใจแค่ว่าแกนเปลี่ยนมาก (ไม่สนว่าบวกหรือลบ)

## 🟥 8. ถึงเส้นจบ (เจอเส้นขาวทั้งซ้ายและขวา)
  ```blocks
  if left = bright AND right = bright
  → stop moving
  → set onboard double light to color green
  → play note C4 for half beats
  ```
  - หุ่นหยุดเมื่อถึงจุดสิ้นสุดของแทร็ก
  - เล่นเอฟเฟกต์จบงาน เช่น เปิดไฟ + เล่นเสียง

    ![image](https://github.com/user-attachments/assets/8563634c-aa97-446c-b085-0371f35b5765)








