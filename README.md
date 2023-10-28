# Configuration

## Dependencies

* rofi
* rofi-calc
* rofi-emoji
* rofi-file-browser-extended

## Posible erros

### Missing plugins

Make sure that the plugins are in `usr/lib64/rofi/`.

Try:

```sh
$ ls /usr/lib64/rofi/
calc.so  emoji.so  filebrowser.so
```

If this is the case, it means that it will work correctly.

### Problems with Emojis

If you have [this](https://github.com/Mange/rofi-emoji/issues/52) problem: 
![img](https://camo.githubusercontent.com/927f78aa6a1eaf0fab929d1d4e9a57432792b2fcce32b837402a2c4991cfc20d/68747470733a2f2f692e696d6775722e636f6d2f356c394555434e2e6a706567)

You have to follow these steps:

1. Install Noto Emoji font [here](https://github.com/googlefonts/noto-emoji)
2. Copy the font (NotoColorEmoji.ttf) to `~/.fonts`
3. Change (or create) the file `~/.config/fontconfig/fonts.conf` like this:
4. Run `fc-cache -fv`


```xml
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <alias>
  <family>sans-serif</family>
  <prefer>
   <!-- Add your Sans-serif fonts here -->
   <family>Noto Color Emoji</family>  <!-- this will be your fallback font -->
   <family>Noto Emoji</family> 
  </prefer>
 </alias>
 <alias>
  <family>serif</family>
  <prefer>
   <!-- Add your Serif fonts here -->
   <family>Noto Color Emoji</family>
   <family>Noto Emoji</family> 
  </prefer>
 </alias>
</fontconfig>
```

For example, in VoidLinux looks my config looks like this:

<details>
  <summary>
    Show my config
  </summary>
    
    
```xml
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
  <!-- Set preferred serif, sans serif, and monospace fonts. -->
  <alias>
    <family>serif</family>
    <prefer>
      <family>Tinos</family>
      <family>Noto Color Emoji</family>     <!-- Here -->
       <family>Noto Emoji</family>          <!-- Here -->
    </prefer>
  </alias>
  <alias>
    <family>sans-serif</family>
    <prefer>
      <family>Arimo</family>
      <family>Noto Color Emoji</family>     <!-- Here -->
      <family>Noto Emoji</family>           <!-- Here -->
    </prefer>
  </alias>
  <alias>
    <family>sans</family>
    <prefer><family>Arimo</family></prefer>
  </alias>
  <!-- Aliases for commonly used MS fonts. -->
  <match>
    <test name="family"><string>Arial</string></test>
    <edit name="family" mode="assign" binding="strong">
      <string>Arimo</string>
    </edit>
  </match>
  <match>
    <test name="family"><string>Helvetica</string></test>
    <edit name="family" mode="assign" binding="strong">
      <string>Arimo</string>
    </edit>
  </match>
  <match>
    <test name="family"><string>Verdana</string></test>
    <edit name="family" mode="assign" binding="strong">
      <string>Arimo</string>
    </edit>
  </match>
  <match>
    <test name="family"><string>Tahoma</string></test>
    <edit name="family" mode="assign" binding="strong">
      <string>Arimo</string>
    </edit>
  </match>
  <match>
    <!-- Insert joke here -->
    <test name="family"><string>Comic Sans MS</string></test>
    <edit name="family" mode="assign" binding="strong">
      <string>Arimo</string>
    </edit>
  </match>
  <match>
    <test name="family"><string>Times New Roman</string></test>
    <edit name="family" mode="assign" binding="strong">
      <string>Tinos</string>
    </edit>
  </match>
  <match>
    <test name="family"><string>Times</string></test>
    <edit name="family" mode="assign" binding="strong">
      <string>Tinos</string>
    </edit>
  </match>
  <match>
    <test name="family"><string>Courier New</string></test>
    <edit name="family" mode="assign" binding="strong">
      <string>Cousine</string>
    </edit>
  </match>
</fontconfig>
```
  
</details>

And **reboot**.
