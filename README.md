# SerwisSamochodow
Serwis do prowadzenia wypożyczalni samochodów
Krótki opis systemu
W ramach projektu należy utworzyć system umożliwiający prowadzenie wypożyczalni samochodów w kilku miastach. System ma pozwalać na rezerwację, wypożyczenia oraz zwroty samochodów. Dodatkowo powinien wyliczać przychody wypożyczalni i prezentować podstawowe statystyki.
Główne funkcje systemu
Rezerwacja samochodu
Wypożyczanie samochodu
Zwrot samochodu
Zarządzanie listą siedzib
Zarządzanie flotą oraz ich obecną lokalizacją
Wyliczanie przychodów
Statystyki
Technologie
Spring + Hibernate
(opcjonalnie) Frontend w Angular
Podstawowe byty (propozycja)
Wypożyczalnia
nazwa
domena internetowa
adres kontaktowy
właściciel
2 | 6
logotyp
lista oddziałów
Oddział
adres (z miastem)
lista pracowników placówki
lista aktualnie dostępnych aut
Pracownik
imię
nazwisko
stanowisko (PRACOWNIK/MANAGER)
oddział, w którym pracuje
Samochód
marka
model
typ nadwozia
rocznik
kolor
przebieg
status (WYPOŻYCZONY/DOSTĘPNY/NIEDOSTĘPNY) – status dotyczy konkretnego terminu; niedostępny tzn. popsuty, w naprawie, w przeglądzie itd.
kwota (za dzień wypożyczenia)
Klient
imię
3 | 6
nazwisko
email
adres
Rezerwacja
data rezerwacji
klient
samochód
data od
data do
oddział wypożyczenia
oddział zwrotu
kwota
Wypożyczenie (powstaje na podstawie Rezerwacji)
pracownik
data wypożyczenia
rezerwacja
uwagi
Zwrot (powstaje na podstawie Rezerwacji)
pracownik
data zwrotu
rezerwacja
dopłata
uwagi
4 | 6
Przychody
suma kwot za wypożyczanie aut
Funkcjonalności
Konfigurowanie wypożyczalni
- system pomyślany jest tak, by można go było sprzedawać do dowolnej sieci wypożyczalni
- powinien umożliwiać skonfigurowanie Wypożyczalni, czyli podaniu nazwy, domeny, adresu, właściciela i logotypu
- z poziomu wypożyczalni zarządza się Oddziałami: dodaje/zamyka
Zarządzanie oddziałami
- każdy oddział posiada listę pracowników
- w każdym oddziale powinien być Manager
- każdy oddział posiada listę aktualnie dostępnych aut w danej lokalizacji w danym terminie
- (opcjonalnie) mechanizm prezentujący informację, gdy w danym terminie dostępne jest tylko 1 lub 2 auta
Samochody
- samochody nie są na stałe przypisane do konkretnej siedziby
- można je wypożyczać i oddawać w różnych oddziałach (za dodatkową opłatą)
- należy aktualizować przebieg samochodów oraz kwotę za wypożyczenie
- ustawiać im odpowiedni status; jeśli nie można go wypożyczyć z przyczyn innych niż wypożyczenie w danym terminie (np. przegląd, awaria)
- należy prezentować ich status w danym terminie
- (opcjonalnie) prosty mechanizm filtrujący po parametrach samochodów (marka, model, rocznik, kolor; można dodać inne parametry)
5 | 6
Klient
- wypożyczalnia powinna posiadać listę klientów
- w podstawowej formie może to być predefiniowana lista
- (opcjonalnie) klient powinien mieć możliwość założenia konta i logowania
Rezerwacja samochodu
- samochód rezerwowany jest przez konkretnego klienta, na konkretny termin
- podczas rezerwacji należy podać oddział odbioru i zwrotu auta (może być różny)
- system powinien wyliczyć całościową kwotę za wypożyczenie (np. mnożąc ilość dni oraz dodając stałą kwotę za oddanie w innym miejscu niż wypożyczenie)
- rezerwacje można anulować np. na 2 dni przed datą wypożyczenia (bez opłat); później zwracane jest 80% kwoty
- (opcjonalnie) system może posiadać promocje ze względu na ilość wypożyczeń, przejechanych kilometrów, okresu świątecznego, wakacyjnego itd. (program lojalnościowy)
Wypożyczenie samochodu
- zdarzenie w systemie: pracownik wypożycza na podstawie rezerwacji auto
- dodatkowo zapisuje ewentualne uwagi
Zwrot samochodu
- zdarzenie w systemie: pracownik odbiera na podstawie rezerwacji auto
- dodatkowo zapisuje ewentualne uwagi
- ewentualnie wpisuje kwotę dopłaty (w związku z przekroczeniem czasu, szkodami itd.)
- (opcjonalnie) można rozszerzyć Rezerwację z generowaniem faktury oraz dodatkowej faktury dla dopłaty (aby odseparować płatności od rezerwacji i zwrotów)
Naliczanie przychodu
- w odpowiednich momentach powinien się aktualizować przychód, tj.
6 | 6
Rezerwacja: przychód wzrasta o kwotę z rezerwacji
Anulowanie Rezerwacji: przychód maleje o kwotę z rezerwacji
Anulowanie Rezerwacji (późne): przychód maleje o 80% z rezerwacji
Dopłata przy zwrocie: przychód wzrasta o kwotę z dopłaty
- należy przemyśleć sposób zliczania i prezentowania pieniędzy, np. trzymać w osobnych kolumnach kwoty zatwierdzone i niezatwierdzone (te, które będzie trzeba zwrócić)
- (opcjonalnie) rozbudowa systemu ze względu na faktury oraz opłaty/kaucje za rezerwacje itd.
Moduł statystyk
- statystyki przychodów z podziałem na oddziały, miasta i pracowników
- statystyki najpopularniejszych tras (najczęściej wybierany oddział pobierania i zwrotu auta)
- statystyki najpopularniejszych oddziałów, miast pobierania auta
- statystyki najpopularniejszych oddziałów, miast zwrotu auta
- statystyki najpopularniejszych aut
- (opcjonalnie) statystyki anulowanych rezerwacji (per odziały, pracowników, auta)
Dodatkowe wymagania
- należy zadbać o estetyczny i funkcjonalny sposób prezentowania danych
- dane pobierane od użytkowników powinny być wstępnie walidowane
