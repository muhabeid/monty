0x19. C - Stacks, Queues - LIFO, FIFO 0. push, pall mandatory Implement the push and pall opcodes.

Monty byte code files

Files containing Monty byte codes usually have the .m extension. Most of the industry uses this standard but it is not required by the specification of the language. There is not more than one instruction per line. There can be any number of spaces before or after the opcode and its argument:

julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ cat -e bytecodes/000.m push 0$ push 1$ push 2$ push 3$ pall $ push 4$ push 5 $ push 6 $ pall$ julien@ubuntu:/0x19. Stack (LIFO) & queue (FIFO)$ Monty byte code files can contain blank lines (empty or made of spaces only, and any additional text after the opcode or its required argument is not taken into account:

julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ cat -e bytecodes/001.m push 0 Push 0 onto the stack$ push 1 Push 1 onto the stack$ $ push 2$ push 3$ pall $ $ $ $ push 4$ $ push 5 $ push 6 $ $ pall This is the end of our program. Monty is awesome!$ julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ The monty program

Usage: monty file where file is the path to the file containing Monty byte code If the user does not give any file or more than one argument to your program, print USAGE: monty file, followed by a new line, and exit with the status EXIT_FAILURE If, for any reason, it's not possible to use read the file, print Error: Can't open file , followed by a new line, and exit with the status EXIT_FAILURE where is the name of the file If the file contains an invalid instruction, print L<line_number>: unknown instruction , followed by a new line, and exit with the status EXIT_FAILURE where is the line number where the instruction appears. Line numbers always start at 1 The monty program runs the bytecodes line by line and stop if: it executed properly every line of the file or it finds an error in the file or an error occured If you can't malloc anymore, print Error: malloc failed, followed by a new line, and exit with status EXIT_FAILURE. You have to use malloc and free and are not allowed to use any other function from man malloc The push opcode

The opcode push pushes an element to the stack.

Usage: push where is an integer if is not an integer or if there is no argument to push, print the message L<line_number>: usage: push integer, followed by a new line, and exit with the status EXIT_FAILURE where is the line number in the file You don't have to deal with overflows. Use the atoi function The pall opcode

The opcode pall prints all the values on the stack, starting from the top of the stack.

Usage pall Format: see example If the stack is empty, don't print anything julien@ubuntu:/0x19. Stack (LIFO) & queue (FIFO)$ cat -e bytecodes/00.m push 1$ push 2$ push 3$ pall$ julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ ./monty bytecodes/00.m 3 2 1 julien@ubuntu:~/0x18. Stack (LIFO) & queue (FIFO)$

pint mandatory Implement the pint opcode.
The pint opcode

The opcode pint prints the value at the top of the stack, followed by a new line.

Usage: pint If the stack is empty, print L<line_number>: can't pint, stack empty, followed by a new line, and exit with the status EXIT_FAILURE julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ cat bytecodes/06.m push 1 pint push 2 pint push 3 pint julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ ./monty bytecodes/06.m 1 2 3 julien@ubuntu:~/0x18. Stack (LIFO) & queue (FIFO)$ 2. pop mandatory Implement the pop opcode.

The pop opcode

The opcode pop removes the top element of the stack.

Usage: pop if the stack is empty, print L<line_number>: can't pop an empty stack, followed by a new line, and exit with the status EXIT_FAILURE julien@ubuntu:/0x19. Stack (LIFO) & queue (FIFO)$ cat bytecodes/07.m push 1 push 2 push 3 pall pop pall pop pall pop pall julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ ./monty bytecodes/07.m 3 2 1 2 1 1 julien@ubuntu:~/0x18. Stack (LIFO) & queue (FIFO)$ 3. swap mandatory Implement the swap opcode.

The swap opcode

The opcode swap swaps the top two elements of the stack.

Usage: swap If the stack is less than two element long, print L<line_number>: can't swap, stack too short, followed by a new line, and exit with the status EXIT_FAILURE julien@ubuntu:/0x19. Stack (LIFO) & queue (FIFO)$ cat bytecodes/09.m push 1 push 2 push 3 pall swap pall julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ ./monty bytecodes/09.m 3 2 1 2 3 1 julien@ubuntu:~/0x18. Stack (LIFO) & queue (FIFO)$ 4. add mandatory Implement the add opcode.

The add opcode

The opcode add adds the top two elements of the stack.

Usage: add If the stack is less than two element long, print L<line_number>: can't add, stack too short, followed by a new line, and exit with the status EXIT_FAILURE The result is stored in the second top element of the stack, and the top element is removed, so that at the end: the top element of the stack contains the result the stack is one element shorter julien@ubuntu:~/0x18. Stack (LIFO) & queue (FIFO)$ cat bytecodes/12.m push 1 push 2 push 3 pall add pall

julien@ubuntu:/0x19. Stack (LIFO) & queue (FIFO)$ ./monty bytecodes/12.m 3 2 1 5 1 julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ 5. nop mandatory Implement the nop opcode.

The nop opcode

The opcode nop doesn't do anything.

Usage: nop 6. sub #advanced Implement the sub opcode.

The sub opcode

The opcode sub subtracts the top element of the stack from the second top element of the stack.

Usage: sub If the stack is less than two element long, print L<line_number>: can't sub, stack too short, followed by a new line, and exit with the status EXIT_FAILURE The result is stored in the second top element of the stack, and the top element is removed, so that at the end: the top element of the stack contains the result the stack is one element shorter julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ cat bytecodes/19.m push 1 push 2 push 10 push 3 sub pall julien@ubuntu:/0x19. Stack (LIFO) & queue (FIFO)$ ./monty bytecodes/19.m 7 2 1 julien@ubuntu:~/0x18. Stack (LIFO) & queue (FIFO)$ 7. div #advanced Implement the div opcode.

The div opcode

The opcode div divides the second top element of the stack by the top element of the stack.

Usage: div If the stack is less than two element long, print L<line_number>: can't div, stack too short, followed by a new line, and exit with the status EXIT_FAILURE The result is stored in the second top element of the stack, and the top element is removed, so that at the end: the top element of the stack contains the result the stack is one element shorter If the top element of the stack is 0, print L<line_number>: division by zero, followed by a new line, and exit with the status EXIT_FAILURE 8. mul #advanced Implement the mul opcode.

The mul opcode

The opcode mul multiplies the second top element of the stack with the top element of the stack.

Usage: mul If the stack is less than two element long, print L<line_number>: can't mul, stack too short, followed by a new line, and exit with the status EXIT_FAILURE The result is stored in the second top element of the stack, and the top element is removed, so that at the end: the top element of the stack contains the result the stack is one element shorter 9. mod #advanced Implement the mod opcode.

The mod opcode

The opcode mod computes the rest of the division of the second top element of the stack by the top element of the stack.

Usage: mod If the stack is less than two element long, print L<line_number>: can't mod, stack too short, followed by a new line, and exit with the status EXIT_FAILURE The result is stored in the second top element of the stack, and the top element is removed, so that at the end: the top element of the stack contains the result the stack is one element shorter If the top element of the stack is 0, print L<line_number>: division by zero, followed by a new line, and exit with the status EXIT_FAILURE 10. comments #advanced Every good language comes with the capability of commenting. When the first non-space character of a line is #, treat this line as a comment (don't do anything).

