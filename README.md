# Ex-3 IMPLEMENTATION OF HILL CIPHER
 
## AIM
To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often, the simple scheme  
A = 0, B = 1, ... Z = 25 is used, but this is not an essential feature of the cipher.

To encrypt a message, each block of *n* letters is multiplied by an invertible  
*n × n* matrix modulo 26.

To decrypt the message, each block is multiplied by the inverse of the matrix  
used for encryption.

The matrix used for encryption is the cipher key, and it should be chosen  
randomly from the set of invertible *n × n* matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. <br>
STEP-2: Split the plain text into groups of length three. <br>
STEP-3: Arrange the keyword in a 3*3 matrix.<br>
STEP-4: Multiply the two matrices to obtain the cipher text of length three. <br>
STEP-5: Combine all these groups to get the complete cipher text.<br>

## PROGRAM 
```java
public class HillCipher {

    static int[][] keyMat = {
            {1, 2, 1},
            {2, 3, 2},
            {2, 2, 1}
    };

    static int[][] invKeyMat = {
            {-1, 0, 1},
            { 2,-1, 0},
            {-2, 2,-1}
    };

    static final String ALPHABET = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";

    // Encrypt 3 characters
    static String encode(char a, char b, char c) {
        int posa = a - 'A';
        int posb = b - 'A';
        int posc = c - 'A';

        int x = posa * keyMat[0][0] + posb * keyMat[1][0] + posc * keyMat[2][0];
        int y = posa * keyMat[0][1] + posb * keyMat[1][1] + posc * keyMat[2][1];
        int z = posa * keyMat[0][2] + posb * keyMat[1][2] + posc * keyMat[2][2];

        return "" +
                ALPHABET.charAt(x % 26) +
                ALPHABET.charAt(y % 26) +
                ALPHABET.charAt(z % 26);
    }

    // Decrypt 3 characters
    static String decode(char a, char b, char c) {
        int posa = a - 'A';
        int posb = b - 'A';
        int posc = c - 'A';

        int x = posa * invKeyMat[0][0] + posb * invKeyMat[1][0] + posc * invKeyMat[2][0];
        int y = posa * invKeyMat[0][1] + posb * invKeyMat[1][1] + posc * invKeyMat[2][1];
        int z = posa * invKeyMat[0][2] + posb * invKeyMat[1][2] + posc * invKeyMat[2][2];

        return "" +
                ALPHABET.charAt((x % 26 + 26) % 26) +
                ALPHABET.charAt((y % 26 + 26) % 26) +
                ALPHABET.charAt((z % 26 + 26) % 26);
    }

    public static void main(String[] args) {

        String msg = "SecurityLaboratory";
        StringBuilder enc = new StringBuilder();
        StringBuilder dec = new StringBuilder();

        System.out.println("Simulation of Hill Cipher");
        System.out.println("Input message : " + msg);

        msg = msg.toUpperCase().replaceAll("\\s+", "");

        // Padding with X
        int n = msg.length() % 3;
        if (n != 0) {
            for (int i = 0; i < 3 - n; i++)
                msg += "X";
        }

        System.out.println("Padded message : " + msg);

        // Encryption
        for (int i = 0; i < msg.length(); i += 3) {
            enc.append(encode(
                    msg.charAt(i),
                    msg.charAt(i + 1),
                    msg.charAt(i + 2)
            ));
        }

        System.out.println("Encoded message : " + enc);

        // Decryption
        for (int i = 0; i < enc.length(); i += 3) {
            dec.append(decode(
                    enc.charAt(i),
                    enc.charAt(i + 1),
                    enc.charAt(i + 2)
            ));
        }

        System.out.println("Decoded message : " + dec);
    }
}


```

## OUTPUT
<img width="1617" height="933" alt="image" src="https://github.com/user-attachments/assets/055ceebd-565b-47b0-b32c-858aa3487c84" />

## RESULT
 Thus the implementation of ceasar cipher had been executed successfully.
