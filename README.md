# nova-glosowka

Nagrywarka głosówek dla komendy `/glosowka` bota Discord NOVA Signs (statyczna strona na GitHub Pages).
Bot daje zarządowi jednorazowy link `?t=<token>` (ważny 15 min); strona nagrywa dźwięk w przeglądarce i wysyła go do
webhooka n8n (`glosowka-wyslij`, automatyzacja 27). Po nagraniu wybierasz:
- **📝 Dalej: sprawdź i opublikuj** (`tryb=szkic`) — n8n przepisuje nagranie (Whisper) i od 45 s robi podsumowanie AI;
  strona pokazuje podsumowanie i transkrypcję do poprawki, a **✅ Opublikuj** (`akcja=opublikuj`, z tym samym nagraniem)
  wrzuca do wątku podsumowanie, nagranie i `transkrypcja.txt`. Szkic czeka 24 h: nagranie trzyma IndexedDB, poprawki
  localStorage, a ten sam link (`akcja=odczyt`) otwiera szkic ponownie,
- **🤖 Wykonaj przez /ai** (`tryb=ai`) — do wątku nic nie trafia; bot bierze transkrypcję jako polecenie `/ai`
  i pokazuje odpowiedź (albo zmiany do zatwierdzenia) tylko wywołującemu.

Strona nie zawiera sekretów — bez ważnego tokenu z Discorda n8n odrzuca nagranie. Strona nie stoi na n8n, bo n8n
podaje HTML z webhooków w piaskownicy CSP, w której przeglądarki blokują mikrofon.

## Kolejność zdjęć do posta (`zdjecia.html`)

Przycisk „📷 Zdjęcia” pod propozycją posta FB/IG daje link `zdjecia.html?k=<klucz>` (ważny 30 min, tylko ten wątek).
Strona pobiera z n8n (`social-kolejnosc`, automatyzacja 25) miniatury zdjęć i filmów z wątku, pozwala ułożyć je
przeciąganiem (SortableJS — działa też palcem na telefonie) i zapisuje kolejność. n8n tworzy nową wersję propozycji
i pisze w wątku „📷 Kolejność zdjęć”, po czym bot odświeża propozycję.
