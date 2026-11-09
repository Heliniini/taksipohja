# Taksipohja (arabia) – yksityinen kuljettaja Marokossa

Arabiankielinen, oikealta vasemmalle (RTL) toimiva yhden sivun kotisivupohja. Toteutus on pelkkää HTML:ää ja CSS:ää sekä vähän JavaScriptiä, eikä sivu tarvitse palvelinta tai tietokantaa.

## Tiedostot

| Tiedosto | Sisältö |
| --- | --- |
| `index.html` | Etusivu: hero, palvelut, hinnasto, varauslomake, kuljettaja ja auto, palautteet, UKK, yhteystiedot |
| `styles.css` | Tyylit. Värit ja fontit ovat tiedoston alussa. Käyttää suuntaneutraaleja ominaisuuksia (`inline-start/end`), joten toimii myös `dir="ltr"`-sivuilla. |
| `khususiya.html` | Tietosuojaselosteen pohja (سياسة الخصوصية) |
| `fontit/` | Tajawal- ja Noto Kufi Arabic -fontit sivuston omina tiedostoina (OFL-lisenssi, vapaa käyttää) |
| `kuvat/` | Lisää tänne auton ja kuljettajan kuvat |

## Miten varaus toimii

Varauslomake **ei lähetä tietoja mihinkään palvelimeen**. JavaScript kokoaa kentistä valmiin viestin ja avaa WhatsAppin (`wa.me`-linkki), jolloin asiakas lähettää varauksen suoraan kuljettajalle. Tämä ratkaisu sopii hyvin Marokkoon:

- WhatsApp on siellä yleisin tapa sopia kyydeistä.
- Hostingiin ei tarvita lomakepalvelua eikä kuukausimaksuja.
- Kuljettaja vahvistaa hinnan ja ajan viestillä. Maksu suoritetaan yleensä käteisellä kyydin jälkeen.

**Vaihda WhatsApp-numero** kaikkiin kohtiin: hae tiedostosta `212600000000` ja `+212 600 000 000`. Lomakkeen numero on `data-whatsapp`-attribuutissa (maatunnus ilman +-merkkiä).

Jos myöhemmin tarvitaan verkkomaksu tai kalenteri, johon näkyvät varatut ajat, sivulle voi lisätä linkin valmiiseen ajanvarausjärjestelmään.

## Muokattavat kohdat

Kaikki muokattavat kohdat on merkitty koodiin kommentilla `MUOKKAA` tai hakasulkeilla `[ ]`:

1. Nimi, kaupunki, puhelinnumero ja sähköposti (myös `<head>`-osan JSON-LD-tiedot)
2. Hinnat: ovat **esimerkkejä**, kysy todelliset hinnat kuljettajalta
3. Kuljettajan tarina, auton malli ja lupanumero
4. Maksutavat ja peruutusehdot UKK:ssa
5. Kuvat: korvaa `<div class="kuvapaikka">` `<img>`-tagilla
6. Asiakaspalautteet: vain todellisia ja luvan kanssa

## Kieliversiot

Marokossa ranska on arabian ohella yleinen kieli, ja turisteja palvellaan usein englanniksi. Pohjassa on valmiina kielivalinta (ع / FR / EN) ja `hreflang`-merkinnät:

1. Kopioi `index.html` kansioihin `fr/` ja `en/`.
2. Vaihda kopioihin `<html lang="fr" dir="ltr">` (tai `lang="en"`).
3. Korjaa polut: `../styles.css`, `../fontit/…`
4. Käännä tekstit. Tekoäly kääntää hyvin, mutta **tarkistuta käännökset aina jollakulla, jonka äidinkieli kyseinen kieli on**. Sama koskee arabiankielistä pohjatekstiä.

Sama CSS toimii kaikissa kieliversioissa sellaisenaan.

## RTL-muistilista

- Puhelinnumerot, sähköpostit, hinnat ja lennon numerot kääritään `<span class="ltr">`-elementtiin, jotta ne eivät mene sekaisin.
- Käytä CSS:ssä aina `margin-inline-start` / `padding-inline-end` / `text-align: start` jne., ei `left`/`right`.
- Suuntaa näyttävät kuvakkeet (nuolet) pitää kääntää peilikuvaksi.
- Marokossa käytetään yleisesti länsimaisia numeroita (0–9), joten niitä ei tarvitse muuttaa itäarabialaisiksi.

## Julkaisu

Sama kuin suomalaisessa pohjassa: GitHub → Cloudflare Pages tai Netlify. Marokkolainen `.ma`-verkkotunnus ostetaan paikalliselta rekisterinpitäjältä. Vaihtoehtoisesti `.com` toimii mainiosti.

## Huomioita kuljettajan kanssa

- **Taksiluvat:** Marokossa taksiliikenne ja henkilökuljetus ovat luvanvaraisia. Varmista, että kuljettajalla on toimintaan vaadittavat luvat. Sivustolla luvatut palvelut, esimerkiksi kaupunkien väliset kyydit, pitää kuulua luvan piiriin.
- **Tietosuoja:** Marokon tietosuojalaki on 09-08 ja valvova viranomainen CNDP. Pohjan tietosuojaseloste on vain lähtökohta.
- Google-yritysprofiili ja kuljettajan WhatsApp Business -profiili kannattaa linkittää samaan verkko-osoitteeseen.
