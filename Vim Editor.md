### Introduction
-  Painful at first 
-  Normal mode and 
-  Insert mode
- `vim filename.py` to create file on terminal itself.
- to exit an unmodified file, press `:q`  
- to discard the modifications use `:q!` 
- to save the changes press `:wq`
- toggle between different modes by using
	- `i` / `s` for insert / replace with edit mode toggle on 
		- HJKL
			- `H` right
			- `J` down
			- `K` up
			- `L` left
		- Character to delete you can press `x`
			- `dd` to delete the entire line
			- `u` for undo
	- `:` for command
	- `v` for visual mode
- add line numbers with `:set number`
	- `:2` goto line 2
	- if you want to change syntax by hitting `i`
	- once modified you can hit `esc` to go back to normal mode
- To copy and paste code
	- `+p `
	- `:w` to save
	- `:! `to run command
		- `:! filename.py`
	
	
### More Shortcuts
- `y` is for yank, for copying the test
- `p` is paste.
- `gg` to go to top
- `shift + v` to select to select a line.

### Vim in VSCode
- Let me something with the vim code here itself actually.
- It gives me super power to type in the Obsidian itslef.
[# Vim  Tutorial](https://youtu.be/IiwGbcd8S7I) 

### More detailed tutorial form Antone Heyward
-  [Here is the video](https://youtu.be/yX_Qdr9-7kg) 
- `H`  as in Head of the screen and `gg`  for top of the file itself
- `L` as in `Leg`  for top of the file
- `M` for the middle 
 - `W or w` begining of word and this cycles
 -  `E or e` for end of the word and this cycles.
 -  `b or B` backwards to begining of the word and this cycles backward.
 -  Navigate to the end of this line.
	 -  `$` goes to the end of this line.
	 -  `0` cursor goes to begiinig of the line.
	 -  `gg` go to the first line of the document
	 -  `G` go to the begining last line of the document
	 - `{` Jump to previous paragraph
	 -  `}` Jump to next paragraph
	 
	 - `A` edit at the end of line
	 - `I` begining of the line  
	 - `o` add a new line
	 
 -  `O` add a new line on top
 -  `ea` end append
 -  `r` for replace
 -  `v` for select 
 -  Change to upper case `gU`
 -  Change them to lower case `gu`
 -  `CC` change (replace) entire line
 - `s` for delete and type, while `r` doesn't put you in an edit more, `s` does, yes.
 - Copy paste works locally on vim, not on entire laptop
 - ` v + 0` seletcts an entire row, if you are in the end of the line ofcourse.
 - `xp` swap letters.
 - `2yy` to copy  2 line, and `4yy` to copy 4 lines.
 - indenting line
	 - `>>` indent
	 - `<<` deindent
	- searching capability
		- `/` triggers search
		- `n` to navigate
		- `N` to reverse navigate
		- Search and replace
			- `%s/circle/line/g`
			- `%s/circle/line/gc` will not replace blindly, asks for confirmation 