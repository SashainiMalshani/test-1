#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Function to encrypt the message 
void encrypt(char *message, int key) {
    for (int i = 0; message[i] != '\0'; i++) {
        if (message[i] >= 'A' && message[i] <= 'Z') {
            message[i] = (message[i] - 'A' + key) % 26 + 'A';
        } else if (message[i] >= 'a' && message[i] <= 'z') {
            message[i] = (message[i] - 'a' + key) % 26 + 'a';
        } else if (message[i] >= '0' && message[i] <= '9') {
            message[i] = (message[i] - '0' + key) % 10 + '0';
        }
    }
}

// Function to decrypt the message 
void decrypt(char *message, int key) {
    for (int i = 0; message[i] != '\0'; i++) {
        if (message[i] >= 'A' && message[i] <= 'Z') {
            message[i] = (message[i] - 'A' - key + 26) % 26 + 'A';
        } else if (message[i] >= 'a' && message[i] <= 'z') {
            message[i] = (message[i] - 'a' - key + 26) % 26 + 'a';
        } else if (message[i] >= '0' && message[i] <= '9') {
            message[i] = (message[i] - '0' - key + 10) % 10 + '0';
        }
    }
}

int main() {
    char message[100];
    int key;

    // Get the message from the user
    printf("Enter a message to encrypt: ");
    fgets(message, sizeof(message), stdin);

    // Get the encryption key from the user
    printf("Enter the encryption key (a number between 1 and 25): ");
    scanf("%d", &key);

    // Encrypt the message
    encrypt(message, key);
    printf("Encrypted message: %s\n", message);

    // Decrypt the message
    decrypt(message, key);
    printf("Decrypted message: %s\n", message);

    return 0;
}


