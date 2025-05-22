# Caesar-Cipher-encoder-decoder
🔐 How the Caesar Cipher Web App Works (Step by Step)
This app is a Caesar Cipher encoder/decoder, built using HTML, CSS, and JavaScript. Here's a breakdown of how it works:

🧠 What is the Caesar Cipher?
A substitution cipher where each letter in the plaintext is shifted a certain number of places down or up the alphabet.

For example, with a shift of 3:

A → D, B → E, ..., Z → C

🧱 Structure Overview
Component	Purpose
HTML	Creates the form and page layout
CSS	Makes it look modern and stylish
JavaScript	Handles encryption and decryption logic

💻 How It Works – Step by Step
1. User Inputs
A message to encrypt or decrypt

A shift value (e.g. 3)

Presses the Encrypt or Decrypt button

2. JavaScript Logic (in caesarCipher() function)
javascript
Copy
Edit
function caesarCipher(text, shift) {
  return text.split('').map(char => {
    const code = char.charCodeAt(0);

    // For lowercase letters
    if (char >= 'a' && char <= 'z') {
      return String.fromCharCode(((code - 97 + shift + 26) % 26) + 97);
    }

    // For uppercase letters
    else if (char >= 'A' && char <= 'Z') {
      return String.fromCharCode(((code - 65 + shift + 26) % 26) + 65);
    }

    // Non-alphabet characters are unchanged
    return char;
  }).join('');
}
What it does:
Converts each letter to its ASCII code

Adjusts the code by adding the shift

Uses modulo 26 to wrap around the alphabet (e.g., Z + 1 → A)

Leaves non-letters (like spaces, punctuation) unchanged

🔄 Encrypt vs Decrypt
Encrypt:
javascript
Copy
Edit
encrypt() {
  caesarCipher(message, shift)
}
Applies the positive shift

Decrypt:
javascript
Copy
Edit
decrypt() {
  caesarCipher(message, -shift)
}
Applies the negative shift to reverse the encryption

🖥️ Example
Input:

Message: HELLO

Shift: 3

Encryption:

H → K, E → H, L → O, L → O, O → R

Result: KHOOR

Decryption (using shift 3 again):

KHOOR → HELLO
