## Basics of Linux
**Shortcut** | **Operations** |
:---------------:|:--------------:|
`cd`            | Change Directory
`mkdir`           | Make Directory
`ls`            | list
`ped`            | path
`vi`            | vi text editor

# Getting Started with RTL
```bash vi full_adder.v ##Initating the name of the vi file
```

```verilog
module full adder (A,B,C_in,C_out, Clock, SUM);
input A,B;
input Clock, Cin;
output reg [3:0] SUM;
output reg C_out;
reg [3:0] reg1, reg2, sum_i;
reg cin, c_out;
always @ (posedge Clock)
begin
reg1 <= A;
reg2 <= B;
c_in <= C_in;
end
always @ (posedge Clock)
begin
SUM <= sum_1; C_out <= c_out;
end
always @ *
begin
{c_out, sum_i} = regl + reg2 + c_in;
end
endmodule
```
