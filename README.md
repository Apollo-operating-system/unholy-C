I'll post docs soon but here is some example code:

10 main
20 int x = 1
30 int target = 5
40 print "Starting program with target: " target
50 goto A

A10 incrementFunction /M
A20 print "In LaTeX function A: x = " x
A30 x = x + 1
A40 x_{n+1} = x_n + 1
A50 if x >= target goto B
A60 goto C if x < target
A70 goto main

B10 checkFunction /C
B20 print "In function B: Checking x = " x
B30 if x >= target goto M1
B40 goto A
B50 return

C10 displayFunction /C
C20 print "In function C: Displaying x = " x
C30 if x == 2 goto B
C40 x = x + 1
C50 if x == 3 goto M1
C60 goto A

10 asmFunction /A /S1
20 print "In ASM function D: Executing ASM code"
30 MOV AX, x
40 ADD AX, 5
50 MOV x, AX
60 if x >= target goto A1
70 goto main

A10 endFunction /C
A20 print "In function E: Ending program"
A30 END /VM 

