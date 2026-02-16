# Muisti tekoälyagenteille  
[![Agent Memory](../../../translated_images/fi/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Keskusteltaessa tekoälyagenttien ainutlaatuisista eduista, puhutaan pääasiassa kahdesta asiasta: kyvystä kutsua työkaluja tehtävien suorittamiseen ja kyvystä kehittyä ajan myötä. Muisti on perustana itseään parantavan agentin luomiselle, joka voi tarjota parempia kokemuksia käyttäjillemme.

Tässä oppitunnissa tarkastelemme, mitä muisti tarkoittaa tekoälyagenteille ja miten voimme hallita ja käyttää sitä sovellustemme hyväksi.

## Johdanto

Tässä oppitunnissa käsitellään:

• **Tekoälyagenttien muistin ymmärtäminen**: Mitä muisti on ja miksi se on agenttien kannalta tärkeää.

• **Muistin toteuttaminen ja tallentaminen**: Käytännön menetelmiä muistikapasiteetin lisäämiseksi tekoälyagenteille, keskittyen lyhyt- ja pitkäaikaiseen muistiin.

• **Itseään parantavien tekoälyagenttien tekeminen**: Kuinka muisti mahdollistaa agenttien oppimisen aiemmista vuorovaikutuksista ja kehittymisen ajan kuluessa.

## Saatavilla olevat toteutukset

Tässä oppitunnissa on kaksi kattavaa muistotekniikka-aiheista muistiinpanoa:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Toteuttaa muistin käyttäen Mem0:aa ja Azure AI Searchia Semantic Kernel -kehykseen pohjautuen

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Toteuttaa rakenteellisen muistin Cogneen avulla, rakentaa automaattisesti upotusten tukeman tietämyskartan, visualisoi kaavion ja tarjoaa älykkään haun

## Oppimistavoitteet

Kun olet suorittanut tämän oppitunnin, osaat:

• **Erotella erilaiset tekoälyagenttien muistin tyypit**, mukaan lukien työmuisti, lyhytkestoinen ja pitkäkestoinen muisti sekä erikoistuneet muodot kuten persoonamuisti ja episodinen muisti.

• **Toteuttaa ja hallita lyhyt- ja pitkäaikaista muistia tekoälyagenteille** Semantic Kernel -kehystä hyödyntäen, käyttäen työkaluja kuten Mem0, Cognee, Whiteboard-muistia ja integroiden Azure AI Searchiin.

• **Ymmärtää itseään parantavien tekoälyagenttien periaatteet** ja kuinka vankat muistinhallintajärjestelmät tukevat jatkuvaa oppimista ja sopeutumista.

## Tekoälyagenttien muistin ymmärtäminen

Perusolemukseltaan **tekoälyagenttien muisti tarkoittaa mekanismeja, joiden avulla ne voivat säilyttää ja palauttaa tietoa**. Tämä tieto voi olla esimerkiksi yksityiskohtia keskustelusta, käyttäjän mieltymyksiä, aiempia toimenpiteitä tai opittuja kaavoja.

Ilman muistia tekoälysovellukset ovat usein tilattomia, eli jokainen vuorovaikutus alkaa alusta. Tämä johtaa toistuviin ja turhauttaviin käyttäjäkokemuksiin, joissa agentti "unohtaa" aiemman kontekstin tai mieltymykset.

### Miksi muisti on tärkeä?

Agentin älykkyys liittyy syvästi kykyyn palauttaa ja hyödyntää aiemmin saatuja tietoja. Muisti mahdollistaa agenttien olevan:

• **Heijastavia**: Oppien menneistä toimista ja tuloksista.

• **Vuorovaikutteisia**: Säilyttäen keskustelun kontekstin käynnissä olevan vuorovaikutuksen ajan.

• **Aloitteellisia ja reagoivia**: Ennakoiden tarpeita tai reagoiden historiallisten tietojen perusteella.

• **Autonomisia**: Toimien itsenäisemmin turvautuen tallennettuun tietoon.

Muistin toteuttamisen tavoitteena on tehdä agenteista **luotettavampia ja kykenevämpiä**.

### Muistityypit

#### Työmuisti

Ajattele tätä kuin luonnospaperia, jota agentti käyttää yhden tehtävän tai ajatusprosessin aikana. Se pitää välittömän tiedon, jota tarvitaan seuraavan vaiheen laskemiseen.

Tekoälyagenteille työmuisti tallentaa usein keskustelun olennaisimmat tiedot, vaikka koko keskusteluhistoria olisi pitkä tai katkaistu. Se keskittyy poimimaan keskeiset elementit, kuten vaatimukset, ehdotukset, päätökset ja toimenpiteet.

**Työmuistin esimerkki**

Matkavarausagentissa työmuisti saattaa tallentaa käyttäjän nykyisen pyynnön, kuten "Haluan varata matkan Pariisiin". Tämä tarkka vaatimus pidetään agentin välittömässä kontekstissa ohjaamaan nykyistä vuorovaikutusta.

#### Lyhytkestoinen muisti

Tämä muistityyppi säilyttää tietoa yhden keskustelun tai istunnon ajan. Se on nykyisen keskustelun konteksti, jonka avulla agentti voi viitata aiempiin vuorovaikutuksen vaiheisiin.

**Lyhytkestoisen muistin esimerkki**

Jos käyttäjä kysyy "Kuinka paljon lento Pariisiin maksaa?" ja jatkaa "Entä majoitus siellä?", lyhytkestoinen muisti varmistaa, että agentti ymmärtää "siellä" viittaavan samaan keskustelussa mainittuun "Pariisiin".

#### Pitkäkestoinen muisti

Tämä on tieto, joka säilyy useiden keskustelujen tai istuntojen yli. Se antaa agenteille mahdollisuuden muistaa käyttäjän mieltymyksiä, historiallisia vuorovaikutuksia tai yleistä tietoa pitkällä aikavälillä. Tämä on tärkeää personoinnissa.

**Pitkäkestoisen muistin esimerkki**

Pitkäkestoinen muisti voisi sisältää tiedon, että "Ben viihtyy laskettelun ja ulkoilun parissa, pitää kahvista vuoristonäkymällä ja haluaa välttää vaativia laskettelurinteitä aiemman vamman takia". Tämä tieto, opittu aiemmista vuorovaikutuksista, vaikuttaa suosituksiin tulevissa matkasuunnittelusessioissa, tehden niistä hyvin henkilökohtaisia.

#### Persoonamuisti

Tämä erikoistunut muistityyppi auttaa agenttia kehittämään johdonmukaisen "persoonallisuuden" tai "roolin". Se antaa agentille mahdollisuuden muistaa tietoja itsestään tai roolistaan, tehden vuorovaikutuksista sujuvampia ja fokusoituneempia.

**Persoonamuistin esimerkki**  
Jos matkatoimistoagentti on suunniteltu olemaan "asiantuntijalaskettelun suunnittelija", persoonamuisti voi vahvistaa tätä roolia, vaikuttaen sen vastauksiin vastaamaan asiantuntijan tyyliä ja tietoja.

#### Työnkulku/Episodinen muisti

Tämä muisti tallentaa järjestyksen, jossa agentti suorittaa monimutkaisen tehtävän, mukaan lukien onnistumiset ja epäonnistumiset. Se on kuin tietyn "jakson" tai aiempien kokemusten muistamista oppimista varten.

**Episodisen muistin esimerkki**

Jos agentti yritti varata tietyn lennon, mutta epäonnistui saatavuuden puutteen takia, episodinen muisti voisi kirjata tämän epäonnistumisen, jolloin agentti voi yrittää vaihtoehtoisia lentoja tai kertoa käyttäjälle asiasta paremmin seuraavalla yrityksellä.

#### Entiteettimuisti

Tähän kuuluu tiettyjen entiteettien (kuten ihmisten, paikkojen tai asioiden) ja tapahtumien poimiminen keskusteluista ja muistaminen. Se antaa agentille mahdollisuuden rakentaa rakenteellinen ymmärrys käsitellyistä keskeisistä elementeistä.

**Entiteettimuistin esimerkki**

Keskustelusta aiemmasta matkasta agentti voi poimia "Pariisi", "Eiffel-torni" ja "illallinen ravintolassa Le Chat Noir" entiteetteinä. Tulevassa vuorovaikutuksessa agentti voisi muistaa "Le Chat Noir" ja ehdottaa uuden varauksen tekemistä sinne.

#### Rakenneperusteinen RAG (Retrieval Augmented Generation)

Vaikka RAG on laajempi tekniikka, "Rakenneperusteinen RAG" korostuu voimakkaana muistiteknologiana. Se poimii tiivistä, rakenteellista tietoa eri lähteistä (keskusteluista, sähköposteista, kuvista) ja käyttää tätä parantaakseen tarkkuutta, palautusta ja nopeutta vastauksissa. Toisin kuin klassinen RAG, joka perustuu vain semanttiseen samankaltaisuuteen, rakenneperusteinen RAG hyödyntää tiedon luonnollista rakennetta.

**Rakenneperusteisen RAGin esimerkki**

Pelkkien avainsanojen yhteensovittamisen sijaan RAG voi purkaa lentotiedot (kohde, päivä, aika, lentoyhtiö) sähköpostista ja tallentaa ne rakenteellisessa muodossa. Tämä mahdollistaa täsmälliset kyselyt kuten "Millä lennolla varasin matkan Pariisiin tiistaina?"

## Muistin toteuttaminen ja tallentaminen

Muistin toteuttaminen tekoälyagenteille on järjestelmällinen prosessi nimeltään **muistinhallinta**, johon kuuluu tiedon tuottaminen, tallentaminen, hakeminen, integrointi, päivittäminen ja jopa "unohtaminen" (tai poistaminen). Hakeminen on erityisen tärkeä osa.

### Erikoistuneet muistityökalut

#### Mem0

Yksi tapa tallentaa ja hallita agentin muistia on käyttää erikoistuneita työkaluja kuten Mem0:aa. Mem0 toimii pysyvänä muistikerroksena, jonka avulla agentit voivat palauttaa olennaiset vuorovaikutukset, tallentaa käyttäjäasetuksia ja todellista kontekstia sekä oppia onnistumisista ja epäonnistumisista ajan myötä. Ajatuksena on, että tilattomat agentit muuttuvat tilallisiksi.

Se toimii **kaksivaiheisen muistiputken avulla: poiminta ja päivitys**. Ensiksi agentin ketjuun lisätyt viestit lähetetään Mem0-palveluun, joka käyttää laajaa kielimallia (LLM) keskusteluhistorian tiivistämiseen ja uusien muistojen poimintaan. Tämän jälkeen LLM-pohjainen päivitysvaihe päättää, lisätäänkö, muokataanko vai poistetaanko muistoja, tallentaen ne hybriditietokantaan, joka voi sisältää vektori-, kaavio- ja avain-arvotietokantoja. Järjestelmä tukee myös erilaisia muistityyppejä ja voi sisältää kaaviomuistin entiteettien välisen suhteen hallinnointiin.

#### Cognee

Toinen tehokas lähestymistapa on käyttää **Cogneea**, avointa lähdekoodia olevaa semanttista muistia tekoälyagenteille, joka muuntaa rakenteellisen ja rakenteettoman datan upotuksiin perustuviksi kysyttävissä oleviksi tietämyskaavioiksi. Cognee tarjoaa **kaksikerroksisen arkkitehtuurin**, joka yhdistää vektorisamanlaisuushaun ja kaaviosuhteet, mahdollistaen agenttien ymmärtämisen pelkän tiedon samankaltaisuuden sijaan myös käsitteiden välisistä suhteista.

Se on erinomainen **hybridihakumenetelmä**, joka yhdistää vektoripohjaisen samankaltaisuuden, kaavion rakenteen ja LLM-pohjaisen päättelyn – raakapalojen hakemisesta kaaviotietoiseen kyselyyn. Järjestelmä ylläpitää **elävää muistia**, joka kehittyy ja kasvaa, mutta pysyy silti kysyttävänä yhtenä yhdistettynä kaaviona, tukeen sekä lyhytkestoista istuntokontekstia että pitkäaikaista pysyvää muistia.

Cogneen muistiinpano-opetusmateriaali ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) havainnollistaa tämän yhtenäisen muistikerroksen rakentamista käytännön esimerkkien kautta, jotka käsittelevät monipuolisten datalähteiden syöttämistä, tietämyskaavion visualisointia ja erilaisilla hakustrategioilla kyselyä agentin tarpeiden mukaan.

### Muistin tallentaminen RAGilla

Erikoistuneiden muistityökalujen kuten Mem0:n lisäksi voit hyödyntää vankkoja hakupalveluita, kuten **Azure AI Searchia, muistojen tallennuksen ja hakemisen taustajärjestelmänä**, erityisesti rakenteelliselle RAGille.

Tämä mahdollistaa agenttisi vastausten pohjaamisen omiin tietoihisi, varmistaen relevantimpia ja täsmällisempiä vastauksia. Azure AI Searchia voidaan käyttää tallentamaan käyttäjäkohtaisia matkamuistoja, tuotekatalogeja tai muuta toimialakohtaista tietoa.

Azure AI Search tukee ominaisuuksia kuten **rakenneperusteinen RAG**, joka loistaa poimiessaan ja noutaessaan tiivistä, rakenteellista tietoa suurista tietoaineistoista, kuten keskusteluhistorioista, sähköposteista tai jopa kuvista. Tämä tarjoaa "yliluonnollisen tarkkuuden ja palautuksen" perinteiseen tekstin palasteluun ja upotustekniikoihin verrattuna.

## Itseään parantavien tekoälyagenttien tekeminen

Yleinen malli itseään parantaville agenteille sisältää **"tietämysagentin"**. Tämä erillinen agentti tarkkailee pääasiallista keskustelua käyttäjän ja primäärin agentin välillä. Sen tehtävänä on:

1. **Tunnistaa arvokas tieto**: Määrittää, onko mikään osa keskustelusta säästämisen arvoista yleisenä tietona tai erityisenä käyttäjäasetuksena.

2. **Poimia ja tiivistää**: Tiivistää olennaisen oppimisen tai mieltymyksen keskustelusta.

3. **Tallentaa tietämyskantaan**: Säilyttää tämä poimittu tieto, usein vektoripohjaisessa tietokannassa, jotta se voidaan hakea myöhemmin.

4. **Täydentää tulevia kyselyjä**: Kun käyttäjä aloittaa uuden kyselyn, tietämysagentti hakee asiaankuuluvaa tallennettua tietoa ja liittää sen käyttäjän kehotteeseen, tarjoten keskeisen kontekstin primäärille agentille (samoin kuin RAG).

### Muistinhallinnan optimoinnit

• **Viiveen hallinta**: Käyttäjävuorovaikutusten hidastamisen välttämiseksi voidaan aluksi käyttää halvempi ja nopeampi malli nopeasti tarkistamaan, onko tieto tallentamisen tai haun arvoista, ja kutsua monimutkaisempi poiminta/haku vain tarpeen mukaan.

• **Tietämyskannan ylläpito**: Kasvavassa tietämyskannassa harvemmin käytetty tieto voidaan siirtää "kylmään varastoon" kustannusten hallitsemiseksi.

## Onko sinulla lisää kysymyksiä agenttimuistista?

Liity [Azure AI Foundry Discord](https://aka.ms/ai-agents/discord) -palveluun tavata muita oppijoita, osallistua toimistoaikoihin ja saada vastauksia tekoälyagenttien kysymyksiisi.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastuuvapauslauseke**:  
Tämä asiakirja on käännetty tekoälypohjaisella käännöspalvelulla [Co-op Translator](https://github.com/Azure/co-op-translator). Vaikka pyrimme tarkkuuteen, on hyvä huomioida, että automaattikäännöksissä voi esiintyä virheitä tai epätarkkuuksia. Alkuperäistä asiakirjaa sen alkuperäisellä kielellä tulee pitää virallisena lähteenä. Tärkeissä asioissa suosittelemme ammattimaista ihmiskääntäjää. Emme ole vastuussa tämän käännöksen käytöstä aiheutuvista väärinymmärryksistä tai virhetulkinnoista.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->