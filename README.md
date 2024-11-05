# termbox2.c3l

C3 Bindings for the [termbox2](https://github.com/termbox/termbox2){:target="_blank"} C library. 

The binding function names should match up the same all that would be needed to change is prefixing it with the library module, ie. tb::tb_init();

I have packaged and set up the bindings to make use of the termbox static library which you can see how its done inside the manifest.json file.

### Setup

* Init a c3c project
* Change directory to project lib folder
* Clone this library repo:
```
git clone git@github.com:jasonhilder/termbox2.c3l.git
```
* Update the project.json file to include this lib:
```
"dependencies": [ "termbox2" ],
```
Please note, termbox2 has the following compile time options: 

TB_OPT_ATTR_W: Integer width of fg and bg attributes. Valid values
                (assuming system support) are 16, 32, and 64. (See
                uintattr_t). 32 or 64 enables output mode
                TB_OUTPUT_TRUECOLOR. 64 enables additional style
                attributes. (See tb_set_output_mode.) Larger values
                consume more memory in exchange for more features.
                Defaults to 16.

TB_OPT_EGC: If set, enable extended grapheme cluster support
            (tb_extend_cell, tb_set_cell_ex). Consumes more memory.
            Defaults off.

TB_OPT_PRINTF_BUF: Write buffer size for printf operations. Represents the
                   largest string that can be sent in one call to tb_print*
                   and tb_send* functions. Defaults to 4096.

TB_OPT_READ_BUF: Read buffer size for tty reads. Defaults to 64.

TB_OPT_TRUECOLOR: Deprecated so I did not include it.

These can be changed where they are defined to fit your needs at the top of the termbox.c3i file.

### Still TODO
* Add all the other .a compiled libraries for macOs and Windows.
