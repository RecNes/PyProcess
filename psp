#!/bin/bash
#title        :psp
#description  :This script suitable for python programmers.
#author       :Sencer HAMARAT
#date         :20131031
#version      :1.0
#usage        :sh psp
#dependency   :Install ps util to use this script.
#bash_version :4.1.5(1)-release
#==============================================================================

if [[ -n "$1" ]]
then
	if [[ "$1" = "-h" ]] || [[ "$1" = "--help" ]]
	then
		echo "Description:	Displays running Python processes."
		echo ""
		echo "Usage:		psp [-g arg | -m |-w [n]]"
		echo "		-g | --grep arg		Displays specific process"
		echo "		-m | --mem		Displays memory usages in KBytes."
		echo "		-w | --watch n		Indicates memory usage repetitively in n seconds. (default is 5.)"
		echo "		-h | --help		Displays (this) help."
		echo ""
		seq -s= 100|tr -d '[:digit:]'
	fi

	if [[ "$1" = "-m" ]] || [[ "$1" = "--mem" ]]
	then
		ps -e -orss=,args= | grep python | sort -b -k1,1n

	elif [[ "$1" = "-w" ]] || [[ "$1" = "--watch" ]]
	then
		T=5

		if [[ "$2" > 0 ]]
		then
			T=$2
		fi

		watch -n $T 'ps -e -orss=,args= | grep python | sort -b -k1,1n'

	elif [[ "$1" = "-g" ]] || [[ "$1" == "--grep" ]]
	then
		if [[ -n "$2" ]]
		then
			ps ax | grep python | grep $2
		fi
	fi

elif [[ -z "$1" ]]
then
	ps ax | grep python
fi
echo ""
