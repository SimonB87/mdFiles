Pracovní postup – HTML Coder
============================

(verze 1.1)

1.  Pro testování vyvíjený aplikací slouží prostředí **testovacího serveru**, kde je možné pracovat v prostředí ekvivalentním produkčnímu.
2.  Webové stránky splňují následující standardy:
    -   [HTML 5.0](http://validator.w3.org/)
    -   [CSS 3.0](http://jigsaw.w3.org/css-validator/)
    -   [JavaScript with „The Good Parts“](http://www.jslint.com/)
    -   [WCAG 1.0](http://www.cynthiasays.com/)
    -   Všechny knihovny jsou linkovány lokálně
    -   CSS kód načítán pomocí importu "@import url('/style1.css')"
    -   Veškerý CSS a JS kód umístěn na konci stránky před tagem </body>
    -   V HTML tagu pro načítání skriptů umístěn atribut „async“
3.  Všechny aplikace jsou vyvýjeny na frameworku [Bootstrap 4](http://www.getbootstrap.com/).
4.  Pro úpravu bitmapové grafiky slouží program [Gimp](https://www.gimp.org/). Výstupní formát soborů odevzdávaných projektů je [XCF.GZ](https://en.wikipedia.org/wiki/XCF_(file_format)).
5.	Program Gimp je použit také pro tvorbu [image map](https://docs.gimp.org/en/plug-in-imagemap.html).
6.  Pro úpravu vektorové grafiky slouží programu [Inkscape](https://inkscape.org/).
Výstupní formát soborů odevzdávaných projektů je [SVGZ](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics#Compression).
7.  Podporované vývojové prostředí je [Geany](https://geany.org/).
8.	Pro snadnější úpravu finálního vzhledu webových stránek doporučujeme doplněk do prohlížeče [Web Developer](http://chrispederick.com/work/web-developer/).
9.	Výsledná aplikace bude optimalizována pro prohlížeče **MS Edge 25+**, **Firefox 50+**, **Chrome 50+**.
10. Výsledek práce bude obsahovat:
    -   Git repository:
        -   **HTML, CSS a JS kód** projektu
        -	**Všechny použité obrázky** ve formátu [PNG](https://en.wikipedia.org/wiki/Portable_Network_Graphics) pro bitmapy a [SVG](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics) pro vektory
    -   Testovací server:
        -   **Plně funkční** verze stránek
