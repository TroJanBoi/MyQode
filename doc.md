# MyQode

## Show
  - ### 🔢 Digital Tube (จอ LED ตัวเลขแบบ 7-segment)
    ```python
    Digital tube port2 show number 0
    ```
    → แสดงตัวเลข "0" บน จอ Digital Tube ที่ต่ออยู่ที่พอร์ต 2
    
    ```python
    Digital tube port2 start timing 0 min 0 s
    ```
    → เริ่มนับเวลาบน Digital Tube เป็นตัวจับเวลา โดยกำหนดเวลาเริ่มต้นได้
    
    ```python
    Digital tube port2 timer zero
    ```
    → รีเซ็ตหรือล้างค่าตัวจับเวลาให้กลับไปเป็น 0
    
    ```python
    Digital tube port2 show the current time
    ```
    → แสดงเวลาปัจจุบัน (หากบอร์ดมี real-time clock หรือจำลองได้)

  - ### LED Matrix (จอแสดงผลเป็นจุด Dot Matrix)
    ```python
    set LED Matrix port2 show image
    ```
    → แสดงรูปภาพ (icon, emoji, pattern) บน LED Matrix ที่ต่อพอร์ต 2

    ```python
    show drawing port2 draw 😀
    ```
    → แสดงภาพอีโมจิ/สัญลักษณ์ ที่เลือกไว้ (เช่น หน้ายิ้ม) บน LED Matrix

  - ### RGB Matrix (จอแสดงผลแบบมีสี)
    
    ```python
    set RGB Matrix port2 show image
    ```
    → แสดงรูปภาพสีบน RGB LED Matrix ที่ต่อกับพอร์ต 2
    
## Event
  ```python
  when program begin
  ```
  - จุดเริ่มต้นของโปรแกรม

## Motion
  ```python
  run forward at speed 45
  ```
  - สั่งให้หุ่นยนต์ เคลื่อนที่ไปข้างหน้า ด้วยความเร็ว 45
  - สามารถเลือก ไปข้างหลัง ซ้าย ขวา ได้

  ```python
   set onboard motor M1 clockwise, speed 80
  ```
  - สั่งให้ มอเตอร์ M1 หมุนตามเข็มนาฬิกา ด้วยความเร็ว 80
  - 🧠 เหมาะสำหรับควบคุมล้อซ้าย/ขวาแยกกันได้
  
  ```python
   stop moving
  ```
  - คำสั่งหยุด การเคลื่อนไหวทั้งหมด ของมอเตอร์ที่กำลังทำงานอยู่
  - 🧠 ปลอดภัยเมื่อจบคำสั่งหรือมีเหตุฉุกเฉิน
