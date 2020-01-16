# Hotkeys

Learning experiment. The replacement for my hotkeys implemented with use of Autohotkeys written on Rust. 

[Gist with the ahk configuration](https://gist.github.com/anzome/5518671)

## Hotkeys from Autohotkeys

```text
; <! - left alt-key
; ^ - ctrl-key
; + - shift-key
; sc021 - W 
; sc010 - D
; sc011 - F
; sc014 - T
; sc013 - R
; sc024 - J
; sc025 - K
; sc026 - L
; sc017 - I
; sc01A - [
; sc01B - ]
; sc027 - ;
; sc02B - \
; sc035 - /
; sc033 - ,
; sc034 - .
 
;++++++++++++++++++++ 
; LEFT: J letter
;++++++++++++++++++++
<!sc024::Send,{Left}
return
^<!sc024::Send,^{Left}
return
+<!sc024::Send,+{Left}
return
+^<!sc024::Send,+^{Left}
return

;++++++++++++++++++++ 
;DOWN: K letter
;++++++++++++++++++++
<!sc025::Send,{Down}
return
^<!sc025::Send,^{Down}
return
+<!sc025::Send,+{Down}
return
+^<!sc025::Send,+^{Down}
return

;++++++++++++++++++++ 
;UP: I letter
;++++++++++++++++++++
<!sc017::Send,{Up}
return
^<!sc017::Send,^{Up}
return
+<!sc017::Send,+{Up}
return
+^<!sc017::Send,+^{Up}
return

;++++++++++++++++++++ 
;RIGHT: L letter
;++++++++++++++++++++
<!sc026::Send,{Right}
return
^<!sc026::Send,^{Right}
return
+<!sc026::Send,+{Right}
return
+^<!sc026::Send,+^{Right}
return

;+++++ 
;DELETE 
;+++++
<!Delete::Send,{Delete}
return

;+++++ 
;BACKSPACE 
;+++++
<!Backspace::Send,{Backspace}
return

;+++++ 
;CODING STUFF IN RUSSIAN KEYBOARD LAYOUT
;+++++
; [ in eng-russian keyboard
<!sc01A::
Send,{[}
return
; ] in eng-russian keyboard
<!sc01B::
Send,{]}
return
; { in eng-russian keyboar
+<!sc01A::
Send,{{}
return
; } in eng-russian keyboard
+<!sc01B::
Send,{}}
return
<!sc027::
Send,{;}
return
+<!sc027::
Send,{:}
return
<!sc02B::
Send,{\}
return
+<!sc02B::
Send,{|}
return
<!sc028::
Send,{'}
return
+<!sc028::
Send,{"}
return
<!,::
Send,{,}
return
<!.::
Send,{.}
return
<!sc035::
Send,{/}
return
+<!sc035::
Send,{?}
return
<!sc033::
Send,{,}
return
<!sc034::
Send,{.}
return
+<!sc033::
Send,{<}
return
+<!sc034::
Send,{>}
return
 
;+++++
; @
;+++++
<!2::
Send,{@}
return


;+++++
; HOW TO GET KEYBOARD LAYOUT CODE
;+++++
;F11::
;  SetFormat, Integer, H
;  WinGet, WinID,, A
;  ThreadID:=DllCall("GetWindowThreadProcessId", "UInt", WinID, "UInt", 0)
;  InputLocaleID:=DllCall("GetKeyboardLayout", "UInt", ThreadID, "UInt")
;  MsgBox, %InputLocaleID%
;Return


;+++++ Grave Acute +++++
;<!ё::
;Send,{`}
;return

;+++++
; TIMESTAMP
;+++++

<!+sc010::
SendInput,%A_YYYY%-%A_MM%-%A_DD% %A_Hour%:%A_Min%
return

last_try := 0
get_time()
{
	global last_try
	now := A_TickCount
	diff := Floor((now-last_try)/(1000*60)) ; minutes
	last_try := now
	SendInput,%diff% min 
}
return

<!+sc014::
get_time()
return

<!+sc013::
last_try := A_TickCount
return

;+++++ 
; KEEPASS
;+++++
#IfWinActive base.kdbx - KeePass 
{
	^sc011::
  	Send,^e
  	return

  	^sc021::
  	Send,^e
  	return
}
```
