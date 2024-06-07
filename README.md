# Zadaca6-8086

Дадени се две низи, VEK1 и VEK2, кои имаат N1, односно N2 16 битни елементи, соодветно. Во низата
VEK1 се бараат елементи од низата N2 на следниот начин. Најпрво последователно во низата VEK1 се бара
првиот елемент од низата VEK2; ако се пронајде, постапката завршува при првото пронаоѓање. Во
спротивно, последователно во низата VEK1 се бара вториот елемент од низата VEK2; ако се пронајде,
постапката завршува при првото пронаоѓање на вториот елемент итн. Ако постапката заврши успешно, во
локациите P1 и P2 треба да се запише вредноста на индексот на елементите од VEK1 и VEK2 кои се
поклопиле инаку на двете локации треба да стои -1 (FFFFh). Напишете асемблерска програма во машинскиот
јазик на процесорот 8086.


**Resenie:** 

```
DATA SEGMENT
 P1 DW -1
 P2 DW -1
 N1 DW ?
 N2 DW ?
 VEK1 DW 1000h DUP (?)
 VEK2 DW 1000h DUP (?)
DATA ENDS
CODE SEGMENT
 ASSUME CS:CODE, DS:DATA
START: MOV AX,DATA ;Иницијализација
 MOV DS,AX
 MOV DI,0 ; Индекс DI за VEK2
 MOV BX,N2 ; Иниц. на бројач за VEK2
 VRTI_V2: MOV SI,0 ; Индекс SI за VEK1
 MOV CX,N1 ; Иниц. на бројач за VEK1
 MOV AX,VEK2[DI] ; во AX е она што се бара
VRTI_V1: CMP AX,VEK1[SI] ; споредување
 JZ IZLEZ ; ако се исти, излез.
 ADD SI,2 ; инаку на следниот податок од VEK1
LOOP VRTI_V1
 ADD DI,2 ; следниот од VEK2
 DEC BX
 JNZ VRTI_V2
 HLT ;крај, не е пронајден
IZLEZ: SHR SI ; крај, пронајден
 SHR DI
 MOV P1,SI
 MOV P2,DI
 HLT
CODE ENDS
 END START
```

![Screenshot (1)](https://github.com/slavko444/Zadaca6-8086/blob/main/Zadaca6%208086%20code.png)

**Develop by:**

[Slavko Srebrenoski ](https://github.com/slavko444)


**Subject**

Microcomputer's systems

**Built With**

This project is built using the following tools:

- [8086 simulator](https://emu8086-microprocessor-emulator.en.softonic.com/?ex=RAMP-2046.0): Assembler and emulator for the Intel 8085 microprocessor.

**Getting Started**

To get a local copy up and running, follow these steps.

**Prerequisites**

In order to run this project you need:

A working computer
Connection to internet
Setup

**How to Run**

To run the program, you need an 8086 emulator or assembler. You can use emulators like DOSBox or TASM (Turbo Assembler). Here's how to run the program using 8086 simulator:

1. Download and install 8086 simulator from [here](https://emu8086-microprocessor-emulator.en.softonic.com/?ex=RAMP-2046.0).
2. Clone this repository to your local machine.
3. Open 8086 simulator and load the `Zadaca6 8086 code.asm` file.
4. Assemble the code by pressing the Assemble button.
5. Run the program by pressing the Run button or by pressing F10.
