﻿# Gruyere-Fix
 
XSS - ošetření vstupních hodnot - pužití html modulu s funkcí escape pro konverzi znaků

Příklady úprav:
V metodě _DoLogin bylo přidáno escapování uživatelského jména pomocí html.escape(uid)
V metodě _DoNewsnippet2 bylo přidáno escapování textu snippetu před jeho vložením do databáze


XSRF

Každé uživatelské session je nyní přiřazen jedinečný XSRF token, tím je zajištěno, že request pochází od oprávněného uživatele

Příklady úprav:
Byla implementována metoda _GenerateXSRFToken, která generuje jedinečný token pro session
V metodě _DoLogin je po úspěšném přihlášení generován a uložen XSRF token
Metoda _DoDeletesnippet nyní vyžaduje validní XSRF token k provedení operace
