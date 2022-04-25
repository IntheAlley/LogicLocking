# Objectives
* DC setup file
  * specify the technology library file
  * search path directories
* read in hierarchical designs
* apply a constraints file
* save the disign

# Commands
``` dc_shell
read_verilog {A.v B.v TOP.v}
current_design TOP
link
check_design
write -f ddc -hier -out unmpd/TOP.ddc
source -echo -verbose TOP.con
check_timing
compile -boundary -scan -map high
report_constraint -all_violators
change_names -rule verilog -hier
write -f verilog -hier -out mpd/TOP.v
write -f ddc -hier -out mpd/TOP.ddc
exit
```