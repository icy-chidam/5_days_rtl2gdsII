## Basics of Linux
**Shortcut** | **Operations** |
:---------------:|:--------------:|
`cd`            | Change Directory
`mkdir`           | Make Directory
`ls`            | list
`ped`            | path
`vi`            | vi text editor

# Getting Started with RTL

```bash
vi full_adder.v ##Initating the name of the vi file
```
### RTL Code

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
### Test_becnch code
```verilog
`timescale 1ns/1ns
`include "full_adder_rtl.v" // includes the module definition for the full adder
module testbench;
	reg [3:0] A, B;
	reg Clock, C_in;
	wire [3:0] SUM;
	wire C_out;

// Instantiate the module under test
full_adder dut  (.A(A),.B(B),.Clock(Clock),.C_in(C_in),.SUM(SUM),.C_out(C_out));

// Clock generation
always #5 Clock = ~Clock; // Clock signal with a period of 10 ns

// Stimulus
initial begin
	 $fsdbDumpvars();

//Tool specific command. Creates novas.fsdb file. Used for waveform generation
//// Reset inputs
//
	A <= 0; B <= 0; C_in <= 0; Clock <= 0;
// Apply test cases
	#20 A <= 4'b0001; B <= 4'b0001; C_in <= 0; // 1 + 1 = 2 (binary: 10)
	$display("A = %b, B = %b, C_in = %b, SUM = %b, C_out = %b", A, B, C_in, SUM, C_out);

	#20 A <= 4'b0110; B <= 4'b1010; C_in <= 1; // 6 + 10 + 1 = 17 (binary: 10001)
	$display("A = %b, B = %b, C_in = %b, SUM = %b, C_out = %b", A, B, C_in, SUM, C_out);

	#20 A <= 4'b1000; B <= 4'b1111; C_in <= 1; // 8 + 15 + 1 = 24 (binary: 11000)
	$display("A = %b, B = %b, C_in = %b, SUM = %b, C_out = %b", A, B, C_in, SUM, C_out);

	#100 $finish;

	end
endmodule
```
Key Changes:
- `include "rtl_file.v"
-  $fsdbDumpvars();

# Into Verdi
This software helps to visulaize and debug the test_bench file.
### Scripts to run Verdi
* vcs -full64 full_adder.v -debug_access+all -lca -kdb
* vcs -full64 full_adder_tb.v -debug_access+all -lca -kdb
* ./simv Verdi
* verdi -ssf novas.fsdb -nologo

<img width="1600" height="819" alt="Screenshot from 2025-02-18 13-45-29" src="https://github.com/user-attachments/assets/ac56c646-4dc0-4f93-8cd0-dc5c5bca5ce7" />

# Design Compiler
<img width="1546" height="433" alt="Screenshot from 2025-02-18 16-20-58 (1)" src="https://github.com/user-attachments/assets/d3ff4274-42df-4ff9-86de-0dcc95db3329" />
Block Diagram
<img width="1600" height="559" alt="Screenshot from 2025-02-18 16-19-43" src="https://github.com/user-attachments/assets/df3b6d8c-0f5b-4525-b315-283176cb13ee" />

Cell Report
<img width="1600" height="900" alt="Screenshot from 2025-02-19 15-01-45" src="https://github.com/user-attachments/assets/338a9484-cb03-46f3-b1f6-f93f3030e5f6" />

# IC Compiler-II
<img width="1556" height="667" alt="Screenshot from 2025-02-19 16-02-15" src="https://github.com/user-attachments/assets/f8bd1604-8d8f-4c4e-8cab-0033bf168d33" />

Floorplanning & Routing

<img width="1595" height="723" alt="Screenshot from 2025-02-20 12-50-26 (1)" src="https://github.com/user-attachments/assets/eee17d0c-c16b-426b-b3fc-95bd6aad5ba6" />

