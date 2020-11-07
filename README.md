# Czas (nadszedł)

Aby zbudować taki obraz z aplikacją, należy napisać utworzyć prosty plik html ze stroną(albo go pobrać, albo przepisać) - generalnie należy wyposażyć się w działający plik html zwany dalej aplikacją.
 Obraz można utworzyć na kilka sposobów, oprócz sposobów polegający na klonowaniu repozytorium, oraz pobieraniu plików, można też samemu napisać dockerfila:
 
 Sposób I - napisanie dockerfile
 1. Uruchomienie konsoli w pliku, w którym pożądane jest utworzenie dockerfile'a.
 2. Wpisanie utworzenie pliku np. "touch Dockerfile" i otworzenie go w dowolnym edytorze tekstowym, np "nano Dockerfile".
 3. W pierwszej linijce należy wpisać z jakiego obrazu będziemy korzystać - "FROM sebp/mini_httpd"
 4. W drugiej linijce można wpisać komendę, która umieści aplikację w kontenerze przy jego tworzeniu - "COPY <nazwa_pliku_albo_ścieżka> /var/www/localhost/htdocs",
np. "COPY aplikacja.html /var/www/localhost/htdocs", albo "COPY . /var/www/localhost/htdocs"(to skopiuje caly plik w którym się znajdujemy)
 5. Zapisać zmiany i na podstawie tego dockerfila zbudować obraz poleceniem "docker build -f Dockerfile -t obraz1"
 6. Następnie na podstawie obrazu można tworzyć kontenery
 
 Jeśli zależy nam na stworzeniu kontenera dla naszej aplikacji, można też po prostu pobrać obraz sebp/mini_httpd poleceniem "pull sebp/mini_httpd", a następnie przy uruchamianiu, lub zaraz po nim dodać naszą aplikację:
 wykonać polecenie "docker run --name obraz1 -d -v "$(pwd)":/var/www/localhost/htdocs -p 2020:80 obraz1" które potraktuje obecny plik jako volumen dołączany do kontenera
 albo
 wykonać polecenie "docker run --name obraz1 -d -p 2020:80 obraz1" oraz polecenie "docker cp <nazwa_aplikacji> /var/wwww/localhost/htdocs", które skopiuje do kontenera naszą aplikację
