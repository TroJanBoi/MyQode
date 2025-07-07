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
  - สั่งให้ มอเตอร์ M1/M2 หมุนตามเข็มนาฬิกา ด้วยความเร็ว 80
  - 🧠 เหมาะสำหรับควบคุมล้อซ้าย/ขวาแยกกันได้
  - clockwise = หมุนตามเข็มนาฬิกา
  - anticlockwise = หมุนทวนเข็มนาฬิกา
  
  ตัวอย่างใช้งานร่วมกัน
  ```plaintext
  set onboard motor M1 anticlockwise speed 80
  set onboard motor M2 clockwise speed 80
  ```
  → มอเตอร์ซ้ายหมุนทวนเข็ม, มอเตอร์ขวาหมุนตามเข็ม → หุ่นยนต์เคลื่อนที่ตรงไป
  - ถ้าอยากให้หุ่นยนต์ “เลี้ยวซ้าย” → ปรับให้ M1 หยุด, M2 หมุน
  - ถ้าอยากให้ “หมุนอยู่กับที่” → M1 กับ M2 หมุนสวนกัน
  
  ```plaintext
   stop moving
  ```
  - คำสั่งหยุด การเคลื่อนไหวทั้งหมด ของมอเตอร์ที่กำลังทำงานอยู่
  - 🧠 ปลอดภัยเมื่อจบคำสั่งหรือมีเหตุฉุกเฉิน

## Light
  ```plaintext
  set onboard [double/left/right] light to color [...]
  ```
  ใช้เพื่อกำหนดสีให้กับไฟ LED ที่อยู่ "บนบอร์ด" (ไม่ใช่โมดูลต่อภายนอก)
  - double: ควบคุม ไฟทั้ง 2 ดวง (ซ้ายและขวา) พร้อมกัน
  - left  : ควบคุมเฉพาะ ไฟดวงซ้าย
  - right : ควบคุมเฉพาะ ไฟดวงขวา

  ```plaintext
  set onboard [double/left/right] light to color R 0 G 0 B 0
  ```
  - R [Red]
  - G [Green]
  - B [Blue]

## Sound
  ```plaintext
  play note C4 for Half beats
  ```
  - ### Note
    - C4, D4, E4, F4, G4, A4, B4 — โน้ตระดับเสียงที่ใช้บ่อย
    - ยังมี C5, D5,... ขึ้นไป (เสียงสูงขึ้น)
    - และ C3, D3,... ต่ำลง (เสียงทุ้ม)
  - ### Beat Duration
    - `Whole` = 1 จังหวะเต็ม
    - `Half` = ครึ่งจังหวะ
    - `Quarter` = ¼ จังหวะ
    - `Eighth, Sixteenth` = ยิ่งสั้นลง

## Control
   ```plaintext
    wait (1) secs
   ```
  - `รอเวลา`: หยุดการทำงานชั่วคราวตามเวลาที่กำหนด (หน่วยเป็นวินาที)
  
  ```plaintext
   repeat (10)
  ```
  - `ทำซ้ำจำนวนครั้งที่กำหนด`: สั่งให้คำสั่งในบล็อกทำงาน 10 ครั้ง (หรือจำนวนที่ระบุ)

  ```plaintext
  forever
  ```
  - `ทำซ้ำไม่รู้จบ`: ใช้สำหรับคำสั่งที่ต้องทำซ้ำตลอดเวลา เช่น ตรวจจับเซ็นเซอร์, ควบคุมมอเตอร์ ฯลฯ

  ```plaintext
  if (เงื่อนไข) then
  ```
  - `ถ้า...ให้ทำ...`: ใช้ตรวจสอบเงื่อนไข ถ้าเป็นจริง (true) จะทำคำสั่งในบล็อกนี้
    
  ```plaintext
   if (เงื่อนไข) then else
  ```
  - `ถ้า...ให้ทำ..., ถ้าไม่ใช่ให้ทำอีกอย่าง`: ใช้ตัดสินใจ 2 ทาง เช่น:
    ```plaintext
     if (เสียง > 50) then → เปิดไฟ
     else → ปิดไฟ
    ```

  ```plaintext
  wait until (เงื่อนไข)
  ```
  - `รอจนกว่าเงื่อนไขจะเป็นจริง`: โปรแกรมจะหยุดค้างไว้ จนกว่าเงื่อนไขที่กำหนดจะเกิดขึ้นจริง เช่น:
    ```plaintext
    wait until (ปุ่มถูกกด)
    ```

  ```plaintext
  repeat until (เงื่อนไข)
  ```
  - `ทำซ้ำจนกว่าเงื่อนไขจะเป็นจริง`: คล้ายกับ while not เช่น:
    ```plaintext
    repeat until (พบเส้นสีดำ)
      เดินหน้า
    ```

