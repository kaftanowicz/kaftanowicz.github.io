---  
date: 2015-03-07 19:43:06+00:00
layout: single
title: Co to znaczy znać jakąś liczbę?
lang: pl
categories: ['Philosophy']
excerpt: Filozofia potrzebuje złożoności obliczeniowej.
---  
W chwili, gdy piszę te słowa, największą znaną liczbą pierwszą jest [2^57885161-1](http://www.mersenne.org/primes/?press=M57885161). Ponieważ liczb pierwszych jest nieskończenie wiele, prędzej czy później ktoś odkryje kolejną, jeszcze większą.  

Na przykład ja. Proszę: niech _n_ = "kolejna liczba pierwsza po 2^57885161-1", albo bardziej precyzyjnie, "najmniejsza liczba pierwsza większa od 2^57885161-1". Liczba _n_ jest pierwsza (z definicji) i jest większa od największej znanej do tej pory liczby pierwszej (też z definicji). Jest też jednoznacznie określona -- ta definicja pasuje tylko do jednej liczby.  

Powiesz, że oszukuję? Masz rację. Intuicyjnie wszyscy czują, że definicja tej "mojej" liczby pierwszej, chociaż jednoznaczna, jest w jakiś sposób gorsza od zapisu takiego jak [2^ileśtam-1](http://mathworld.wolfram.com/MersennePrime.html). Czy da się tę intuicję ująć bardziej formalnie?  

Pójdźmy teraz o jeden poziom abstrakcji wyżej i zastanówmy się, co to znaczy "znać" jakąś liczbę.  

Czy trzeba do tego mieć jej rozwinięcie dziesiętne? Liczba 2^57885161-1 ma 17425170 cyfr. Zapisanie jej zajęłoby ponad 1936 godzin, czyli 242 dni pisania po 8 godzin dziennie i prawie 10 000 stron A4. Większe liczby będą wymagały jeszcze więcej pracy, a prędzej czy później zostaną odkryte liczby pierwsze zbyt duże, by ich rozwinięcie dziesiętne zmieściło się w pamięci operacyjnej jakiegokolwiek pojedynczego komputera.   

Wydaje się, że bardziej zwięzły zapis, jak na przykład 2^k-1, jest wystarczający (plus, oczywiście, dowód, że ta liczba jest pierwsza). Z drugiej strony, słowa "kolejna liczba pierwsza po tej" nie wystarczą, żebyśmy uznali taką liczbę za znaną.  

Okazuje się, że można elegancko rozwiązać ten paradoks. Trzeba do tego użyć pojęcia [złożoności obliczeniowej](http://mathworld.wolfram.com/ComplexityTheory.html). Algorytm obliczający liczbę zdefiniowaną jako 2^k-1 jest wielomianowy względem k -- to znaczy, że funkcja opisująca czas potrzebny na zadziałanie takiego algorytmu jest wielomianem zmiennej k. Nie istnieje natomiast algorytm wielomianowy obliczający liczbę pierwszą na podstawie definicji takiej, jak "następna liczba pierwsza po 2^k-1".  

Mówiąc prościej, definicja liczby pierwszej w postaci wzoru takiego jak 2^k-1 wystarcza, żeby odpowiedni algorytm komputerowy mógł efektywnie wyznaczyć tę liczbę. Definicja, która na to nie pozwala, słusznie wydawała nam się "oszukana".  

O tym, dlaczego algorytmy wielomianowe mogą mieć duże znaczenie nie tylko w matematyce, ale i w filozofii, na czym polega słynny problem P kontra NP, co to tak naprawdę znaczy "efektywnie wyznaczyć liczbę" i o innych fajnych rzeczach z pogranicza matematyki, informatyki i filozofii można poczytać w bardzo przystępnym artykule Scotta Aaronsona [Dlaczego filozofowie powinni zajmować się złożonością obliczeniową](http://www.scottaaronson.com/papers/philos.pdf). Stamtąd -- rozdział 3.3, _Known Integers_ -- wziąłem powyższy przykład.
