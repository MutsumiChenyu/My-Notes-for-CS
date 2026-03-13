**&     *    malloc     free**

16 Hexa-decimal 16进制
10 Decimal 10进制
2 Binary 2进制

& + AABB： Find the address of the "AABB"
\*p  ：Go to the address of something
Hints: the p is a pointer. p is the variable itself, not includes the "\*"

The pointer takes the place of 8 bytes (64 bits)  
1 byte is 8 bits

in printf, %p stands for the pointer

The "string"

string s = "HI!";  == char \*s ="HI!";

Actually, the string is a pointer which points at the address of the first character of the latter string

Compare them:
printf("%s\n",s): it will output the whole string.
printf("%p\n",s): it will output the address of string
printf("%p\n",\*s): it has syntax wrongs, \*s is a char actually, not a pointer.
printf("%s\n",\*s):it will output the first character of the string.

What is strcmp?

if says s1 == s2, it is definitely different since the address of two string cannot be the same.

copy.c
char \*s = "hi";
t = s
t[0] = toupper(t[0])

in fact, it will change the output for both t and s, since the address is not changed and for both t and s. But the corresponding thing is changed from hi to Hi.

\#include stdlib string library includes the malloc and free

malloc Apply for a piece of memory space
You must remember that how many bites you apply.

char *s = get_string("s:");
char *t =  malloc(strlen(s) + 1); Apply a memory space for the pointer "t"

Use loops to realize that t[i] = s[i+1]
Why s+1 here? Because you need to include the "/0" since you need to finish the string using the "/0"

At this time you do not create a t pointed at s, but a whole memory space you apply in the function malloc.

Not a good design when using function in a loop function, since you always call the same function times by times. You can declare the value of the function before the loop.

Actually a function called    strcpy(t,s); copying from s to t

**NULL** is a pointer pointed at the address "0"

free  
You need to give the asked memory back after you use the function malloc.

Eg:

char *t = malloc(strlen(s)+1);
......
free(t); // to free the memory you asked for in the former malloc

	int x[3];    ==   int *x  = malloc(3*sizeof(int))`  Ask for a malloc with 3 sizes of the standard input of "int"

A software called  Valgrind : Examine the memory errors in your codes
valgrind ./xxxx

AKA  the memory leak

Two concepts: "Stack栈" & "Heap堆"

Stack does not need you to free it, but it has a limit and fixed space for memory.

For example, int x[3]; is a typical memory assignment on the stack.

Heap need to be freed in time, but its memory space can be controlled by the coder of the programmer.

For example, **int \*x = malloc(sizeof(int))**; is assigned on the heap.

Be aware of the memory leak.
The array need a initial value.  When you define a variable but do not give it a explicit initial value, it will be the garbage value left in the memory before.

**Temporary variable**  (A third variable)
In order to change the position of 2 variables

void swap(int a, int b)
int temp = a;
a = b;
b = temp;    

Why it don't act effectively?
When you call a function and pass i 2 arguments, you send the copies of the values into the function, but actually not the arguments themselves.

So: Using pointers to solve the problem.  You cannot change the argument but change the inputted copies inside.

Machine code
Globals
Heap↓

Stack↑

void swap(int *a, int *b)
int temp = *a;
*a = *b;
*b = temp;    

When you call the function:
 swap(&x , &y); //input the address into the function

When you use pointers, it will change the real value of the arguments instead of the copies.

a & b ---->*a & *b 

Heap overflow
Stack overflow
Buffer overflow: A chunk of memory in the computer

How the cs50 library code works?

For The function "get_int"

int x;
printf("x:");
scanf("%i", &x);

char \*s;
printf......
scanf()

To introduce a outer file in C

FILE \*file = fopen("phonebook.csv", "a")
......
fprintf(file, "......");

fclose(file);

fopen的几种模式：
a 只写（追加）
r 只读
w 只写（覆盖）
**后加b**  ：以二进制方式

The usage of file-related functions
```C
size_t fread(void *ptr_output, size_t sizeofone, size_t wholenumber, FILE *input);
//fread is a function that transfrom the content from a piece of memory to another
//fread accept 4 arguments
//1.a pointer pointed at the memory will be put
//2.the length of the basic unit of the thing be written into
//3.the length of the whole thing will be transferred 
//4.the space of memory will be copied

//What is size_t?
```


