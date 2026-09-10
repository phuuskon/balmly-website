# Balmly — Kriisiseula, vihamielisyyskehote ja käyttöehtojen hyväksyntä

**Status: juristin tarkistama ja hyväksymä, toteutettu ja laitetestattu (ks. kohta 6).**

**Markkina:** Yhdysvallat (sovelluksen saatavuus rajattu Yhdysvaltoihin).

---

## 1. Konteksti: mitä nämä ruudut tekevät ja miksi

Balmly on sovellus, jolla käyttäjä kuvailee toisen ihmisen (ystävän, perheenjäsenen) vaikean tilanteen, ja AI kirjoittaa henkilökohtaisen lohdutusviestin + raamatunjakeen + rukouksen lähetettäväksi kyseiselle henkilölle.

Ennen jokaista generointia käyttäjän kuvaus analysoidaan kahden asian varalta:

- **Kriisi**: viittaako kuvaus konkreettiseen itsetuhoisuuden tai väkivallan suunnitelmaan, keinoon tai ajankohtaan (tai jatkuvaan itsensä vahingoittamiseen), kolmatta osapuolta (ei käyttäjää itseään) koskien.
- **Vihamielisyys**: vaikuttaako kuvauksen sävy syyllistävältä/kostonhaluiselta sitä henkilöä kohtaan jolle viesti on tarkoitus lähettää.

Jos kriisi tunnistetaan, normaali polku (jae+viesti+rukous) ohitetaan kokonaan ja käyttäjälle näytetään sen sijaan kiinteä, ei-AI-generoitu teksti kriisiresursseineen. Jos vihamielisyys tunnistetaan, käyttäjälle näytetään pehmeä, ei-estävä kehote harkita uudelleen — käyttäjä voi aina jatkaa.

**Rajaus:** tunnistus on AI-pohjainen luokittelu, ei täydellinen eikä takuuvarma. Tuotekehityksessä on tietoisesti priorisoitu väärien negatiivien minimointia kriisiakselilla, mutta tätä ei esitetä käyttäjälle takuuna — ks. disclaimer kohdassa 4.

---

## 2. Ruutu — Käyttöehtojen hyväksyntä (uusi, juristin vaatima)

Näytetään ensimmäisenä ruutuna, ennen mitään muuta toimintoa, vain kerran per asennus. Eksplisiittinen clickwrap-hyväksyntä — pelkkä ehtojen linkittäminen valikkoon (browsewrap) ei olisi juristin arvion mukaan riittävä USA:n oikeuskäytännössä.

### Otsikko
> Before you start

### Selitys
> Balmly helps you write a message of encouragement for someone else. It is not a medical, counseling, or crisis service. Please review our Terms of Service and Privacy Policy.

### Valintaruutu (Continue-painike lukittu kunnes rastitettu)
> I agree to the Terms of Service and Privacy Policy, and understand Balmly is not a medical or crisis service.

### Painike
> Get Started

---

## 3. Ruutu 3a — Kriisiseula (näytetään kun kriisi=true)

**Ei paluuta samaan syötteeseen tästä ruudusta.** Ainoa toiminto on aloittaa uusi viesti alusta.

### Otsikko
> It sounds like this situation requires immediate support.

### Selitys
> We've paused message creation because the description mentions potential self-harm, violence, or an immediate emergency. Please reach out to trained professionals right away:

### Hätänumero (näytetään ensimmäisenä, korostettuna omalla kortillaan)
> In immediate physical danger? Call 911.

### Resurssit (napautettavat: soitto/tekstiviesti suoraan)
> **CALL OR TEXT, 24/7**
> **988**
> Suicide & Crisis Lifeline (US) · tap to call
>
> **PREFER TEXTING**
> **Text HOME to 741741**
> Crisis Text Line · tap to open a message

### Ainoa painike
> Start a new message

---

## 4. Ruutu 3b — Vihamielisyyskehote (näytetään kun hostility=true)

**Ei estä etenemistä.** Molemmat painikkeet ovat visuaalisesti tasavertaisia, ei oletusvalintaa.

### Otsikko
> Consider reviewing your note before sending.

### Selitys
> The language entered includes strong or accusatory tone. While you can still generate a message, messages containing conflict or anger may not achieve the comforting result you intend.

### Näytetään käyttäjän oma teksti
> **WHAT YOU WROTE**
> [käyttäjän kirjoittama kuvaus sanasta sanaan]

### Painikkeet (tasavertaiset)
> Edit Description | Continue Anyway

---

## 5. Käyttöehdot & disclaimer (Legal-ruutu)

Linkitetty sekä käyttöehtojen hyväksyntäruudulta että myöhemmin sovelluksen asetuksista. Näytetään kokonaisuudessaan omalla ruudullaan.

### Otsikko
> Terms of Service & Disclaimer

### Sisältö
> Balmly is an automated tool designed solely to assist with creative writing and offer faith-based encouragement. Balmly is NOT a medical device, mental health provider, crisis intervention service, or substitute for professional care, counseling, or emergency services.
>
> Although Balmly includes automated safety checks to detect potential crisis indicators, these features are automated, imperfect, and provided "AS IS". Balmly does not monitor user activity in real-time, cannot guarantee the detection of any risk, and does not dispatch emergency services. NEVER rely on this app to assess risk or secure emergency help. If you or someone else is in immediate danger, call 911 or contact a national crisis lifeline (such as calling or texting 988 in the US) immediately.
>
> Balmly is intended solely for use within the United States.

---

## 6. Toteutustilanne

