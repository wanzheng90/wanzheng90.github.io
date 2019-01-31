---
title: vim surround插件
date: 2016-08-31 15:19:20
tags: vim 插件
category: 工具
---
surround 一个快速对内容包裹或解包的插件
<!---more-->

示例：
```
  Old text                  Command     New text ~
  "Hello *world!"           ds"         Hello world!
  [123+4*56]/2              cs])        (123+456)/2
  "Look ma, I'm *HTML!"     cs"<q>      <q>Look ma, I'm HTML!</q>
  if *x>3 {                 ysW(        if ( x>3 ) {
  my $str = *whee!;         vlllls'     my $str = 'whee!';
  <div>Yo!*</div>           dst         Yo!
  <div>Yo!*</div>           cst<p>      <p>Yo!</p>
```
其中，*表示光标所在位置。


快捷键的列表：
```
  Normal mode
	----------
	ds  - delete a surrounding
	cs  - change a surrounding
	ys  - add a surrounding
	yS  - add a surrounding and place the surrounded text on a new line + indent it
	yss - add a surrounding to the whole line
	ySs - add a surrounding to the whole line, place it on a new line + indent it
	ySS - same as ySs

	Visual mode
	-----------
	s   - in visual mode, add a surrounding
	S   - in visual mode, add a surrounding but place text on new line + indent it

	Insert mode
	-----------
	<CTRL-s> - in insert mode, add a surrounding
	<CTRL-s><CTRL-s> - in insert mode, add a new line + surrounding + indent
	<CTRL-g>s - same as <CTRL-s>
	<CTRL-g>S - same as <CTRL-s><CTRL-s>
```
