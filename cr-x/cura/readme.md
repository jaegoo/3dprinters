
* Default Printer GCode

;START GCODE
G21 ;metric values
G28 ;home all
;G29
M420 S1
G90 ;absolute positioning
M107 ;start with the fan off
T0 ;Switch to Extruder 1
G1 F3000 X5 Y10 Z0.2 ;move to prime start position
G92 E0 ;reset extrusion distance
G1 F600 X160 E15 ;prime nozzle in a line
G1 F5000 X180 ;quick wipe
G92 E0 ;reset extrusion distance


;END GCODE
M104 S0  ;hotend off
M140 S0  ;bed off
G92 E0
G1 F2000 E-100  ;retract filament 100mm
G92 E0
G1 F3000 X0 Y270  ;move bed for easy part removal
M84  ;disable steppers

;EXTRUDER START GCODE
T0 ;switch to extruder 1
G92 E0 ;reset extruder distance
G1 F2000 E93 ;load filament
G92 E0 ;reset extruder distance
M104 S{material_print_temperature}

;EXTRUDER END GCODE
G92 E0 ;reset extruder distance
G1 F800 E-5 ;short retract
G1 F2400 X295 Y265 ;move near prime tower
G1 F2000 E-93 ;long retract for filament removal
G92 E0 ;reset extruder distance
G90