## Sensor
  - ### 🎯 Event Trigger
     ```plaintext
      when onboard button pressed
     ```
     - เริ่มทำงานเมื่อปุ่มบนบอร์ดถูกกด

  - ### 📏 การวัดระยะ / เส้นทาง
    ```plaintext
    read ultrasonic sensor port2
    ```
    - อ่านระยะจาก เซ็นเซอร์อัลตราโซนิก (วัดระยะห่าง)

    ```plaintext
    read line follower sensor port2
    ```
    - อ่านค่าจาก เซ็นเซอร์ตรวจเส้น (ซ้าย-ขวา)

    ```plaintext
    port2 line follower sensor left [bright] right [bright] ?
    ```
    - `port2`         : พอร์ตที่ต่อเซ็นเซอร์ Line Follower (ให้เปลี่ยนตามพอร์ตที่ใช้จริง เช่น port1)
    - `left bright`   : เซ็นเซอร์ฝั่งซ้ายตรวจพบพื้น สว่าง
    - `right bright`  : เซ็นเซอร์ฝั่งขวาตรวจพบพื้น สว่าง
    - `?`             : เป็นบล็อกชนิด Boolean (จริง/เท็จ) สำหรับใช้ในเงื่อนไข if
    - ตัวเลือกในแต่ละด้าน
      - `bright` : พื้นที่สว่าง (เช่น พื้นสีขาว) -> หุ่นยนต์อยู่นอกเส้น
      - `dark`   : พื้นที่มืด (เช่น เส้นสีดำ) -> หุ่นยนต์อยู่บนเส้น

    🧠 ตัวอย่างการใช้งาน
    ตรวจสอบว่าเซ็นเซอร์ ซ้าย-ขวา เจอพื้นขาวทั้งคู่:
    ```plaintext
    if port2 line follower sensor left bright right bright ?
      → ให้เดินหน้า
    ```

    ถ้าเซ็นเซอร์ขวาเจอสีดำ ให้เลี้ยวขวา:
    ```plaintext
    if port2 line follower sensor left bright right dark ?
      → หมุนไปทางขวา
    ```
  - ### 🔊 เสียง / แสง
    ```plaintext
    read sound sensor port2
    ```
    อ่านระดับเสียงจากเซ็นเซอร์เสียง

    ```plaintext
    read light sensor port2
    ```
    อ่านระดับความสว่างจากเซ็นเซอร์แสง

  - ### 🕵️‍♂️ ตรวจจับการเคลื่อนไหว / อุณหภูมิ
    ```plaintext
    read PIR motion sensor port2
    ```
    → ตรวจจับการเคลื่อนไหว (คนเดินผ่าน)

    ```plaintext
    read temperature sensor port2
    ```
    → อ่านอุณหภูมิจากเซ็นเซอร์วัดอุณหภูมิ
  
    ```plaintext
    read humidity sensor port2
    ```
    → อ่านความชื้นในอากาศ

  - ### 🔄 ทิศทางและการหมุน
    ```plaintext
    read port2 gyro sensor X angle
    ```
    → อ่านค่ามุมเอียงจาก Gyro sensor ในแกน X, Y หรือ Z

  - ### 🎨 ตรวจจับสี / สัมผัส
    ```plaintext
    port2 color sensor detect colorless ?
    ```
    → ตรวจสอบว่าเซ็นเซอร์ตรวจพบสีที่กำหนดหรือไม่

    ```plaintext
    port2 get the key value of the touch pad
    ```
    → อ่านค่าปุ่มที่ถูกสัมผัสจาก Touch Pad

    ```plaintext
    port2 is the touch pad button 1 pressed?
    ```
    → ตรวจสอบว่า ปุ่มที่ 1 บน Touch Pad ถูกกดหรือไม่

