# Vault Door 5

In the last challenge, you mastered octal (base 8), decimal (base 10), and hexadecimal (base 16) numbers, but this vault door uses a different change of base as well as URL encoding! The source code for this vault is here: 

```java
import java.net.URLDecoder;
import java.util.*;

class VaultDoor5 {
    public static void main(String args[]) {
        VaultDoor5 vaultDoor = new VaultDoor5();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    public String base64Encode(byte[] input) {
        return Base64.getEncoder().encodeToString(input);
    }

    public String urlEncode(byte[] input) {
        StringBuffer buf = new StringBuffer();
        for (int i=0; i<input.length; i++) {
            buf.append(String.format("%%%2x", input[i]));
        }
        return buf.toString();
    }

    public boolean checkPassword(String password) {
        String urlEncoded = urlEncode(password.getBytes());
        String base64Encoded = base64Encode(urlEncoded.getBytes());
        String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                        + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                        + "JTM0JTVmJTY1JTMzJTMxJTM1JTMyJTYyJTY2JTM0";
        return base64Encoded.equals(expected);
    }
}
```
**FLAG: picoCTF{c0nv3rt1ng_fr0m_ba5e_64_e3152bf4}**

## My Approach to solve this challenge:-


In this challenge code, the user input is taken and first it is url encoded and then Base 64 encoded. Then this is checked with the hardcoded string sequence.

I used online decryption site( [cyber chef](https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',false,false)URL_Decode()&input=SlRZekpUTXdKVFpsSlRjMkpUTXpKVGN5SlRjMEpUTXhKVFpsSlRZM0pUVm1KVFkySlRjeUpUTXdKVFprSlRWbUpUWXlKVFl4SlRNMUpUWTFKVFZtSlRNMkpUTTBKVFZtSlRZMUpUTXpKVE14SlRNMUpUTXlKVFl5SlRZMkpUTTA)) to first decrypt the base64 and then url Encryption.

This gives us the flag.

![image](https://github.com/user-attachments/assets/b34be3c0-8224-44bf-9e91-8d6d47b99297)

## Learning outcomes:-

1. What is URL Encryption?

   > 1. `Allowed Characters`: URLs can only safely contain alphanumeric characters (A-Z, a-z, 0-9) and a limited set of special characters (-, _, ., and ~).
   > 2. `Reserved Characters`: Certain characters have special meanings in URLs (e.g., /, ?, #, &, =). If these characters are part of the actual data, they must be encoded to avoid misinterpretation.
   > 3. `Encoding Unsafe Characters`: Characters like spaces, <, >, {, }, and others are "unsafe" and need to be encoded.

      **Steps of URL Encoding**

   > 1. `Identify Unsafe Characters`: Find any character that is not a letter, number, or one of the safe special characters.
    > 2. `Convert to Hexadecimal`: Convert the ASCII value of each unsafe character to a two-digit hexadecimal number.
   >  3. `Prefix with %`: Replace each unsafe character with % followed by its hexadecimal code.
