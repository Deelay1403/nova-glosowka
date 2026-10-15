# nova-glosowka

Nagrywarka głosówek dla komendy `/glosowka` bota Discord NOVA Signs (statyczna strona na GitHub Pages).
Bot daje zarządowi jednorazowy link `?t=<token>` (ważny 15 min); strona nagrywa dźwięk w przeglądarce i wysyła go do
webhooka n8n (`glosowka-wyslij`), który przepisuje nagranie (Whisper) i wrzuca je z transkrypcją do wątku na Discordzie.

Strona nie zawiera sekretów — bez ważnego tokenu z Discorda n8n odrzuca nagranie. Strona nie stoi na n8n, bo n8n
podaje HTML z webhooków w piaskownicy CSP, w której przeglądarki blokują mikrofon.

## Kolejność zdjęć do posta (`zdjecia.html`)

Przycisk „📷 Zdjęcia” pod propozycją posta FB/IG daje link `zdjecia.html?k=<klucz>` (ważny 30 min, tylko ten wątek).
Strona pobiera z n8n (`social-kolejnosc`, automatyzacja 25) miniatury zdjęć i filmów z wątku, pozwala ułożyć je
przeciąganiem (SortableJS — działa też palcem na telefonie) i zapisuje kolejność. n8n tworzy nową wersję propozycji
i pisze w wątku „📷 Kolejność zdjęć”, po czym bot odświeża propozycję.
