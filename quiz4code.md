'''
_foobar:
push ebp
mov ebp, esp
sub esp, 16

mov eax, DWORD[ebp+8]
mov DWORD[ebp-4], eax

mov eax, DWORD[ebp+12]
mov DWORD[ebp-8], eax

mov eax,DWORD[ebp+16]
mov DWORD[ebp-12], eax

mov eax, [ebp-4]
mov ebx,[ebp-8]
mov edx, [ebp-12]
lea eax,[ebx+eax]
lea eax, [edx+eax]
mov DWORD[ebp-16], eax
leave 
ret
section .text
	global _start
_start:
mov eax,[x]
push eax
mov eax,[y]
push eax
mov eax,[z]
push eax
call _foobar
mov [result],eax

mov eax,1
int 0x80

section .data
x dd 3
y dd 6
z dd 8

segment .bss
result resb 1
'''
