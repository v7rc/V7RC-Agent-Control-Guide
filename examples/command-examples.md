# Command Examples

## Neutral motion
Intent:
- neutral_motion

Command:
```text
SRT1500150015001500#
```

## Stop using custom command
Intent:
- stop

Command:
```text
CMDSTOP           #
```

## Reset robot
Intent:
- reset_robot

Command:
```text
CMDRESET          #
```

## Front LEDs solid red
Intent:
- error_led

Command:
```text
LEDF00AF00AF00AF00A#
```

## Front LEDs blinking blue
Intent:
- waiting_led

Command:
```text
LED00F500F500F500F5#
```

## Mecanum forward slow
Intent:
- move_forward_slow

Command:
```text
SRT1500160015001500#
```

## Mecanum backward
Intent:
- move_backward

Command:
```text
SRT1500140015001500#
```

## Mecanum strafe left
Intent:
- strafe_left

Command:
```text
SRT1400150015001500#
```

## Mecanum strafe right
Intent:
- strafe_right

Command:
```text
SRT1600150015001500#
```

## Mecanum turn left
Intent:
- turn_left

Command:
```text
SRT1500150015001400#
```

## Mecanum turn right
Intent:
- turn_right

Command:
```text
SRT1500150015001600#
```

## Mecanum forward-left
Intent:
- move_forward_left

Command:
```text
SRT1400160015001500#
```

## Tank forward slow
Intent:
- move_forward_slow

Command:
```text
SRT1600160015001500#
```

## Tank turn left
Intent:
- turn_left

Command:
```text
SRT1400160015001500#
```

Important:
These examples assume:
- for mecanum: Channel1 = left/right movement, Channel2 = forward/backward movement, Channel4 = turning
- for tank: Channel1 = left drive, Channel2 = right drive
- Channel3 is reserved or unused unless explicitly documented