pchar #advanced Implement the pchar opcode.
The pchar opcode

The opcode pchar prints the char at the top of the stack, followed by a new line.

Usage: pchar The integer stored at the top of the stack is treated as the ascii value of the character to be printed If the value is not in the ascii table (man ascii) print L<line_number>: can't pchar, value out of range, followed by a new line, and exit with the status EXIT_FAILURE If the stack is empty, print L<line_number>: can't pchar, stack empty, followed by a new line, and exit with the status EXIT_FAILURE julien@ubuntu:/0x19. Stack (LIFO) & queue (FIFO)$ cat bytecodes/28.m push 72 pchar julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ ./monty bytecodes/28.m H julien@ubuntu:~/0x18. Stack (LIFO) & queue (FIFO)$ 12. pstr #advanced Implement the pstr opcode.

The pstr opcode

The opcode pstr prints the string starting at the top of the stack, followed by a new line.

Usage: pstr The integer stored in each element of the stack is treated as the ascii value of the character to be printed The string stops where: the stack is over the value of the element is 0 the value of the element is not in the ascii table If the stack is empty, print only a new line julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ cat bytecodes/31.m push 1 push 2 push 3 push 4 push 0 push 110 push 0 push 110 push 111 push 116 push 114 push 101 push 98 push 108 push 111 push 72 pstr julien@ubuntu:/0x19. Stack (LIFO) & queue (FIFO)$ ./monty bytecodes/31.m Holberton julien@ubuntu:~/0x18. Stack (LIFO) & queue (FIFO)$ 13. rotl #advanced Implement the rotl opcode.

