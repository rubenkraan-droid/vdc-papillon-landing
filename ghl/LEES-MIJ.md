# Tricolore-variant, opgesplitst voor GoHighLevel

Plakvolgorde in de funnelstap:

1. **Custom Code blok** -> `blok-a-boven.html`
   Alles van de navigatie tot en met de CTA-kop "Plan uw Zoom-gesprek, of vraag eerst de brochure aan".
2. **Natief GHL-formulier** -> "Gesprek inplannen"
3. **Natief GHL-formulier** -> "Brochure aanvragen"
4. **Custom Code blok** -> `blok-b-footer.html`
   De twee blokjes "wat er gebeurt nadat u verzendt", de belregel en de footer.

## Instellingen per rij
Zet de rij op **volle breedte** en **padding 0**. De blokken hebben zelf een
full-bleed wrapper (`.mp-fb`), maar met een smalle rij eromheen gaat dat vechten.

## Ankers
Alle knoppen op de pagina scrollen naar `#aanvragen`. Dat is de CTA-sectie
onderaan blok A, dus precies boven de formulieren. Je hoeft op de
formuliersecties **geen** sectie-ID te zetten.

## Tekens (belangrijk)
Beide bestanden zijn **volledig ASCII**: geen accenten, geen HTML-entities.
GHL decodeert entities en serveert ze daarna met de verkeerde charset, waardoor
je mojibake krijgt. Daarom komen het euroteken, de scheidingspunt, het vinkje en
het kruisje via CSS-escapes binnen:

    .eu::before{content:"\20AC"}   ->  euroteken
    .dot::before{content:"\00B7"}  ->  scheidingspunt
    .ico.ok::before{content:"\2713"}
    .ico.no::before{content:"\2715"}

Pas je tekst aan? Gebruik dan **geen** accenten of speciale tekens direct in de
HTML, maar dezelfde truc, anders verhaspelt GHL het alsnog.

## Formuliervelden
- **Gesprek**: bij voorkeur een GHL **Calendar**, zodat iemand een tijdslot kiest
  en dus bewust om een belafspraak vraagt.
- **Brochure**: alleen e-mail en voornaam verplicht, **geen** verplicht
  telefoonveld, met een optioneel vinkje "bel mij". Alleen dat vinkje leidt tot
  een belverzoek.
