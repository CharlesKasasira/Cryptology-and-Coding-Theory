# CSC3114 Cryptology and Coding Theory

```
    Cryptology = cryptography + cryptanalysis
```

![cryptography+cryptanalysis](./images/cryptology-vs-cryptograpy.png)

Cryptography broken down into:
- `Transposition`
- `Subsitition`

### Codes ≠ Ciphers ≠ Nomenclators
`Codes`: Codes are systems in which individual words, phrases, or even whole sentences are replaced with specific code words or symbols.

`Ciphers`: Ciphers are cryptographic techniques that involve the transformation of individual characters or blocks of characters in a systematic way.

`Nomenclators`: Nomenclators are a specific type of code used for secret communication.

### Code Types

- monoalphabetic
- Polyalphabetic

### Common Ciphers

- Caesar’s Cipher
- Vigenere Square
- Enigma Cipher
- AES (Variant of Rijndae)



### Letter frequency
![letter-frequency](./images/letter-frequency.png)


#### Assignment
create a Python program that encrypts and decrypts given text using the Caesar cipher. A user should be prompted for input i.e. the text to encrypt/decrypt and the key (number of shifts to make).

```python

def caesar_cipher(text, key, mode):
    """
    Encrypts or decrypts a given text using the Caesar cipher.

    :param text (str): The text to be encrypted or decrypted.
    :param key (int): The key (number of shifts) to be used for encryption or decryption.
    :param mode (str): The mode of operation, either 'encrypt' or 'decrypt'.

    :return (str): The encrypted or decrypted text.
    """
    result = ""
    for char in text:
        if char.isalpha():
            shift = key % 26
            if char.islower():
                if mode == 'encrypt':
                    shifted_char = chr(((ord(char) - ord('a') + shift) % 26) + ord('a'))
                elif mode == 'decrypt':
                    shifted_char = chr(((ord(char) - ord('a') - shift) % 26) + ord('a'))
            elif char.isupper():
                if mode == 'encrypt':
                    shifted_char = chr(((ord(char) - ord('A') + shift) % 26) + ord('A'))
                elif mode == 'decrypt':
                    shifted_char = chr(((ord(char) - ord('A') - shift) % 26) + ord('A'))
        else:
            shifted_char = char
        
        result += shifted_char

    return result

def main():
    while True:
        print("Caesar Cipher")
        print("1. Encrypt")
        print("2. Decrypt")
        print("3. Quit")
        choice = input("Enter your choice (1/2/3): ")

        if choice == '1':
            text = input("Enter the text to encrypt: ")
            key = int(input("Enter the key (number of shifts): "))
            encrypted_text = caesar_cipher(text, key, 'encrypt')
            print("Encrypted text:", encrypted_text)
        elif choice == '2':
            text = input("Enter the text to decrypt: ")
            key = int(input("Enter the key (number of shifts): "))
            decrypted_text = caesar_cipher(text, key, 'decrypt')
            print("Decrypted text:", decrypted_text)
        elif choice == '3':
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Please enter 1, 2, or 3.")

if __name__ == "__main__":
    main()

```



### References

<div style="display: flex; justify-content: space-between;">

[![PBS Cryptography](http://img.youtube.com/vi/jhXCTbFnK8o/0.jpg)](https://www.youtube.com/watch?v=jhXCTbFnK8o "PBS Cryptography")

[![History of Cryptography](http://img.youtube.com/vi/9pp9YpginNg/0.jpg)](https://www.youtube.com/watch?v=9pp9YpginNg "History of Cryptography")

</div>