## Extension
  - ### 🔘 รีเลย์ (Relay)
    ```plaintext
    set relay port2 to open/close
    ```
    → เปิด/ปิดวงจรไฟฟ้าผ่านโมดูลรีเลย์ (ใช้ควบคุมอุปกรณ์ไฟฟ้าแรงสูง)

  - ### 🧲 เซ็นเซอร์แม่เหล็ก / การสัมผัส / การกระแทก
    ```plaintext
    port2 hall switch detects magnet
    ```
    → ตรวจจับแม่เหล็กด้วยเซ็นเซอร์ Hall Effect

    ```plaintext
    port2 when touch button is pressed
    ```
    → ตรวจจับว่าปุ่มสัมผัส (Touch Sensor) ถูกกด

    ```plaintext
    port2 when knock sensor triggers
    ```
    → ตรวจจับแรงกระแทกจาก Knock Sensor

  - ### เซ็นเซอร์การเคลื่อนไหว/เอนเอียง
    ```plaintext
    port2 when mercury sensor triggers
    ```
    → ตรวจจับการเคลื่อนไหว/เอนจาก Mercury Tilt Sensor

    ```plaintext
    port2 when tilt sensor triggers
    ```
    → ตรวจจับการเอียงจาก Tilt Sensor

    ```plaintext
    port2 when infrared sensor triggers
    ```
    → ตรวจจับวัตถุหรือความเคลื่อนไหวผ่าน Infrared Sensor
    
  - ### ไฟ RGB LED
    ```plaintext
    set RGB LED port2 to open/close
    ```
    → เปิดหรือปิดไฟ RGB ที่พอร์ต 2

  - ### 💧🌡️ เซ็นเซอร์วัดค่าต่าง ๆ
    ```plaintext
    port2 water level sensor value (mm)
    ```
    → อ่านค่าระดับน้ำจาก Water Level Sensor
    
    ```plaintext
    port2 temperature sensor value
    ```
    → อ่านค่าอุณหภูมิ
    
    ```plaintext
    port2 potentiometer value
    ```
    → อ่านค่าความต้านทานจากปุ่มหมุน (Potentiometer)
    
    ```plaintext
    read temperature sensor port2
    ```
    → อ่านอุณหภูมิ (อีกบล็อกที่เหมือนกัน แต่ต่างรูปแบบ)
    
    ```plaintext
    read humidity sensor port2
    ```
    → อ่านค่าความชื้น

  - ### ⚙️ เซอร์โวมอเตอร์ & การแยกเฉดสี
    ```plaintext
    set servo port2 angle to 0
    ```
    → สั่งให้เซอร์โวมอเตอร์หมุนไปที่มุมที่กำหนด เช่น 0°, 90°, 180°
    
    ```plaintext
    port2 gray scale sensor value
    ```
    → อ่านค่า เฉดสีเทา (Grayscale) สำหรับตรวจเส้น/พื้นผิว

## Operators
  - ### คำนวณ (Arithmetic) 
    `+`: บวก
    `-`: ลบ
    `*`: คูณ
    `/`: หาร
    📌 ใช้ร่วมกับค่าตัวเลข เช่น ความเร็ว, มุม, ค่าจากเซ็นเซอร์ ฯลฯ

  - ### เปรียบเทียบ (Comparison)
    `>`: มากกว่า
    `=`: เท่ากับ
    `<`: น้อยกว่า
    📌 ใช้ใน `if` หรือ `wait until` เพื่อตัดสินใจตามเงื่อนไข

  - ### ตรรกะ (Logical)
    `and` : จริงเมื่อทั้ง 2 เงื่อนไขเป็นจริง
    `or`  : จริงเมื่อมีอย่างน้อย 1 เงื่อนไขเป็นจริง
    `not` : ตรงข้ามกับเงื่อนไข (not true = false)

  
