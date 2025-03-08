# Pracownicy

Jest to aplikacja robiona przez mój zespół w ramach przedmiotu Bazy Danych 2 na Politechnice Warszawskiej.

## Autorzy

Mateusz Kiełbus <br>
Nel Kułakowska <br>
Marcin Wawrzyniak <br>
Albert Torzewski

## Instalacja własnej instancji bazy danych

Instrukcja do instalacji własnej instancji bazy danych znajduje się pod adresem https://github.com/oracle/docker-images/tree/main/OracleDatabase/SingleInstance#how-to-build-and-run. Użyte komendy:

1. ./buildContainerImage.sh -v 19.3.0 -t oracle_database_19_3_0_s_e:oracle_db -s
2. sudo docker run --name oracle_db_19_3_0_s_e -d -p 1521:1521 -p 5500:5500 -p 2484:2484 --ulimit nofile=1024:65536 --ulimit nproc=2047:16384 --ulimit stack=10485760:33554432 --ulimit memlock=3221225472 -e ORACLE_SID=oracleSID -e ORACLE_PDB=oraclePDB -e ORACLE_PWD=password -e ORACLE_EDITION=standard oracle_database_19_3_0_s_e:oracle_db

## O aplikacji

Używaliśmy Oracle do bazy danych stawianej na dockerze. Aplikacja napisana została przy użyciu Flask.
Aplikacja uruchamiana jest przez `python3 app.py`.
W folderze baza_danych znajdują się skrypty do utworzenia bazy danych.

Aplikacja pozwala nam na zarządzanie danymi osobowymi pracowników naszej firmy.

## Uruchomienie

Należy otworzyć aplikację przeglądarki i wpisać jako adres URL http://localhost:5000/ <br>
W pliku baza_danych/insertdata.sql od linii 261 znajdują się loginy pracowników. Hasło to password (w bazie danych są zapisane hasze haseł).

## Inicjalizacja bazy danych

Do inicjalizacji bazy danych należy wykorzystać skrypty z folderu baza_danych w podanej kolejności:

1. create_tables_views.ddl
2. insertdata.sql
3. triggery.sql
4. procedury.sql
5. indexes.sql
