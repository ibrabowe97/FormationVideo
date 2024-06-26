# Code de César

> **SOMMAIRE**
> + [C](#c)
> + [C++](#c-1)
> + [C#](#c-2)
> + [Java](#java)
> + [JavaScript](#javascript)
> + [PHP](#php)
> + [Python](#python)

---

## C

```c
static const int ALPHABET_SIZE = 26;

// Chiffrement
void caesarCipherEncrypt(char* message, int shift)
{
    shift %= ALPHABET_SIZE;

    if(shift < 0)
        shift += ALPHABET_SIZE;

    for(int i = 0 ; message[i] != '\0' ; ++i)
        if(isalpha(message[i]))
        {
            char base = (message[i] >= 'a') ? 'a' : 'A';
            message[i] = (message[i] - base + shift) % ALPHABET_SIZE + base;
        }

}

// Déchiffrement
void caesarCipherDecrypt(char* message, int shift)
{
    caesarCipherEncrypt(message, ALPHABET_SIZE - shift);
}
```

---

## C++

```cpp
constexpr int ALPHABET_SIZE = 26;

// Chiffrement
void caesarCipherEncrypt(std::string& message, int shift)
{
    shift %= ALPHABET_SIZE;

    if(shift < 0)
        shift += ALPHABET_SIZE;

    for(char& character : message)
    {
        if(std::isalpha(character))
        {
            char base = (character >= 'a') ? 'a' : 'A';
            character = (character - base + shift) % ALPHABET_SIZE + base;
        }
    }
}

// Déchiffrement
void caesarCipherDecrypt(std::string& message, int shift)
{
    return caesarCipherEncrypt(message, ALPHABET_SIZE - shift);
}
```

---

## C#

```csharp
public class CaesarCipher
{
    private const int ALPHABET_SIZE = 26;

    // Chiffrement
    public static string Encrypt(string message, int shift)
    {
        shift %= ALPHABET_SIZE;

        if(shift < 0)
            shift += ALPHABET_SIZE;

        string encryptedMessage = "";

        foreach(char character in message)
        {
            if(char.IsLetter(character))
            {
                char baseCharacter = char.IsUpper(character) ? 'A' : 'a';
                char c = (char)(((character - baseCharacter + shift) % ALPHABET_SIZE) + baseCharacter);
                encryptedMessage += c;
            }
            else
                encryptedMessage += character;
        }

        return encryptedMessage;
    }

    // Déchiffrement
    public static string Decrypt(string message, int shift)
    {
        return Encrypt(message, ALPHABET_SIZE - shift);
    }
}
```

---

## Java

```java
public class CaesarCipher
{
    private static final int ALPHABET_SIZE = 26;

    // Chiffrement
    public static String encrypt(String message, int shift)
    {
        shift %= ALPHABET_SIZE;

        if(shift < 0)
            shift += ALPHABET_SIZE;

        StringBuilder encryptedMessage = new StringBuilder();
        int messageLength = message.length();

        for(int i = 0 ; i < messageLength ; ++i)
        {
            char character = message.charAt(i);
            char lowerCharacter = Character.toLowerCase(character);

            if(lowerCharacter >= 'a' && lowerCharacter <= 'z')
            {
                char base = Character.isUpperCase(character) ? 'A' : 'a';
                char c = (char)((character - base + shift) % ALPHABET_SIZE + base);
                encryptedMessage.append(c);
            }
            else
                encryptedMessage.append(character);
        }

        return encryptedMessage.toString();
    }

    // Déchiffrement
    public static String decrypt(String message, int shift)
    {
        return encrypt(message, ALPHABET_SIZE - shift);
    }
}
```

---

## JavaScript

```js
const ALPHABET_SIZE = 26;

// Chiffrement
function caesarCipherEncrypt(message, shift)
{
    shift %= ALPHABET_SIZE;

    if(shift < 0)
        shift += ALPHABET_SIZE;

    let encryptedMessage = "";
    let messageLength = message.length;

    for(let i = 0 ; i < messageLength ; ++i)
    {
        if(/[a-zA-Z]/.test(message[i]))
        {
            const base = message[i].toUpperCase() === message[i] ? 'A'.charCodeAt(0) : 'a'.charCodeAt(0);
            const c = String.fromCharCode(((message[i].charCodeAt(0) - base + shift) % ALPHABET_SIZE) + base);
            encryptedMessage += c;
        }
        else
        encryptedMessage += message[i];
    }

    return encryptedMessage;
}

// Déchiffrement
function caesarCipherDecrypt(message, shift)
{
    return caesarCipherEncrypt(message, ALPHABET_SIZE - shift);
}
```

---

## PHP

```php
const ALPHABET_SIZE = 26;

// Chiffrement
function caesarCipherEncrypt(string $message, int $shift): string
{
    $shift %= ALPHABET_SIZE;

    if($shift < 0)
        $shift += ALPHABET_SIZE;

    $encryptedMessage = "";
    $messageLength = strlen($message);

    for($i = 0 ; $i < $messageLength ; ++$i)
    {
        if(ctype_alpha($message[$i]))
        {
            $base = ctype_upper($message[$i]) ? ord('A') : ord('a');
            $c = chr(($shift + ord($message[$i]) - $base) % ALPHABET_SIZE + $base);
            $encryptedMessage .= $c;
        }
        else
            $encryptedMessage .= $message[$i];
    }

    return $encryptedMessage;
}

// Déchiffrement
function caesarCipherDecrypt(string $message, int $shift): string
{
    return caesarCipherEncrypt($message, ALPHABET_SIZE - $shift);
}
```

---

## Python

```python
ALPHABET_SIZE = 26

# Chiffrement
def caesar_cipher_encrypt(message, shift):
    shift %= ALPHABET_SIZE

    if shift < 0:
        shift += ALPHABET_SIZE

    encrypted_message = ""

    for character in message:
        if character.isalpha() and character.isascii():
            base = ord('A') if character.isupper() else ord('a')
            c = chr((ord(character) - base + shift) % ALPHABET_SIZE + base)
            encrypted_message += c
        else:
            encrypted_message += character

    return encrypted_message

# Déchiffrement
def caesar_cipher_decrypt(message, shift):
    return caesar_cipher_encrypt(message, ALPHABET_SIZE - shift)
```
