# SSC0108 - Prática-SD

Projeto 1: Latches, Flip-flops, and Registers.

# Softwares utilizados

Versão do Quartus: Quartus Prime 21.1 <br>
Versão ModelSim: ModelSim - Intel FPGA Starter Edition 10.5b <br>

## Part 1

RTL Viewer:

<div align ="center">
    <img src ="imgs/Part1_Img1.png" style="max-width: 100%;" alt="img1">
</div>

Technology Map Viewer:

<div align ="center">
    <img src ="imgs/Part1_Img2.png" style="max-width: 100%;" alt="img1">
</div>

Gráfico de ondas da simulação(Modelsim):

<div align ="center">
    <img src ="imgs/Part1_Img3.png" style="max-width: 100%;" alt="img1">
</div>

Codigo VHDL:

```
LIBRARY ieee;
USE ieee.std_logic_1164.all;

ENTITY part1 IS
 PORT ( Clk, R, S : IN STD_LOGIC;
	Q : OUT STD_LOGIC);
END part1;


ARCHITECTURE Structural OF part1 IS
 SIGNAL R_g, S_g, Qa, Qb : STD_LOGIC ;
 ATTRIBUTE KEEP : BOOLEAN;
 ATTRIBUTE KEEP OF R_g, S_g, Qa, Qb : SIGNAL IS TRUE;
BEGIN
 R_g <= R AND Clk;
 S_g <= S AND Clk;
 Qa <= NOT (R_g OR Qb);
 Qb <= NOT (S_g OR Qa);
 Q <= Qa;
END Structural;

```
<a href = "Block1.bdf">Link</a>
	
## Part 2

RTL Viewer:

<div align ="center">
    <img src ="imgs/Part2_Img1.png" style="max-width: 100%;" alt="img1">
</div>

Technology Map Viewer:

<div align ="center">
    <img src ="imgs/Part2_Img2.png" style="max-width: 100%;" alt="img1">
</div>

Gráfico de ondas da simulação(Modelsim):

<div align ="center">
    <img src ="imgs/Part2_Img3.png" style="max-width: 100%;" alt="img1">
</div>

Codigo VHDL:

```
LIBRARY ieee;
USE ieee.std_logic_1164.all; 

LIBRARY work;

ENTITY latchD IS 
	PORT
	(
		D :  IN  STD_LOGIC;
		CLK :  IN  STD_LOGIC;
		Qa :  OUT  STD_LOGIC
	);
END latchD;

ARCHITECTURE bdf_type OF latchD IS 

SIGNAL	SYNTHESIZED_WIRE_0 :  STD_LOGIC;
SIGNAL	SYNTHESIZED_WIRE_1 :  STD_LOGIC;
SIGNAL	SYNTHESIZED_WIRE_2 :  STD_LOGIC;
SIGNAL	SYNTHESIZED_WIRE_3 :  STD_LOGIC;
SIGNAL	SYNTHESIZED_WIRE_4 :  STD_LOGIC;


BEGIN 
Qa <= SYNTHESIZED_WIRE_4;



SYNTHESIZED_WIRE_2 <= NOT(CLK AND D);


SYNTHESIZED_WIRE_3 <= NOT(SYNTHESIZED_WIRE_0 AND CLK);


SYNTHESIZED_WIRE_4 <= NOT(SYNTHESIZED_WIRE_1 AND SYNTHESIZED_WIRE_2);


SYNTHESIZED_WIRE_1 <= NOT(SYNTHESIZED_WIRE_3 AND SYNTHESIZED_WIRE_4);


SYNTHESIZED_WIRE_0 <= NOT(D);



END bdf_type;

```

## Part 3

RTL Viewer:

<div align ="center">
    <img src ="imgs/Part3_Img1.png" style="max-width: 100%;" alt="img1">
</div>

Technology Map Viewer:

<div align ="center">
    <img src ="imgs/Part3_Img2.png" style="max-width: 100%;" alt="img1">
</div>


Codigo VHDL:

```
LIBRARY ieee;
USE ieee.std_logic_1164.all; 

LIBRARY work;

ENTITY masterslaveD IS 
	PORT
	(
		D :  IN  STD_LOGIC;
		clk :  IN  STD_LOGIC;
		Q :  OUT  STD_LOGIC
	);
END masterslaveD;

ARCHITECTURE bdf_type OF masterslaveD IS 

COMPONENT latchd
	PORT(D : IN STD_LOGIC;
		 CLK : IN STD_LOGIC;
		 Qa : OUT STD_LOGIC
	);
END COMPONENT;

SIGNAL	SYNTHESIZED_WIRE_0 :  STD_LOGIC;
SIGNAL	SYNTHESIZED_WIRE_1 :  STD_LOGIC;


BEGIN 



b2v_inst : latchd
PORT MAP(D => D,
		 CLK => SYNTHESIZED_WIRE_0,
		 Qa => SYNTHESIZED_WIRE_1);


b2v_inst1 : latchd
PORT MAP(D => SYNTHESIZED_WIRE_1,
		 CLK => clk,
		 Qa => Q);


SYNTHESIZED_WIRE_0 <= NOT(clk);



END bdf_type;

```

## Part 4

RTL Viewer:

<div align ="center">
    <img src ="imgs/Part4_Img1.png" style="max-width: 100%;" alt="img1">
</div>

Gráfico de ondas da simulação(Modelsim):

<div align ="center">
    <img src ="imgs/Part4_Img2.png" style="max-width: 100%;" alt="img1">
</div>

Codigo VHDL Principal:

```
LIBRARY ieee ;
USE ieee.std_logic_1164.all ;
ENTITY part4 IS
PORT ( D, Clk : IN STD_LOGIC ;
Q1,Q2,Q3 : OUT STD_LOGIC) ;
END part4 ;
ARCHITECTURE Behavior OF part4 IS
BEGIN
PROCESS ( D, Clk )
BEGIN
IF Clk = '1' THEN
Q1 <= D ;
END IF ;
IF rising_edge(Clk) THEN
Q2 <= D ;
END IF ;
IF falling_edge(Clk) THEN
Q3 <= D ;
END IF ;
END PROCESS ;
END Behavior ;


```
