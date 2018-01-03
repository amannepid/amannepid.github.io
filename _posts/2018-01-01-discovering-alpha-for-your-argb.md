---
layout: post
title: Discovering Alpha for Your ARGB
tags: [Android, UI/UX, Material Design]
crosspost_to_medium: true
---
Hey Rockstar, do you know `what is the hex color value of 75% Black color?` Is it `#BF000000`?

First let me remind you something else than how hex value of 75% black became #BF000000.

Android uses Hex ARGB values, which are formatted as #AARRGGBB. So what is the first pair `AA?` I assume that you know what #RRGGBB means. Yeah, its simple, RED, GREEN & BLUE hex color value.

>An 8-digit hex color value is a representation of ARGB (Alpha, Red, Green, Blue), whereas a 6-digit value just assumes 100% opacity (fully opaque) and defines just the RGB values. So to make this be fully opaque, you can either use #FF555555, or just #555555. Each 2-digit hex value is one byte, representing values from 0-255.

### So how to find the Alpha values in Hex ?


1. Take your opacity as a decimal value and multiply it by 255. So, if you have `a block that is 50% opaque, the decimal value would be 0.5. For example .5 * 255 = 127.5`

2. The fraction won’t convert to hex, so you must round your number up or down to the nearest whole number. For example `127.5 rounds up to 128; 55.25 rounds down to 55.`

3. Enter your decimal value in a `decimal to hexadecimal converter`, like this: [http://www.binaryhexconverter.com/decimal-to-hex-converter](http://www.binaryhexconverter.com/decimal-to-hex-converter){:target="_blank"} and convert your values.

4. `If you only get back a single value, prefix it with a zero.` For example, if you’re trying to get 5% opacity and you are going through this process you’ll end up with the hex value of D. Add a zero in front of it so it appears 0D.

That’s how you find the alpha channel value. But still are you lazy enough to just copy and paste the values? Thank me for the below list of values :wink:

>100% — FF  
>95% — F2  
>90% — E6  
>85% — D9  
>80% — CC  
>75% — BF  
>70% — B3  
>65% — A6  
>60% — 99  
>55% — 8C  
>50% — 80  
>45% — 73  
>40% — 66  
>35% — 59  
>30% — 4D  
>25% — 40  
>20% — 33  
>15% — 26  
>10% — 1A  
>5% — 0D  
>0% — 00  

Oh! I almost forgot, if you are an energetic android developer then below piece of code will give you the Alpha channel values in hex. Try this:

```java
public class AndroidColorsAlphaChannel {

  public static void main(String[] args) {
    for (double i = 1; i >= 0; i -= 0.01) {
      i = Math.round(i * 100) / 100.0d;
      int alpha = (int) Math.round(i * 255);
      String hex = Integer.toHexString(alpha).toUpperCase();

      if (hex.length() == 1) {
        hex = "0" + hex;
      }

      int percent = (int) (i * 100);
      System.out.println(String.format("%d%s", percent, hex));
    }
  }
}
```

Did I forgot to mention enjoy ? :wink:

>There are only 3 colors, 10 digits, and 7 notes; its what we do with them that's important.
