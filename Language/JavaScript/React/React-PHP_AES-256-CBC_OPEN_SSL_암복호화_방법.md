1. React 에서는 CryptoJS라는 암/복호화 Lib가 존재

    ```
    npm install crypto-js
    ```

2. CryptoJS AES 암호화 기본 문법

    ```
    CryptoJS.AES.encrypt(plainText, Key, option).toString();
    ```

3. OPEN SSL 암호화를 위해 iv, padding, mode(CBC) 옵션을 추가하고 Key와 iv를 UTF-8 형식으로 변경

    ```
    const ciphertext = CryptoJS.AES.encrypt(plainText, CryptoJS.enc.Utf8.parse(key), {

        iv: CryptoJS.enc.Utf8.parse(iv),

        padding: CryptoJS.pad.Pkcs7,

        mode: CryptoJS.mode.CBC

    }).toString();
    ```

4. toString() Function을 사용해 Base64 형식으로 변경

5. PHP 5.3 버전 이상부터 openssl en/decrypt를 사용 가능하므로 간편하게 암/복호화가 가능

    ```
    $plainText = "message";

    $key = "12345678912345678912345678912345";  // 32Byte

    $iv = "1234567891234567";  // 16Byte

    $encrypted = openssl_encrypt($plainText, "aes-256-cbc", $key, true, $iv);

    $encrypted = base64_encode($encrypted);
    

    $decrypted = base64_decode($encrypted);

    $decrypted = openssl_decrypt($encrypted, "aes-256-cbc", $key, true, $iv);
    ```