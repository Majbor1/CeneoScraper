# CeneoScraper

## Kod produktu, o którm będą pobierane opinie
84514582

## Algorytm pobierania opinii o pojedynczym produkcie z serwisu Ceneo.pl
1. Wysłanie żądania dostępu do strony z opiniami o produkcie.
2. Jeśli operacja zakończy się sukcesem, wyodrębnienie z kody strony fragmentów odpowiadających poszczególnym opiniom
3. Dla każdej z wyodrębnionej opinii wydobycie z kodu HTML poszczególnych składowych i zapisanie ich w postaci złożonych struktur danych.
4. Jeśli istnieje kolejna strona z opiniamii, przejście na następną stronę i powtórzenie dla niej kroków 1-4.
5. Zapisanie wszystkich opinii w bazie danych.

## Struktura opinii w serwisie Ceneo.pl
|składnia|zmienna|selektor|
|--------|-------|--------|
|opinia|review|div.js_product-review|
|identyfikator opinii|review_id|.js_product-review["data-entry-id"]|
|autor|author|span.user-post__author-name|
|rekomendacja|recomendation|span.user-post__author-recomendation > em|
|liczba gwiazdek|stars|span.user-post__score-count|
|treść opinii|content|div.user-post__text|
|listę zalet|pros|div.review-feature__item--positive|
|listę wad|cons|div.review-feature__item--negative|
|ile osób uznało opinię za przydatną|likes|button.vote-yes > span|
|ile osób uznało opinię za nieprzydatną|dislikes|button.vote-no > span|
|data wystawienia opinii|publish_date|span.user-post__published > time:nth-child(1)['datetime']|
|data zakupu produktu|purchase_date|span.user-post__published > time:nth-child(2)['datetime']|