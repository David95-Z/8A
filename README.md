#include <stdio.h>
#include <string.h>

int main() {

    // Encryption and Decryption matrices (predefined)
    int encryptKey[3][3] = {
        {6, 24, 1},
        {13, 16, 10},
        {20, 17, 15}
    };

    int decryptKey[3][3] = {
        {8, 5, 10},
        {21, 8, 21},
        {21, 12, 8}
    };

    char message[20];
    int plain[3], cipher[3], decrypted[3];
    int i, j, temp;

    printf("\nEnter a 3-letter UPPERCASE plain text (A-Z only): ");
    scanf("%s", message);

    // Convert characters to numbers (A=0, B=1, ..., Z=25)
    for (i = 0; i < 3; i++) {
        plain[i] = message[i] - 'A';
    }

    // Encrypt: Multiply with encryption key
    for (i = 0; i < 3; i++) {
        temp = 0;
        for (j = 0; j < 3; j++) {
            temp += encryptKey[i][j] * plain[j];
        }
        cipher[i] = temp % 26;
    }

    // Show encrypted message
    printf("\nEncrypted Text: ");
    for (i = 0; i < 3; i++) {
        printf("%c", cipher[i] + 'A');
    }

    // Decrypt: Multiply with decryption key
    for (i = 0; i < 3; i++) {
        temp = 0;
        for (j = 0; j < 3; j++) {
            temp += decryptKey[i][j] * cipher[j];
        }
        decrypted[i] = temp % 26;
    }

    // Show decrypted message
    printf("\nDecrypted Text: ");
    for (i = 0; i < 3; i++) {
        printf("%c", decrypted[i] + 'A');
    }

    printf("\n");
    return 0;
}
