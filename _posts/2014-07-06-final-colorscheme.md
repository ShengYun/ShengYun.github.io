---
layout: post
title: Final colorscheme I use
---

Last night I wrote a post about deciding which colorscheme to use in Vim, today I decided to switch back to my own [dbs](https://github.com/ShengYun/vim-dbs-easycolour) colorscheme. I downloaded the latest [EasyColour](http://www.cgtk.co.uk/vim-scripts/easycolour) plugin and also installed [TagHighlight](http://www.cgtk.co.uk/vim-scripts/taghighlight).

With the help of `EasyColour`, tweaking colorschemes in Vim became extremely easy. Here's my `dbs.txt`.

{% highlight text %}

# Saving this file will update the current colour scheme.
Basis:None
Colours:
	DBSFG:#C0C0C0
	DBSComment:#00FFFF
	DBSConstant:#FF00FF
	DBSYellow:#FFFF00
	DBSOrange:#FF8000
	DBSMaroon:Maroon
	DBSLightBlue:#8080FF
	DBSGreen:#00FF00
	DBSVisual:#404040
Dark:
	Normal:DBSFG,Black
	Visual:DBSVisual,Grey
	Comment:DBSComment
	DoxygenComment:#008800
	DoxygenKeyword:#88ffdd
	DoxygenLink:#8888ff
	DoxygenTable:#00bb00
	DoxygenTableLines:#88ffdd
	LintComment:#00ff88
	Constant:DBSConstant
	String:DBSConstant
	Character:DBSConstant
	PreProc:DBSYellow
	Include:DBSYellow
	Define:DBSYellow
	Macro:DBSYellow
	PreCondit:DBSYellow
	Statement:DBSYellow
	Conditional:DBSYellow
	Repeat:DBSYellow
	Label:DBSYellow
	Exception:DBSYellow
	Operator:DBSFG
	Identifier:DBSOrange
	Function:Maroon
	Method:Maroon
	Class:Green
	DefinedName:DBSLightBlue
	EnumerationValue:DBSGreen
	EnumerationName:DBSGreen
	Member:DBSOrange
	Union:DBSGreen
	GlobalVariable:DBSOrange
	LocalVariable:#AAA14C
	GlobalConstant:DBSConstant
	Type:DBSGreen
	StorageClass:DBSYellow
	Structure:DBSYellow
	Special:Red
	SpecialChar:#AA0000
	SpecialKey:#555555
	NonText:#555555
	MatchParen:Red
	Error:White,Red
	NonIndentTabError:SP=#FFAA00,Style=Undercurl
	Todo:Blue,DBSYellow
	FoldColumn:DarkBlue,Grey
	Pmenu:Red,Black
	PmenuSel:Green,Black
	LineNr:DBSYellow
	StatusLine:Black,LightGrey
	StatusLineNC:Black,DarkGrey
	VertSplit:Black,White
	SpellBad:Style=Undercurl,SP=Red
	SignColumn:BG=#222222
	Title:DBSYellow
	htmlH1:#3333FF
	htmlH2:#8888FF
	htmlH3:#9999DD
	htmlH4:#5555AA
	htmlH5:#8888AA
	htmlH6:#888888
	Delimiter:DarkCyan
	hlLevel0:@Delimiter
	hlLevel1:#bfbf00
	hlLevel2:#990033
	hlLevel3:#334488
	hlLevel4:#996622
	hlLevel5:#ff2222
	hlLevel6:#4444ff
	hlLevel7:#ffff44
	hlLevel8:#96cdcd
	hlLevel9:#698b22
	DiffAdd:Black,Green
	DiffChange:Black,DBSOrange
	DiffDelete:Black,Red
	DiffText:Black,DBSYellow
	Folded:DBSFG,#555555
	ModeMsg:DBSComment

# vim: ff=unix:noet:ft=EasyColour

{% endhighlight %} 

