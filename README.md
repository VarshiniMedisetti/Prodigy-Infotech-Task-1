# Prodigy-Infotech-Task-1
A python program that allows users to encrypt and decrypt text using the Caesar Cipher algorithm. The program takes a message and a shift value as input and then performs either encryption or decryption based on user choice.
def caesar_cipher(text, shift, mode='encrypt'):
    result = ""

    # Adjust the shift for decryption
    if mode == 'decrypt':
        shift = -shift

    # Traverse the text
    for i in range(len(text)):
        char = text[i]

        # Encrypt uppercase characters
        if char.isupper():
            result += chr((ord(char) + shift - 65) % 26 + 65)

        # Encrypt lowercase characters
        elif char.islower():
            result += chr((ord(char) + shift - 97) % 26 + 97)

        # For non-alphabetic characters, add them without change
        else:
            result += char

    return result

# Get user input
message = input("Enter your message: ")
shift = int(input("Enter the shift value: "))
choice = input("Type 'encrypt' to encrypt or 'decrypt' to decrypt: ").lower()

# Encrypt or decrypt the message
if choice in ['encrypt', 'decrypt']:
    processed_message = caesar_cipher(message, shift, mode=choice)
    print(f"The {choice}ed message is: {processed_message}")
else:
    print("Invalid choice. Please choose 'encrypt' or 'decrypt'.")
