# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```
#include <stdio.h> 
#include <string.h> 
#include <stdlib.h> 
void encryptRailFence(char str[], int rails, char encrypted[]) { 
int i, j, len, count, code[100][1000]; 
len = strlen(str); 
// Initialize the code array to 0 
for (i = 0; i < rails; i++) { 
for (j = 0; j < len; j++) { 
code[i][j] = 0; 
} 
} 
count = 0; 
j = 0; 
while (j < len) { 
if (count % 2 == 0) { // Moving down the rails 
for (i = 0; i < rails && j < len; i++) { 
code[i][j] = (int)str[j]; 
j++; 
} 
} else { // Moving up the rails 
for (i = rails - 2; i > 0 && j < len; i--) { 
code[i][j] = (int)str[j]; 
j++; 
} 
} 
count++; 
} 
int pos = 0; 
for (i = 0; i < rails; i++) { 
for (j = 0; j < len; j++) { 
if (code[i][j] != 0) { 
encrypted[pos++] = code[i][j]; 
} 
} 
} 
encrypted[pos] = '\0';  
} 
void decryptRailFence(char str[], int rails, char decrypted[]) { 
int i, j, len, count, code[100][1000], pos = 0; 
len = strlen(str); 
// Initialize the code array to 0 
for (i = 0; i < rails; i++) { 
for (j = 0; j < len; j++) { 
code[i][j] = 0; 
} 
} 
count = 0; 
j = 0; 
while (j < len) { 
if (count % 2 == 0) {  
for (i = 0; i < rails && j < len; i++) { 
code[i][j] = 1; 
j++; 
} 
} else {  
for (i = rails - 2; i > 0 && j < len; i--) { 
code[i][j] = 1; 
j++; 
} 
} 
count++; 
} 
for (i = 0; i < rails; i++) { 
for (j = 0; j < len; j++) { 
if (code[i][j] == 1) { 
code[i][j] = str[pos++]; 
} 
} 
} 
pos = 0; 
count = 0; 
j = 0; 
while (j < len) { 
if (count % 2 == 0) { // Moving down the rails 
for (i = 0; i < rails && j < len; i++) { 
if (code[i][j] != 0) { 
decrypted[pos++] = code[i][j]; 
} 
j++; 
} 
} else { // Moving up the rails 
for (i = rails - 2; i > 0 && j < len; i--) { 
if (code[i][j] != 0) { 
decrypted[pos++] = code[i][j]; 
} 
j++; 
} 
} 
count++; 
} 
decrypted[pos] = '\0';  
} 
int main() { 
char str[1000], encrypted[1000], decrypted[1000]; 
int rails; 
printf("Simulating Rail Fence Cipher\n"); 
printf("Enter a Secret Message: "); 
fgets(str, sizeof(str), stdin); 
str[strcspn(str, "\n")] = 0;  
printf("Enter number of rails: "); 
scanf("%d", &rails); 
encryptRailFence(str, rails, encrypted); 
printf("Encrypted Message: %s\n", encrypted); 
decryptRailFence(encrypted, rails, decrypted); 
printf("Decrypted Message: %s\n", decrypted); 
return 0; 
}
```

## OUTPUT
<img width="1431" height="886" alt="Screenshot 2026-02-02 111644" src="https://github.com/user-attachments/assets/8911c2a8-40f3-4dcf-88de-c3d89a8c851b" />


## RESULT
The implementation of rail fence transposition technique using c program is successful.
