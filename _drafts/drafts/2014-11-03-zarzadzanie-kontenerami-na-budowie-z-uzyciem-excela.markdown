---
author: admin
comments: true
date: 2014-11-03 19:44:20+00:00
excerpt: '[:pl]Użyteczna sztuczka dla młodych inżynierów budownictwa.[:]'
layout: post
link: http://kaftanowicz.com/zarzadzanie-kontenerami-na-budowie-z-uzyciem-excela/
slug: zarzadzanie-kontenerami-na-budowie-z-uzyciem-excela
title: Zarządzanie kontenerami na budowie z użyciem Excela
wordpress_id: 115
---

[:pl][caption id="attachment_116" align="aligncenter" width="300"][![źródło: http://www.container-lion.com/en/news-2011-05-Airport-Kassel-Calden.php](http://kaftanowicz.com/wp-content/uploads/2014/11/container-300x168.jpg)](http://kaftanowicz.com/wp-content/uploads/2014/11/container.jpg) źródło: http://www.container-lion.com/en/news-2011-05-Airport-Kassel-Calden.php[/caption]

Jeśli jesteś młodym inżynierem i pójdziesz do pracy na budowie u generalnego wykonawcy, jednym z pierwszych zadań, które dostaniesz od swojego kierownika, będzie zarządzanie kontenerami.

Oczywistym rozwiązaniem jest mapka. Zastanowisz się nad tym chwilę i jeżeli Moc jest w tobie słaba, to ulegniesz studenckim przyzwyczajeniom i spróbujesz zrobić ją w AutoCADzie. Przegoń tę myśl; do rysowania prostokątów wypełnionych łatwym do zmieniania tekstem służy Excel. Włączasz więc kilka obramowań i masz swoją pierwszą mapkę kontenerów.

<!-- more -->Kontenery budowlane stawia się jeden na drugim, więc widok z boku jest lepszy niż rzut z góry. Ile komórek potrzebujesz na każdy kontener? Każdy z nich ma jakiś numer, musisz też zapisać, jaka firma akurat go używa. Dwie komórki wystarczą? Nie, bo w czasie trwania budowy kontener może przechodzić z rąk do rąk. W jednej komórce wpisujesz więc aktualnego użytkownika, a w drugiej - listę poprzednich, koniecznie z datami przekazania i zwrotu kontenera; wpisywanie każdej firmy i każdej daty w osobnych komórkach popsułoby przestrzenne relacje naszej mapki.

Po pewnym czasie wymyślisz ułatwiające orientację oznaczenia kolorystyczne, na przykład błękit na magazyn, oraz inne symbole. Twoja mapka będzie wyglądać na przykład tak:

[![zk1](http://kaftanowicz.com/wp-content/uploads/2014/11/zk1-300x243.png)](http://kaftanowicz.com/wp-content/uploads/2014/11/zk1.png)

Powyżej widać lekko zmieniony fragment arkusza, którego sam używałem do zarządzania zapleczem na budowie kompleksu [GBC](http://www.hbreavis.com/gdanski-business-center-i). Jest bardzo wygodny i czytelny - do chwili, gdy przyjdzie czas na podliczenie, ile różne firmy są nam winne za wynajem. W powyższym układzie wymaga to znalezienia (CTRL+F) nazwy każdej firmy, które to nazwy będą zdublowane w sytuacji, gdy firma dalej używa kontenera w momencie rozliczenia, i przepisania dat wynajmu do osobnego arkusza. Mam też nadzieję, że kontenery wyjeżdżające z budowy wycinałeś do osobnego arkusza...? Musi istnieć lepsze rozwiązanie.

Mamy dane o kontenerach, ich użytkownikach i datach użytkowania i chcemy wpisywać i odczytywać je tylko raz. Pomyślałeś w tym momencie o relacyjnej bazie danych? Ale budowanie bazy danych dla takiej liczby rekordów to lekki _overkill_, nie mówiąc już o tym, że twoje dzieło musi być przystępne dla innych użytkowników, w tym kierownika budowy, który może nie mieć cierpliwości do informatycznych wynalazków, i młodszego nawet od ciebie inżyniera, któremu przekażesz kiedyś zaszczytny obowiązek zarządzania zapleczem.

Rozwiązanie, które jest lepsze i jednocześnie dalej proste, składa się z dwóch arkuszy w Excelu (lub jakimś jego darmowym odpowiedniku - w moim przypadku to LibreOffice Calc). Pierwszy arkusz to mapka, która przedstawia przestrzenne ustawienie kontenerów.

Każdy kontener to 3 komórki: numer, rodzaj (magazyn, socjalny dla pracowników, biurowy dla kierownictwa) i aktualny użytkownik. Ręcznie wpisujemy jedynie numer; informacje o rodzaju i aktualnym użytkowniku są wczytywane z drugiego arkusza za pomocą formuły WYSZUKAJ.PIONOWO.

[![zk2](http://kaftanowicz.com/wp-content/uploads/2014/11/zk2-300x210.png)](http://kaftanowicz.com/wp-content/uploads/2014/11/zk2.png)

Drugi arkusz to tabela, do której wprowadzamy informacje o firmach używających kontenerów. Kiedy nowa firma przejmuje kontener, musimy wstawić nowy wiersz i przekleić poprzednich użytkowników w dół; nazwa aktualnego użytkownika musi być zawsze w tym samym wierszu, co numer kontenera. Ta niewygodna procedura to cena za czytelność tabeli i prostotę formuły wyłuskującej z niej informacje potrzebne na mapce. Rozdzielenie części graficznej od tabeli danych pozwala na usuwanie kontenerów z mapki, gdy opuszczają budowę, bez utraty informacji o czasach ich wynajmu.

[![zk3](http://kaftanowicz.com/wp-content/uploads/2014/11/zk3-300x146.png)](http://kaftanowicz.com/wp-content/uploads/2014/11/zk3.png)

Co teraz, gdy przyjdzie Dzień Rozliczenia? Tym razem załatwimy go jedną tabelą przestawną, z nazwami firm w obszarze kolumn, numerami kontenerów w obszarze wierszy i czasem wynajmu (policzonym automatycznie) w obszarze danych.

[![zk4](http://kaftanowicz.com/wp-content/uploads/2014/11/zk4-300x165.png)](http://kaftanowicz.com/wp-content/uploads/2014/11/zk4.png)

 _Voilà!_ Łączne czasy wynajmu dla poszczególnych firm podliczają się same.

[![zk5](http://kaftanowicz.com/wp-content/uploads/2014/11/zk5-300x123.png)](http://kaftanowicz.com/wp-content/uploads/2014/11/zk5.png)

Powyższy arkusz w formacie programu LibreOffice Calc jest [do pobrania całkiem za darmo](http://kaftanowicz.com/wp-content/uploads/2014/11/Zarzadzanie-kontenerami-na-budowie.ods).[:]
