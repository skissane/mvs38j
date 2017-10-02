# mvs38j

This runs the [TK4-](http://wotho.ethz.ch/tk4-/) distribution of MVS 3.8J inside Docker.

All credit belongs to Juergen Winkelmann for creating TK4-, Volker Bande for creating TK3, the Hercules team for
creating Hercules, IBM for creating MVS, etc. - all I did was package it into a Docker container.

## Running it

```
./start
docker logs mvs38j
```

Now wait until startup message is displayed:
```
HHC01603I *
HHC01603I *                           ************   ****  *****          ||
HHC01603I *                           **   **   **    **    **           |||
HHC01603I *                           **   **   **    **   **           ||||
HHC01603I *                                **         **  **           || ||
HHC01603I *        |l      _,,,---,,_      **         ** **           ||  ||
HHC01603I * ZZZzz /,'.-'`'    -.  ;-;;,    **         ****           ||   ||
HHC01603I *      |,4-  ) )-,_. ,( (  ''-'  **         *****         ||    ||
HHC01603I *     '---''(_/--'  `-')_)       **         **  **       ||     ||    ||||||||||
HHC01603I *                                **         **   **      |||||||||||  Update 08
HHC01603I *       The MVS 3.8j             **         **    **            ||
HHC01603I *     Tur(n)key System           **         **     **           ||
HHC01603I *                              ******      ****     ***       ||||||
HHC01603I *
HHC01603I *            TK3 created by Volker Bandke       vbandke@bsp-gmbh.com
HHC01603I *            TK4- update by Juergen Winkelmann  winkelmann@id.ethz.ch
HHC01603I *                     see TK4-.CREDITS for complete credits
HHC01603I *
HHC02264I Script 5: file scripts/tk4-.rc processing ended
```

Next run:
```
./c3270
```

Press Ctrl+] and at the prompt type `attn`:
```
Press <Enter> to resume session.
c3270> attn
```
Now at the `Logon ===> ` prompt type `LOGON HERC01/CUL8TR`

At the menu, to get the TSO prompt, select option `X`.
You can run `TSOAPPLS` to get back to the menu.

To shutdown, run `SHUTDOWN` then `LOGOFF` then press Ctrl+] and at the c3270 prompt type `quit`.

Alternatively, using line mode (instead of 3270):

1. `telnet localhost 33351`
2. `LOGON HERC01/CUL8TR`
3. `SHUTDOWN`
4. `LOGOFF`
5. Ctrl+] then `quit`
