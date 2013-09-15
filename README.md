## INTRODUCTION [![Build Status](https://travis-ci.org/rhysd/clever-f.vim.png?branch=dev)](https://travis-ci.org/rhysd/clever-f.vim)

clever-f.vim extends `f`, `F`, `t` and `T` mappings for more convenience.  Instead of `;`, `f` is available to repeat after you type `f{char}` or `F{char}`.  `F` after `f{char}` and `F{char}` is also available to undo a jump. `t{char}` and `T{char}` are ditto. This extension makes a repeat easier and makes you forget the existence of `;`. You can use `;` for other key mapping.
In addition, you can customize a behavior of the mappings.



## USAGE

I'll show some examples of usage. _ is the place of cursor, -> is a move of
cursor, alphabets above -> is input by keyboard.


    input:       fh         f         f      e         fo         f
    move :  _---------->_------>_---------->_->_---------------->_->_
    input:                            F                            F
    move :                        _<-----------------------------_<-_
    text :  hoge        huga    hoo         hugu                ponyo



    input:        f        Fh       b     f                         Fo
    move :  _<----------_<------_<-_<-----------------------------_<-_
    input:        F        F          F
    move :  _---------->_------>_----------->_
    text :  hoge        huga    huyo         hugu                ponyo



    input:       th         t         t      e         to         t
    move :  _--------->_------>_---------->_-->_--------------->_->_
    input:                            T                            T
    move :                         _<-----------------------------__
    text :  hoge        huga    hoo         hugu                ponyo



## CUSTOMIZE

### Search a character only in current line

`g:clever_f_across_no_line` controls to search a character across multi lines or not.
Please set it to `1` in your vimrc to search a character only in current line.

### Ignore case

`g:clever_f_ignore_case` controls to make a search case-insensitive or not.
Please set it to `1` in your vimrc to ignore case.

### Smart case
`g:clever_f_smart_case` controls make smart case or not.
If and only if you type an lower case character, clever-f.vim ignores case.
Please set it to `1` in your vimrc to make smart case

### Migemo support

In Japanese environment, it is convenient that `fa` matches `あ` in some cases. Originally, this feature is provided by [migemo](http://0xcc.net/migemo/).
clever-f can search multibyte Japanese character with `f`, 'F', 't' and 'T' key mappings. A cmigemo package is **NOT** required because clever-f includes regex patterns generated by migemo.
Set `clever_f_use_migemo` to `1` to get migemo support.

### Fix a direction of search

If you always want to search forward with `f` and always want to search backward with `F`, set `g:clever_f_fix_key_direction` to `1`.

    input:        F        Fh     b     F                         Fo
    move :  _<----------_<------_<-_<-----------------------------_<-_
    input:        f        f          f
    move :  _---------->_------>_----------->_
    text :  hoge        huga    huyo         hugu                ponyo

### Show prompt

If you want to show a prompt when you input a character for clever-f, set `g:clever_f_show_prompt` to `1`. The prompt is disposed after a character is input.

### Match all signs with one char

Many sign(like {, (, ", and so on) keys are hard to press. If you want to match `;` key to all signs, you can use `g:clever_f_chars_match_any_signs`. If you set it to `';'`, `f;` matches all signs.

    input:   f;   f       f      f f       f       f
    move :  _-->_--->_--------->_>_>_------------>_>_
    text :  hoge.huga( autoloads: %w{ aaa bbb ccc } )


## LICENSE

Distributed under MIT License. See `doc/clever_f.txt`
