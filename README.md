# nova-glosowka

Nagrywarka głosówek dla komendy `/glosowka` bota Discord NOVA Signs (statyczna strona na GitHub Pages).
Bot daje zarządowi jednorazowy link `?t=<token>` (ważny 15 min); strona nagrywa dźwięk w przeglądarce i wysyła go do
webhooka n8n (`glosowka-wyslij`), który przepisuje nagranie (Whisper) i wrzuca je z transkrypcją do wątku na Discordzie.

Strona nie zawiera sekretów — bez ważnego tokenu z Discorda n8n odrzuca nagranie. Strona nie stoi na n8n, bo n8n
podaje HTML z webhooków w piaskownicy CSP, w której przeglądarki blokują mikrofon.
