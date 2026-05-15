---
name: common-ground
description: >-
  Toetst gemeentelijke IT-implementaties aan de Common Ground principes:
  data bij de bron, API-first architectuur, open standaarden, gescheiden
  applicatie- en datalaag. Bevat GEMMA-koppeling, voorbeeldimplementaties
  (Haven, NL Design System, SensRNet), en migratiestrategieën van zaakgericht
  naar informatiekundig werken.
  Gebruik deze skill wanneer de gebruiker vraagt over 'Common Ground',
  'informatiekundige kern', 'data bij de bron', 'gemeentelijke IT',
  'zaakgericht werken', 'GEMMA API's', 'Haven', 'NL Design System', 'NLDS',
  'SensRNet', 'mijn-zaken', 'gemeentelijke architectuur', 'API-first overheid',
  'informatiekundige visie', 'digitale transformatie gemeenten',
  'omgevingswet IT', 'WOO IT', 'gemeentelijk ICT-beleid',
  of wanneer de gebruiker een gemeentelijk IT-project wil toetsen
  aan Common Ground.
model: sonnet
allowed-tools:
  - WebFetch(*)
---

# Common Ground Compliance Checker

Toets gemeentelijke IT-implementaties aan de Common Ground principes. Common Ground is de informatiekundige visie van de Nederlandse gemeenten: een radicale herziening van hoe gemeenten hun IT inrichten — van gesloten monolithische systemen naar een open, API-gedreven, data-gecentreerd ecosysteem.

