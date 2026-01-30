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

STEP-1: Read the plain text and key from the user.

STEP-2: Split the plain text into groups of length three.

STEP-3: Arrange the keyword in a 3*3 matrix.

STEP-4: Multiply the two matrices to obtain the cipher text of length three.

STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```
#include <stdio.h>
#include <string.h>

int main()
{
    unsigned int a[3][3] = {{6, 24, 1}, {13, 16, 10}, {20, 17, 15}}; // encryption key
    unsigned int b[3][3] = {{8, 5, 10}, {21, 8, 21}, {21, 12, 8}};   // decryption key
    int i, j, t;
    unsigned int c[3], d[3];
    char msg[4]; // buffer for 3 chars + null terminator

    printf("Enter plain text (3 letters): ");
    scanf("%3s", msg);

    // Ensure the message has exactly 3 characters
    if (strlen(msg) != 3)
    {
        printf("Error: The plain text must be exactly 3 letters.\n");
        return 1;
    }

    // Convert plain text to numerical values (A=0,...,Z=25)
    for (i = 0; i < 3; i++)
    {
        c[i] = msg[i] - 'A';
        printf("%d ", c[i]); // debugging: show numeric
    }

    // Encrypt the message using matrix 'a'
    for (i = 0; i < 3; i++)
    {
        t = 0;
        for (j = 0; j < 3; j++)
        {
            t += a[i][j] * c[j];
        }
        d[i] = t % 26;
    }

    // Output encrypted cipher text
    printf("\nEncrypted Cipher Text: ");
    for (i = 0; i < 3; i++)
    {
        printf("%c", d[i] + 'A');
    }

    // Decrypt the message using matrix 'b'
    for (i = 0; i < 3; i++)
    {
        t = 0;
        for (j = 0; j < 3; j++)
        {
            t += b[i][j] * d[j];
        }
        c[i] = t % 26;
    }

    // Output decrypted cipher text
    printf("\nDecrypted Cipher Text: ");
    for (i = 0; i < 3; i++)
    {
        printf("%c", c[i] + 'A');
    }

    getchar();
    return 0;
}
```
## OUTPUT
<img width="401" height="134" alt="image" src="https://github.com/user-attachments/assets/aedb2b2a-dcd3-4950-a436-b5d4b0a4bf6d" />



## RESULT
The program implementing the Hill cipher for encryption and decryption has been successfully 
executed, and the results have been verified.