The rotl opcode

The opcode rotl rotates the stack to the top.

Usage: rotl The top element of the stack becomes the last one, and the second top element of the stack becomes the first one rotl never fails julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ cat bytecodes/35.m push 1 push 2 push 3 push 4 push 5 push 6 push 7 push 8 push 9 push 0 pall rotl pall julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ ./monty bytecodes/35.m 0 9 8 7 6 5 4 3 2 1 9 8 7 6 5 4 3 2 1 0 julien@ubuntu:~/0x19. Stack (LIFO) & queue (FIFO)$ 14. rotr #advanced Implement the rotr opcode.

The rotr opcode

The opcode rotr rotates the stack to the bottom.

Usage: rotr The last element of the stack becomes the top element of the stack rotr never fails 15. stack, queue #advanced Implement the stack and queue opcodes.

The stack opcode

The opcode stack sets the format of the data to a stack (LIFO). This is the default behavior of the program.

Usage: stack The queue opcode

The opcode queue sets the format of the data to a queue (FIFO).

Usage: queue When switching mode:

the top of the stack becomes the front of the queue the front of the queue becomes the top of the stack julien@ubuntu:/0x18. Stack (LIFO) & queue (FIFO)$ cat bytecodes/47.m queue push 1 push 2 push 3 pall stack push 4 push 5 push 6 pall add pall queue push 11111 add pall julien@ubuntu:/0x19. Stack (LIFO) & queue (FIFO)$ ./monty bytecodes/47.m 1 2 3 6 5 4 1 2 3 11 4 1 2 3 15 1 2 3 11111 julien@ubuntu:~/0x18. Stack (LIFO) & queue (FIFO)$ 16. Holberton #advanced Write a Brainf*ck script that prints Holberton, followed by a new line.

All your Brainfck files should be stored inside the brainfuck sub directory You can install the bf interpreter to test your code: sudo apt-get install bf Read: Brainfck julien@ubuntu:/brainfuck$ bf 1000-holberton.bf Holberton julien@ubuntu:/brainfuck$ 17. Add two digits #advanced Add two digits given by the user.

Read the two digits from stdin, add them, and print the result The total of the two digits with be one digit-long (<10) julien@ubuntu:/brainfuck$ bf ./1001-add.bf 81 9julien@ubuntu:/brainfuck$ 18. Multiplication #advanced Multiply two digits given by the user.

Read the two digits from stdin, multiply them, and print the result The result of the multiplication will be one digit-long (<10) julien@ubuntu:/braifuck$ bf 1002-mul.bf 24 8julien@ubuntu:/braifuck$ 19. Multiplication level up #advanced Multiply two digits given by the user. Read the two digits from stdin, multiply them, and print the result, followed by a new line julien@ubuntu:/brainfuck$ bf 1003-mul.bf 77 49 julien@ubuntu:/brainfuck$