Bron: [Common Ground](https://commonground.nl/) | [GEMMA Online](https://www.gemmaonline.nl) | [VNG Realisatie](https://www.vngrealisatie.nl/)

## De 5 Common Ground Principes

```
1. DATA BIJ DE BRON
   ├── Gegevens worden NIET gekopieerd tussen systemen
   ├── Elke dataset heeft één eigenaar/bronhouder
   ├── Andere systemen BEVRAGEN de bron via API's
   └── Voorbeeld: BRP-gegevens blijven in BRP, niet gekopieerd naar 15 applicaties

2. GESCHEIDEN APPLICATIE- EN DATALAAG
   ├── Data-laag: registraties, bronbestanden, gestandaardiseerd en API-ontsloten
   ├── Applicatie-laag: proceslogica, formulieren, taken, rapportages
   ├── NIET: data en logica verweven in één pakket (vendor lock-in)
   └── Dit is de TECHNISCHE kern van Common Ground

3. API-FIRST — ALLES VIA OPEN, GESTANDAARDISEERDE API'S
   ├── Elke component communiceert exclusief via API's
   ├── API's conform NL Gov REST API Design Rules (v2.0)
   ├── Geen directe database-koppelingen (view/grant) — ALTIJD via API
   └── API's zijn open, gedocumenteerd (OpenAPI v3+), en herbruikbaar

4. OPEN STANDAARDEN — FORUM STANDAARDISATIE
   ├── Gebruik verplichte Forum Standaardisatie-standaarden
   ├── Gegevensuitwisseling: StUF-uitfasering → REST-API's, NEN 2660 (informatiemodellen)
   ├── Berichten: Digikoppeling (ebMS2, WUS, REST-API)
   └── Geen vendor-specifieke protocollen en formaten

5. GEMEENTELIJKE SAMENWERKING & HERBRUIKBAARHEID
   ├── Bouw componenten één keer, gebruik door alle gemeenten
   ├── Open source tenzij dwingende reden (NORA BP07)
   ├── Gemeenschappelijke voorzieningen (GEMMA, VNG-referentiecomponenten)
   └── De markt innoveert, de overheid standaardiseert
```

## Common Ground Referentie Architectuur

```
GEBRUIKERS LAAG — Burger, medewerker, bedrijf
   ├── NL Design System (NLDS) componenten
   └── MijnZaken, formulieren, portalen
─────────────────────────────────────────
APPLICATIE LAAG — Processen & functionaliteit
   ├── Zaakafhandeling, workflow, samenwerking
   ├── Taakgericht werken, stuurinformatie
   └── Toegang via API's tot datalaag
─────────────────────────────────────────
API LAAG — Gestandaardiseerde koppelvlakken
   ├── REST API's conform NL Gov API Design Rules
   ├── Digikoppeling voor GDI-koppelingen
   └── API Gateway (bijv. Haven)
─────────────────────────────────────────
DATA LAAG — Registraties & bronnen
   ├── Basisregistraties: BRP, BRK, BAG, etc.
   ├── Kernregistraties: Zaken, Documenten, etc.
   └── Domeinspecifiek: WMO, Jeugd, Omgevingswet
```

## Haven — API Gateway voor Common Ground

**Haven** is de open-source API-gateway van VNG Realisatie voor gemeenten:

| Kenmerk | Beschrijving |
|---------|-------------|
| **Doel** | Centraal toegangspunt voor alle gemeentelijke API's; beveiliging, logging, autorisatie |
| **Functies** | API-key management, OAuth2/OIDC, rate limiting, request logging, analytics |
| **Standplaats** | Draait in of nabij de gemeentelijke infrastructuur |
| **Open source** | Ja, MPL-2.0 licentie |

**Check:** Gebruikt het project Haven als API-gateway, of een gelijkwaardig open alternatief?

## NL Design System (NLDS)

Gemeenschappelijke UI-componentenbibliotheek voor alle overheidsorganisaties:

- **Doel:** Herkenbare, consistente, toegankelijke gebruikersinterface voor alle overheidsdiensten
- **Componenten:** Buttons, formulieren, navigatie, tabellen, kaarten, formulieren, etc.
- **Toegankelijkheid:** Voldoet aan WCAG 2.1 AA (EN 301 549)
- **Integratie:** React, Angular, Web Components beschikbaar

**Check:** Gebruikt het project NLDS-componenten voor de frontend?

## Common Ground Migratiestrategie

Migreren van zaakgericht (monolieten) naar informatiekundig (Common Ground):

```
FASE 1: ONTVLECHTEN (0-12 maanden)
├── Inventariseer: welke data zit in welke systemen?
├── Identificeer: wat is de bron van elke dataset?
├── Stop: kopiëren van data tussen systemen
└── Start: API-ontsluiting van kernregistraties

FASE 2: API-ONTSLUITEN (6-18 maanden)
├── Bouw API's voor elke registratie (conform NL Gov API Design Rules)
├── Implementeer Haven als API-gateway
├── Richt autorisatie in (OAuth 2.0 / OIDC)
└── Start met eerste herbruikbare component

FASE 3: COMPONENTEN VERVANGEN (12-36 maanden)
├── Vervang monolithische modules één voor één door API-gedreven componenten
├── Elk component communiceert ALLEEN via API's
├── Data blijft in bronsystemen
└── Herbruikbare componenten delen met andere gemeenten

FASE 4: ECOSYSTEEM OPERATIONEEL (24-48 maanden)
├── Volledig API-gedreven IT-landschap
├── Gemeenschappelijke voorzieningen actief
├── Vendor-onafhankelijk: componenten uitwisselbaar
└── Continue doorontwikkeling in gemeentelijke samenwerking
```

## Common Ground Compliance Checklist

- [ ] **Data bij de bron**: Worden gegevens NIET gekopieerd? Blijft elke dataset bij de bronhouder?
- [ ] **Gescheiden lagen**: Is er een duidelijke scheiding tussen data-, API- en applicatielaag?
- [ ] **API-first**: Communiceren ALLE componenten via API's? (geen directe DB-koppelingen!)
- [ ] **REST API Design Rules**: Voldoen de API's aan NL Gov REST API Design Rules v2.0?
- [ ] **OpenAPI documentatie**: Zijn API's gedocumenteerd als OpenAPI v3+ specificatie?
- [ ] **Haven of API Gateway**: Is er een open API-gateway geïmplementeerd?
- [ ] **NLDS**: Wordt het NL Design System gebruikt voor de UI?
- [ ] **Open standaarden**: Worden Forum Standaardisatie-standaarden consequent toegepast?
- [ ] **GEMMA-compliance**: Is de oplossing conform GEMMA (processen, informatiemodellen)?
- [ ] **Open source**: Zijn de componenten open source of is er een 'leg uit'?
- [ ] **Herbruikbaarheid**: Kan de component door andere gemeenten worden hergebruikt?
- [ ] **Geen vendor lock-in**: Is de oplossing component-gewijs vervangbaar zonder totale migratie?
- [ ] **Autorisatie**: Is OAuth 2.0 / OIDC geïmplementeerd voor API-toegang?
- [ ] **Logging en monitoring**: Worden API-calls gelogd en gemonitord?
- [ ] **NEN 2660**: Wordt NEN 2660 (SOR) toegepast voor informatiemodellering?

## StUF Uitfasering

Het StUF-standaard (Standaard Uitwisselingsformaat) wordt uitgefaseerd:

| Van | Naar |
|-----|------|
| StUF-koppelingen | REST-API's (NL Gov API Design Rules) |
| StUF-BG, StUF-ZKN | API-standaarden voor Zaken (RGBZ 2.0) en Documenten |
| Berichtverkeer via SOAP | REST + JSON + OpenAPI |
| Point-to-point koppelingen | API-gateway (Haven) |

**Check:** Worden er nog StUF-koppelingen gebouwd of is de oplossing volledig REST/API?

## VNG Referentiecomponenten

Overzicht van beschikbare en geplande componenten in het ecosysteem:

| Component | Fase | Omschrijving |
|-----------|------|-------------|
| **Objectregistratie** | Productie | Generieke registratie voor objecten (bomen, lantaarnpalen, afvalbakken) |
| **Klantinteractie** | Productie | Contactmomenten, klantvragen |
| **MijnZaken** | Productie | Burgertoegang tot eigen zaken |
| **Zaken** | In ontwikkeling | Generieke zaakregistratie API |
| **Documenten** | In ontwikkeling | Documentbeheer als API |
| **Besluiten** | In ontwikkeling | Besluitenregistratie API |
| **Processen** | In ontwikkeling | Procesmodellering en -uitvoering |
| **Archief** | Planfase | E-depot API's voor duurzame toegankelijkheid |

## Meer informatie

- [Common Ground](https://commonground.nl/)
- [GEMMA Online](https://www.gemmaonline.nl)
- [VNG Realisatie](https://www.vngrealisatie.nl/)
- [Haven API Gateway](https://haven.commonground.nl/)
- [NL Design System](https://nldesignsystem.nl/)
- [NL Gov API Design Rules](https://logius-standaarden.github.io/API-Design-Rules/)
- [NORA Online](https://www.noraonline.nl)
- [Forum Standaardisatie](https://www.forumstandaardisatie.nl/open-standaarden)
- [SensRNet](https://sensrnet.nl/) — Sensorenregister Common Ground
