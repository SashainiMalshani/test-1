
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

// Function to encrypt the message using Caesar cipher
void encrypt(char *message, int key) {
    while (*message) {
        if (isalpha(*message)) {
            char base = islower(*message) ? 'a' : 'A';
            *message = ((int)(*message - base + key) % 26) + base;
        }
        message++;
    }
}

// Function to decrypt the message using Caesar cipher
void decrypt(char *message, int key) {
    encrypt(message, 26 - key);
}

int main() {
    char message[1000];
    int key;

    printf("Enter the message to encrypt: ");
    fgets(message, sizeof(message), stdin);

    printf("Enter the key (a number between 1 and 25): ");
    scanf("%d", &key);

    // Validate the key
    if (key < 1 || key > 25) {
        printf("Invalid key. Key must be between 1 and 25.\n");
        return 1;
    }

    printf("Original message: %s", message);

    // Encrypt the message
    encrypt(message, key);
    printf("Encrypted message: %s", message);

    // Decrypt the message
    decrypt(message, key);
    printf("Decrypted message: %s", message);

    return 0;
}
