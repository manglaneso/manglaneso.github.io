---
layout: post
title:  "Hide messages on PNG files!"
categories: steg steganography python LSB github
tags: steg steganography python LSB github
---


# Hide messages on PNG files!

So, recently one friend sent me a [hackthebox](https://www.hackthebox.eu/) style challenge he designed.
The challenged consisted on some [steganography](https://en.wikipedia.org/wiki/Steganography) challenges in which I had
to manage to get some information from an image file.

In one of those challenges I had access some data hidden using a technique called LSB (Least Significant Bit) Based 
Steganography. This technique consists on modifying the least significant bit of every byte of every pixel on an image,
which is the bit which adds the least information to the byte, and encode each bit of your message there. This way, the
change on the image is imperceptible to the human eye, being the modified image almost completely equal to the original
file.

Interesting, right? If you want to learn more about it, just continue reading.

To understand this concept lets see a simplified example. 

> tl;dr: If you just need some code to hide text in PNG images and to read it from them, just check this 
>[repo on Github](https://github.com/manglaneso/LSB-encode-decode).

## Some boring theory
Let's take a small PNG image file:
![png_file](/assets/images/hide-messages-on-png-files/png_file.png)

This image consists of a grid of 5x5 pixels. Each pixel consists of 3 bytes, each representing the value of the 
Red, Green and Blue channel:

![png_bytes_grid](/assets/images/hide-messages-on-png-files/png_bytes_grid.png) 
 
Each pixel represents the color RGB(255, 149, 11), or #ff950b in hexadecimal, which looks like the following image:

![original_pixel_color](/assets/images/hide-messages-on-png-files/original_pixel_color.png) 

So, imagine we want to hide a message in this file. To keep it simple, let's try to hide the letter **'a'**, 
represented by the binary number **01100001** in ASCII encoding. How can we do it without anyone noticing? With the
LSB technique we'll modify the least significant bit of the first 8 bytes of the red channel of the image:

![bits_to_modify_on_image](/assets/images/hide-messages-on-png-files/png_selected_bits_to_modify.png) 

After we modify them, we get:

![bits_modified_on_image](/assets/images/hide-messages-on-png-files/png_bits_modified.png) 

We ended up with our message hidden inside an image! But wait, we altered the original image doing it! Remember how
every pixel in our original image represented the color RGB(255, 149, 11)? Well, we changed some of the first 8 bytes of
the red channel from 11111111 (255) to 11111110 (254), so now some pixels will represent the color RGB(254, 149, 11) 
instead of the original RGB(255, 149, 11)! Let's see how does this new color look like:

![modified_pixel_color](/assets/images/hide-messages-on-png-files/modified_pixel_color.png) 

Can you spot any difference?

![color_comparison](/assets/images/hide-messages-on-png-files/color_comparison.png) 

## Real world example

So, now we know how all this works, let's see a real world example with a real size image. I've put together two simple
Python scripts, one to hide ASCII messages in PNG files following the previously explained method, and another one to 
unhide them:

{% gist c07bac89768a3fa7fbcd5e1d36bbbc58 %}

Using the encoding script we will try and hide the **Star Wars Episode IV: A New Hope** film crawl inside the following
220x174 pixels Rebel Alliance flag:

![original_rebel_alliance_flag](/assets/images/hide-messages-on-png-files/Rebel_Alliance_flag.png)

After running the **encode_file.py**, we can see the following output through the terminal, where we find the message
to hide in plain text, and represented as a list of ASCII encoded bytes:

![encode_file_py_output](/assets/images/hide-messages-on-png-files/encode_file_py_output.png)

Finally we end up with the following image:

![modified_rebel_alliance_flag](/assets/images/hide-messages-on-png-files/encoded_image.png)

Can you see any difference with the original? (You can download it yourself and try to decode it!)

Okay, so now, let's see if the message is really there (and if our **decode_file.py** works properly). If we run
it, we can see the following message through the terminal:

![decode_file_py_output](/assets/images/hide-messages-on-png-files/decode_file_py_output.png)

We can see the same list of ASCII encoded bytes and the **Star Wars Episode IV: A New Hope** film crawl! Yay it works!

## Conclusions

If you got this far, thanks for reading! I hope you learn something today.

Also, if you want easy access to the code, with the example image and the LICENSE and all that stuff, check the 
[repo on Github!](https://github.com/manglaneso/LSB-encode-decode). 
