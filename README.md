# termbox2.c3l

C3 Bindings for the <a href='https://github.com/termbox/termbox2' target='_blank'>termbox2</a> C library.

The binding function names should match up the same all that would be needed to change is prefixing it with the library module, ie. tb::tb_init();

I have packaged and set up the bindings to make use of the termbox static library which you can see how its done inside the manifest.json file.

### Setup

* Init a c3c project
```
c3c init myproject
```
* Change directory to project lib folder
```
cd myproject && cd lib
```
* Clone this library repo:
```
git clone git@github.com:jasonhilder/termbox2.c3l.git
```
* Update the project.json file to include this lib:
```
"dependencies": [ "termbox2" ],
```

### Configurable Lib Options

Please note, termbox2 has the following compile time options: 

**TB_OPT_ATTR_W**:\
Integer width of fg and bg attributes. Valid values
(assuming system support) are 16, 32, and 64. 32 or 64 enables output mode
TB_OUTPUT_TRUECOLOR. 64 enables additional style
attributes. (See tb_set_output_mode.) Larger values
consume more memory in exchange for more features.

**TB_OPT_EGC**:\
If set, enable extended grapheme cluster support
(tb_extend_cell, tb_set_cell_ex). Consumes more memory.
Defaults off.

**TB_OPT_PRINTF_BUF**:\
Write buffer size for printf operations. Represents the
largest string that can be sent in one call to tb_print*
and tb_send* functions. Defaults to 4096.

**TB_OPT_READ_BUF**:\
Read buffer size for tty reads. Defaults to 64.

**TB_OPT_TRUECOLOR**:\
Deprecated so I did not include it.

These can be changed where they are defined to fit your needs at the top of the <a href='https://github.com/jasonhilder/termbox2.c3l/blob/main/termbox2.c3i' target='_blank'>termbox.c3i file</a>.

### Example usage with project setup
```
module myproject;

import termbox2::tb;

fn void main()
{
    Tb_event ev;
    int y = 0;

    tb::tb_init();

    tb::tb_printf(0, y++, tb::TB_RED, 0, "ATTR_W: %d", tb::TB_OPT_ATTR_W);
    tb::tb_printf(0, y++, tb::TB_GREEN, 0, "hello from termbox");
    tb::tb_printf(0, y++, 0, 0, "width=%d height=%d", tb::tb_width(), tb::tb_height());
    tb::tb_printf(0, y++, 0, 0, "press any key...");

    tb::tb_present();

    tb::tb_poll_event(&ev);

    y++;
    tb::tb_printf(0, y++, 0, 0, "event type=%d key=%d ch=%c", ev.type, ev.key, ev.ch);
    tb::tb_printf(0, y++, 0, 0, "press any key to quit...");
    tb::tb_present();

    tb::tb_poll_event(&ev);
    tb::tb_shutdown();
}

```

### Still TODO
* Add all the other .a compiled libraries for macOs and Windows.
