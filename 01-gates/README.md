# Digital-electronics-1

GitHub repository: [https://github.com/vmensik/Digital-electronics-1/](https://github.com/vmensik/Digital-electronics-1/)

EDA Playground: [https://www.edaplayground.com/x/Mj6V](https://www.edaplayground.com/x/Mj6V)
## Code examples
### VHDL Code for both excercises
```VHDL
------------------------------------------------------------------------
--
-- Example of basic OR, AND, XOR gates.
-- Nexys A7-50T, Vivado v2020.1, EDA Playground
--
-- Copyright (c) 2019-2020 Tomas Fryza
-- Dept. of Radio Electronics, Brno University of Technology, Czechia
-- This work is licensed under the terms of the MIT license.
--
------------------------------------------------------------------------

library ieee;               -- Standard library
use ieee.std_logic_1164.all;-- Package for data types and logic operations

------------------------------------------------------------------------
-- Entity declaration for basic gates
------------------------------------------------------------------------
entity gates is
    port(
        a_i    : in  std_logic;         -- Data input
        b_i    : in  std_logic;         -- Data input
        c_i	   : in  std_logic;
        --for_o  : out std_logic;         -- OR output function
        --fand_o : out std_logic;         -- AND output function
        --fxor_o : out std_logic          -- XOR output function
        f_o    : out std_logic;
        fnand_o : out std_logic;
        fnor_o  : out std_logic;
        dist_law1_l : out std_logic;
        dist_law1_r : out std_logic;
        
        dist_law2_l : out std_logic;
        dist_law2_r : out std_logic
    );
end entity gates;

------------------------------------------------------------------------
-- Architecture body for basic gates
------------------------------------------------------------------------
architecture dataflow of gates is
begin
    -- for_o  <= a_i or b_i;
    --fand_o <= a_i and b_i;
    --fxor_o <= a_i xor b_i;
    f_o <= ((not b_i) and a_i) or ((not c_i) and (not b_i));
    fnor_o <= (((b_i nor (a_i nor a_i)) nor (c_i nor b_i)) nor ((b_i nor (a_i nor a_i)) nor (c_i nor b_i)));
    fnand_o <= (((b_i nand b_i) nand ((a_i nand a_i) nand (a_i nand a_i))) nand ((c_i nand c_i) nand (b_i nand b_i)));
    
    dist_law1_l <=  ((a_i and b_i) or (a_i and c_i));
    dist_law1_r <=  (a_i and (b_i or c_i));
    
    dist_law2_l <= ((a_i or b_i) and (a_i or c_i));
    dist_law2_r <= (a_i or (b_i and c_i));
    

end architecture dataflow;

```



### Screenshot of signal waveforms

![A](https://github.com/vmensik/Digital-electronics-1/blob/main/01-gates/Capture.PNG)