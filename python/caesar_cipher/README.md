Caesar cipher, person can encrypt a message by replacing each letter in it with a “shifted” letter.

The first function get_mode() allows player to choose the mode: encode, decode or brute force.

The second function get_message() returns the input from a player. 

The letters are included in the SYMBOLS variable, 26 uppercase and 26 lowercase letters. Thus len(SYMBOLS) equals 52 in this case but the other symbols can be added.

The third function get_key() returns a key which is an integer that the player entered. The while loop is created and the only way out is to enter the integer 1 - len(SYMBOLS), In this case it is 52. The statement:    if (key >= 1 and key <= MAX_KEY_SIZE).

The fourth function get_translated_message(mode, message, key) has three parameters: mode sets the function to encryption mode or decryption mode. message - is the plaintext (or ciphertext) to be encrypted (or decrypted), key is the key that is used in this cipher.
if mode[0] == 'd':
        key = -key
    translated = ''
This if statement makes difference between decryption and encryption mode. The key is set to the negative version of itself during decryption. The translated variable will contain the string of the result: either the ciphertext if you are encrypting or the plaintext if you are decrypting.
Next there is a for loop which will itterate through the message. It will get the index of each index of the string in symbol variable:

for symbol in message:
        symbol_index = SYMBOLS.find(symbol)
        if symbol_index == -1:     
            translated += symbol

Any characters that aren’t part of the alphabet, such as commas and periods, won’t be changed. 

            if symbol_index >= len(SYMBOLS):    
                symbol_index -= len(SYMBOLS)
            elif symbol_index < 0:
                symbol_index += len(SYMBOLS)
            
This if statement allows symbol_index to go past the last index of SYMBOLS when the sum is more than len(SYMBOLS), we’ll need to wrap around to the beginning of the list at 0.
The function returns encrypted or decrypted translated variable.

The additional mode that the player can use is brute-force mode, which uses the for loop to iterate through all the possible keys, in this case 1-52 and print every possible encryption or decryption:

for key in range(1, MAX_KEY_SIZE + 1):
        print(key, get_translated_message('decrypt', message, key))

