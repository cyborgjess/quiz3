[factorial.txt](https://github.com/user-attachments/files/21808857/factorial.txt)# quiz3

factorial of 7: 5040


[Uploasection .data
    x       dd 7
    result  dd 1
    newline db 10, 0

section .bss
    buffer  resb 16

section .text
    global _start

_start:
    mov eax, [x]
    mov ebx, eax
    mov ecx, [result]

.factorial_loop:
    cmp ebx, 1
    jle .done
    imul ecx, ebx
    dec ebx
    jmp .factorial_loop

.done:
    mov eax, ecx
    mov edi, buffer + 15
    mov byte [edi], 0

.convert_loop:
    dec edi
    xor edx, edx
    mov ebx, 10
    div ebx
    add dl, '0'
    mov [edi], dl
    test eax, eax
    jnz .convert_loop

    mov eax, 4
    mov ebx, 1
    mov ecx, edi
    mov edx, buffer + 15
    sub edx, edi
    int 0x80

    mov eax, 4
    mov ebx, 1
    mov ecx, newline
    mov edx, 1
    int 0x80

    mov eax, 1
    xor ebx, ebx
    int 0x80
ding factorial.txt…]()

![quizfact](https://github.com/user-attachments/assets/ac536a67-3701-4ae5-baee-97563f2d986c)
