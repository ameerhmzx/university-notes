- ## Performance
	- $$\text{Performance} = \dfrac {1} {\text{Execution Time}}$$
	- $X$ is n times faster than $Y$
		- id:: 627a38dd-af50-4544-af8d-e10d28c86d27
		  $$n = \dfrac {\text{PerformanceX}} {\text{PerformanceY}} = \dfrac{\text{ExecutionTimeX}}{\text{ExecutionTimeY}}$$
		- `Example`: Time taken to run a program
		  10s on A, 
		  15s on B
		  Execution Time B / Execution Time A = 15s / 10s = 1.5 = 1½
		  So A is 1½ times faster than B
	- Performance can be improved by
		- Reducing number of clock cycles
		- Increasing clock rate
		- Hardware designer must often trade off clock rate against cycle count
	- **Base Formulas**
		- $$\text{Cpu time} = \text{CPU Clock Cycles } * \text{ Clock Cycle Time}$$
		- $$\text{Clock Cycle Time} = \dfrac{1}{\text{Clock Rate}}$$
		- $$\text{Clock Cycles} = \text{Instruction Count} * \text{Cycles per Instruction (CPI)}$$
- ## Data Path
	- **Complete Diagram**
		- ![image.png](../assets/image_1652180681450_0.png)
	- **ALU Control Bits**
		- | **ALU control** | **Operation** |
		  | 000 | and |
		  | 001 | or |
		  | 010 | add |
		  | 110 | sub |
		  | 111 | slt |
		- | **Instruction** | **ALU op** | **Function Field** | **ALU Action** | **ALU Control bits** |
		  | LW / SW | 00 | xxxxxx | add | 010 |
		  | Branch (any) | 01 | xxxxxx | sub | 110 |
		  | add / sub / or / and / slt | 10 | relative function bits | add / sub / or / and / slt | *consult respective ALU Control |
	- **Control Unit Fields**
		- | **inst** | **RegDst** | **ALUsrc** | **Mem2Reg** | **RegWrite** | **MemRead** | **MemWrite** | **Branch** | **ALUop1** | **ALUop2** |
		  | R | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 |
		  | lw | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | 0 |
		  | sw | x | 1 | x | 0 | 0 | 1 | 0 | 0 | 0 |
		  | beq | x | 0 | x | 0 | 0 | 0 | 1 | 0 | 1 |