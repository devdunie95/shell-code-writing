`section .data
  msg db '/bin/sh' ; db stands for define byte, 

section .text
  global _start   ; Needed for compiler, comparable to int main()
_start:             ; entry point for commands
     ; use the write syscall to print 'Hello world!' to stdout
     mov eax, 4          ; move syscall 4(write) to the eax register
     mov ebx, 1          ; move field descriptor for stdout to ebx
     mov ecx, msg        ; move the memory address of our string to ecx
     mov edx, 13         ; move the length of the string to edx
     int 0x80       ; execute the syscall
 
     ; use the exit syscall to exit the program with a status code of 0
     mov eax, 1          ; mov syscall 1(exit) to the eax register)
     mov ebx, 0          ; move status code to ebx
     int 0x80       ; execute the syscall
section .data
     msg: db “Hello world!”, 0x0a  ; the string, followed by a new line character`
