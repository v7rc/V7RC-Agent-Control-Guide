# Session Example

## User request
Move the mecanum robot forward slowly and show ready status.

## Agent reasoning summary
- active profile: mecanum_basic
- supported intent: move_forward_slow
- safe method: SRT
- led intent: ready_led

## Output
- motion command: `SRT1500160015001500#`
- led command: `LED0F0A0F0A0F0A0F0A#`
