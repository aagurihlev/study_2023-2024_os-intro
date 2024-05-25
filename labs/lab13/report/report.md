---
## Front matter
title: "Лабораторная работа №13"
subtitle: "Программирование в командном процессоре OC UNIX. Ветвления и циклы"
author: "Гурылев Артем Андреевич"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Целью работы является изучение основ программирования в оболочке ОС UNIX. Нужно научится писать более сложные командные файлы с использованием логических управляющих конструкций и циклов.

# Выполнение лабораторной работы

Для начала напишем первую программу, в которой нужно использовать ключи. Листинг программы:

```
while getopts iinputfile:ooutputfile:p:Cn optletter
do case $optletter in
iinputfile)	inputflag=1;	inputfile=$OPTARG;;
ooutputfile)	outputflag=1;	outputfile=$OPTARG;;
p)	pflag=1;	pvalue=$OPTARG;;
C)	Cflag=1;;
n)	nflag=1;;
*)	echo Illegal option $optletter
esac
done
if [[ Cflag = 1 ]]; then
	opt_grep+=" -i"
fi
if [[ nflag = 1 ]]; then
	opt_grep+=" -n"
fi
if [[ inputflag = 1 ]] and [[ pflag=1 ]]; then
	if [[ outputflag = 1 ]]; then
		grep $opt_grep "$pvalue" "$inputfile" >> "$outputfile"
	else grep $opt_grep "$pvalue" "$inputfile"
```

# Выводы

В этой работе я научился использовать циклы и ветвления для более эффективного программирования в OC UNIX.


