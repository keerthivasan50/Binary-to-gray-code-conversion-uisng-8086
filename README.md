# Binary to Gray Code Conversion (8086 Assembly)

## Aim
To convert a binary number into its equivalent Gray code using 8086 Assembly language.

- *Input:* Binary number in register AL  
- *Output:* Gray code stored in memory location 1200H

---

## Algorithm
1. Store the binary number in register AL.  
2. Copy the binary number into another register BL.  
3. Right shift the original binary number by 1 (AL >> 1).  
4. XOR the shifted value with the original copy (BL XOR AL).  
5. Store the result in memory (BX → [SI]).  
6. Terminate the program.

---

## Flowchart
![WhatsApp Image 2025-09-29 at 11 54 54_ac3ff53c](https://github.com/user-attachments/assets/92f6a9c2-0e6d-49d4-b896-3954b5a54ee4)
---

## 8086 Assembly Code

```asm
CODE SEGMENT
ASSUME CS:CODE,DS:CODE
ORG 1000H

MOV AL,09H      ; Load binary number 09H
MOV BL,AL       ; Copy AL to BL
SHR AL,1        ; Shift AL right by 1
XOR BL,AL       ; BL XOR AL → Gray code
MOV SI,1200H    ; Memory location to store result
MOV [SI],BX     ; Store Gray code in memory
MOV AH,4CH      ; Terminate program
INT 21H

CODE ENDS
END
```

## Manual Calculation

*Input binary:* 09H → 00001001

| Binary           | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 |
|-----------------|---|---|---|---|---|---|---|---|
| Shift Right by 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| XOR with original| 0 | 0 | 0 | 0 | 1 | 1 | 0 | 1 |

*Gray code:* 00001101 → *0DH*

---

## Memory Output

Memory at 1200H after program execution:
1200: 0D 00


- 0D = Gray code of 09H  
- Program works for 8-bit binary inputs (0–FFH)

---

## Execution Steps (MASM → LINK → DEBUG)

1. Assemble the code:  
```bash
masm bg.asm;
```
Link the object file:
```bash
link bg.obj;
```
Run the program in DEBUG:
```bash
debug bg.exe
```
Execute the program:
```nginx
Copy code
g
```
Dump the memory at 1200H to see the result:
```yaml
d 1200
```

## Summary

| Feature          | Value                     |
|-----------------|---------------------------|
| Input            | 09H (00001001)            |
| Gray Code Output | 0DH (00001101)            |
| Memory Address   | 1200H                     |
| Registers used   | AL, BL, SI, BX, AH       |

## Result
Thus, the binary number 09H was successfully converted to Gray code 0DH. The Gray code was stored in memory at 1200H.
The experiment demonstrates the correct use of bitwise shift and XOR operations in 8086 assembly to convert any 8-bit binary number into its Gray code equivalent.
