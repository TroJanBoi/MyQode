```python
  when program begin
  set white_counter to 0
  forever
    if (abs of (read port2 gyro sensor X angle) > 3) or (abs of (read port2 gyro sensor Y angle) > 3)
      run forward at speed 20

    if (read port2 gyro sensor X angle) > 10
      run forward at speed 90

    if (read port2 gyro sensor X angle) < -10
      run forward at speed 30

    if (port2 line follower sensor left dark right bright ?)
      set onboard motor M1 clockwise speed 30

    if (port2 line follower sensor left bright right dark ?)
      set onboard motor M2 clockwise speed 30

    if (port2 line follower sensor left dark right dark ?)
      run forward at speed 70
      set white_counter to 0

    if (port2 line follower sensor left bright right bright ?)
      change white_counter by 1

      if (white_counter < 4)
        run forward at speed 40
        set onboard double light to color yellow
        play note D4 for quarter beats

      else if (white_counter > 3)
        wait (0.25) secs
        repeat until (port2 line follower sensor left dark right dark ?)
          stop moving
          set onboard double light to color green
          play note C4 for half beats
```
