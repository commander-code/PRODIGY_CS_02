Image Encryption and Decryption Tool
Overview
This Python script provides a simple implementation of image encryption and decryption using pixel manipulation. The encryption process swaps the red (R) and blue (B) channels of each pixel, creating a scrambled version of the image. The decryption process reverses this swap to restore the original image.

Code Breakdown
encrypt_image(input_path, output_path, key)
This function encrypts the image by swapping the red and blue channels of each pixel.

Image Loading: The input image is loaded using Image.open(), and the pixel data is accessed through img.load().
Pixel Iteration: The function iterates over each pixel in the image:
Pixel Swapping: For each pixel, the red (R) and blue (B) channels are swapped while the green (G) channel remains unchanged.
Save Encrypted Image: The encrypted image is saved to the specified output path using img.save().
Print Success Message: A success message is printed when the encryption is completed.
decrypt_image(input_path, output_path, key)
This function decrypts the image by swapping the red and blue channels back to their original positions.

Image Loading: The encrypted image is loaded using Image.open(), and the pixel data is accessed through img.load().
Pixel Iteration: The function iterates over each pixel in the image:
Pixel Swapping: For each pixel, the red (R) and blue (B) channels are swapped back to their original positions while the green (G) channel remains unchanged.
Save Decrypted Image: The decrypted image is saved to the specified output path using img.save().
Print Success Message: A success message is printed when the decryption is completed.
Usage
Encrypt an Image:
python
Copy code
input_image = r"C:\path\to\input_image.jpg"
encrypted_image = r"C:\path\to\encrypted_image.jpg"

encrypt_image(input_image, encrypted_image, key=None)
This will save the encrypted image at the specified location.

Decrypt an Image:
python
Copy code
decrypted_image = r"C:\path\to\decrypted_image.jpg"

decrypt_image(encrypted_image, decrypted_image, key=None)
This will restore and save the decrypted image at the specified location.

Full Code Example
python
Copy code
from PIL import Image

def encrypt_image(input_path, output_path, key):
    img = Image.open(input_path)
    pixels = img.load()

    width, height = img.size

    for i in range(width):
        for j in range(height):
            r, g, b = pixels[i, j]

            # swapping red and blue channels
            encrypted_pixel = (b, g, r)

            pixels[i, j] = encrypted_pixel

    img.save(output_path)
    print("Image encrypted successfully!")

def decrypt_image(input_path, output_path, key):
    img = Image.open(input_path)
    pixels = img.load()

    width, height = img.size

    for i in range(width):
        for j in range(height):
            r, g, b = pixels[i, j]

            # swapping red and blue channels back
            decrypted_pixel = (b, g, r)

            pixels[i, j] = decrypted_pixel

    img.save(output_path)
    print("Image decrypted successfully!")

# File paths
input_image = r"C:\path\to\input_image.jpg"
encrypted_image = r"C:\path\to\encrypted_image.jpg"
decrypted_image = r"C:\path\to\decrypted_image.jpg"

# Encrypt the image
encrypt_image(input_image, encrypted_image, key=None)

# Decrypt the image
decrypt_image(encrypted_image, decrypted_image, key=None)
Notes
Key Parameter: Although the key parameter is present in the functions, it is not currently used. It can be extended to include more advanced encryption techniques.
Supported Image Formats: The script supports various image formats like .jpg, .png, and .bmp.
Security: This is a simple pixel-based encryption technique and is not suitable for secure applications. For real encryption tasks, consider using advanced encryption algorithms like AES or RSA.