| Osa | Tila |
|---|---|
| Käyttöehtojen hyväksyntäruutu | Toteutettu, laitetestattu |
| Kriisiseula (3a) + 911 | Toteutettu, laitetestattu. **Katso kohta 7 — kriteerin laajuus toisen lausunnon mukaan uudelleenarvioitavana.** |
| Vihamielisyyskehote (3b) | Toteutettu, laitetestattu |
| Legal-ruutu (disclaimer) | Toteutettu, laitetestattu |
| Täysi Terms of Service | **Avoinna** — vaatii oman erillisen läpikäynnin yhdysvaltalaisen asianajajan kanssa. Versiohistoria dokumentoitava kun valmis (toisen lausunnon lisävaatimus). |
| Hostattu Privacy Policy -sivu | **Avoinna** — App Store Connect vaatii tämän pakollisena metadatakenttänä. |
| Markkinointitekstien linjakkuus disclaimerin kanssa | **Uusi, avoinna** — ks. kohta 8. Tarkistettava App Store -kuvausteksti, verkkosivu, onboarding-kopio ennen julkaisua: ei ilmaisuja kuten "mental health support" tai "helps process trauma" missään käyttäjälle näkyvässä tekstissä. |

---

## 7. Toinen lakilausunto: kriisikriteerin laajuus (avoin kysymys)

Riippumaton toinen juristi katsoi ensimmäisen lausunnon pääosin oikeansuuntaiseksi, mutta kyseenalaisti nykyisen kriisikriteerin sanan "imminent" liian kapeana ja ehdotti korvaamista laajalla muotoilulla ("any indication of self-harm, suicide, suicidal ideation... or risk of harm to self or others").

**Ei toteutettu suoraan.** Nykyinen kapea kriteeri on validoitu 40 tapauksen evaluaatiolla (1.00/1.00 precision/recall), ja se on tietoisesti rajattu niin ettei se laukea tavallisesta, voimakkaastakin surusta ilman konkreettista merkkiä (suunnitelma/keino/valmistautuminen) — tämä on sovelluksen lippulaivakategorian (suru/menetys) toimivuuden kannalta välttämätön raja. Toisen lausunnon ehdottama laaja muotoilu laukaisisi todennäköisesti suuren osan normaaleista suru-/sairauskuvauksista.

**Sovittu jatkotoimenpide:** lisätään eval-settiin tapauksia jotka testaavat onko "imminent"-sana otsikkotasolla harhaanjohtava suhteessa jo olemassa olevaan, laajempaan bullet-listaan (suunnitelma/keino/ajankohta EI vaadi kaikkien kolmen yhtäaikaista täyttymistä, valmistautumisteko riittää yksinään). Jos testi paljastaa aidon aukon, korjataan otsikkolause täsmällisemmäksi — ei korvata koko kriteeriä rajattomalla muotoilulla joka veisi tuotteen ydintoiminnon.

## 8. Markkinointitekstien ja käyttöliittymän linjakkuus (uusi tarkistuskohta)

Toinen lausunto nosti esiin kohdan joka puuttui ensimmäisestä kokonaan: **pelkkä disclaimer-ruutu ei riitä**, jos mikään muu käyttäjälle näkyvä teksti (App Store -kuvaus, verkkosivu, onboarding-kopio, markkinointimateriaali) antaa ymmärtää sovelluksen tarjoavan enemmän kuin se tekee — esim. ilmaisut kuten "mental health support" tai "helps you process trauma".

**Tarkistettava ennen julkaisua:** App Store -kuvausteksti, mahdollinen verkkosivu, kaikki onboarding- ja markkinointikopio — ei mitään joka viittaisi terapeuttiseen, lääketieteelliseen tai kriisipalvelu-rooliin. Tuotespeksin oma tagline ("words for someone you love") ja mikrokopiotyyli ovat jo linjassa tämän kanssa, mutta tarkistus pitää tehdä eksplisiittisesti kun App Store -kuvaus kirjoitetaan.

## 9. Miksi vain Yhdysvallat

Kriisiresurssit (988, 741741) ovat Yhdysvaltain-spesifisiä. Sovelluksen saatavuus on rajattu Yhdysvaltoihin App Storessa/Play Storessa juuri tästä syystä — muun maan käyttäjä ei voisi käyttää näytettyjä numeroita.

---

## 10. Tekninen tarkennus tunnistuskriteereistä (taustatiedoksi, ei julkaistavaa tekstiä)

Nykyinen kriisin tunnistuskriteeri (LLM-promptin sisältö, ei käyttäjälle näkyvä):

> Set crisis=true when the description contains a concrete sign of imminent self-harm or violence toward others: a plan, a means, or a timeframe; a preparatory act (giving possessions away, writing goodbye messages, researching or acquiring a method, sorting out affairs "for everyone"); a recent attempt together with current intent; OR ongoing/repeated self-harm, whether or not the person has said anything about wanting to die.

Ei laukea: arkikielen liioittelu ("kuolen häpeästä"), epämääräinen ahdistus ilman konkreettista merkkiä, menneisyydessä ratkaistu tilanne, tumma huumori jonka kirjoittaja itse kuittaa vaarattomaksi.

Sisäiseen dokumentaatioon suositellaan kirjattavaksi juristin sanoin: *"Safety filter is a best-effort automated boundary, not a safety-critical clinical monitoring system."*

---

*Tämä dokumentti kuvaa sovelluksessa toteutetun, juristin hyväksymän tilan syyskuussa 2026. Kohdassa 6 mainitut avoimet kohdat (täysi ToS, hostattu Privacy Policy) vaativat vielä oman työnsä ennen App Store -julkaisua.*
