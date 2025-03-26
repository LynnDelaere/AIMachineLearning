# Chapter 8: The naive Bayes model

## Het naive Bayes theorema is gebaseerd op prior probability, posterior probability en event.
**Hoe staan deze drie in relatie tot elkaar en geef een concreet voorbeeld?**
- **Prior probability:** De initiële kans op een bepaalde uitkomst, voordat er enige informatie over de uitkomst bekend is. Voorbeeld: Wat is de kans dat een mail spam is voordat we weten of het woord 'sale' erin voorkomt?
- **Event:** Een gebeurtenis die plaatsvindt en nieuwe informatie oplevert. Voorbeeld: Een mail ontvangen met het woord 'sale' erin.
- **Posterior probability:** De uiteindelijke kans die we berekenen nadat we de prior probability hebben gecombineerd met de informatie van het event. Voorbeeld: Wat is de kans dat een mail spam is nadat we weten dat het woord 'sale' erin voorkomt?
**Wat veronderstelt het naive Bayes theorema?**
Het naive Bayes theorema veronderstelt dat de features onafhankelijk zijn van elkaar. Dit betekent dat de aanwezigheid van een bepaalde feature geen invloed heeft op de aanwezigheid van een andere feature. In de context van spamdetectie betekent dit dat de aanwezigheid van het woord 'sale' in een mail geen invloed heeft op de aanwezigheid van het woord 'discount'.

## Toon aan dat P(spam|'sale') = 0.60 als volgende gegevens beschikbaar zijn:
**de dataset bestaat uit 100 mails**
**P(spam) = 20/100**
**6/20 van de spam mails bevat het woord 'sale'**
**4/80 van de ham mails bevat het woord 'sale’**
**Wat betekent P(spam|’sale’)?**
We berekenen eerst de individuele kansen:

- **P(spam) = 20/100 = 0.20**  
- **P(ham) = 80/100 = 0.80**  
- **P('sale' | spam) = 6/20 = 0.30**  
- **P('sale' | ham) = 4/80 = 0.05**  

We berekenen de kans dat een mail spam is en het woord *'sale'* bevat met de productregel:

**P('sale' ∩ spam) = P('sale' | spam) × P(spam)**  
= **0.30 × 0.20 = 0.06**  

Vervolgens berekenen we de kans dat een mail het woord *'sale'* bevat met de wet van de totale kans:

**P('sale') = P('sale' ∩ spam) + P('sale' ∩ ham)**  

Eerst berekenen we **P('sale' ∩ ham)**:

**P('sale' ∩ ham) = P('sale' | ham) × P(ham)**  
= **0.05 × 0.80 = 0.04**  

Nu berekenen we **P('sale')**:  
**P('sale') = 0.06 + 0.04 = 0.10**  

Tot slot berekenen we **P(spam | 'sale')** met het Bayes-theorema:  

**P(spam | 'sale') = P('sale' | spam) × P(spam) / P('sale')**  
= **0.06 / 0.10 = 0.60**  


## Wat om schrijft de ‘rule of complementary probabilities’?
De 'rule of complementary probabilities' beschrijft dat voor een gebeurtenis A, de kans op de complementaire gebeurtenis (niet-A) gelijk is aan 1 minus de kans op A. Dit kan worden uitgedrukt als: **P(A') = 1 - P(A)**. Bijvoorbeeld, als de kans op regen 0.30 is, dan is de kans op geen regen 0.70.

## Wat is de wiskundigevorm van het Bayes theorem?
Het Bayes-theorema kan worden uitgedrukt als:
**P(F | E) = P(E | F) × P(F) / P(E)**
waarbij:
- **P(F | E)** de posterior probability: de kans dat gebeurtenis F plaatsvindt gegeven dat gebeurtenis E heeft plaatsgevonden.
- **P(E | F)** de likelihood: de kans dat gebeurtenis E plaatsvindt gegeven dat gebeurtenis F heeft plaatsgevonden.
- **P(F)** de prior probability: de initiële kans op gebeurtenis F voordat er enige informatie over gebeurtenis E bekend is.
- **P(E)** de normaliseringsconstante: de kans op gebeurtenis E.


## Wat omschrijft de ‘product rule for independent probabilities’?
De 'product rule of independent probabilities' omschrijft wat de kans is dat twee onafhankelijke gebeurtenissen tegelijkertijd plaatsvinden. Volgens deze regel is de kans op de intersectie van twee onafhankelijke gebeurtenissen gelijk aan het product van de afzonderlijke kansen van elk van die gebeurtenissen. Dit kan worden uitgedrukt als: **P(E ∩ F) = P(E) × P(F)**. 

## Wat betekent de wiskundige uitdrukking 𝑃 𝐸 ∩𝐹 en aan wat kan dit worden gelijkgesteld? Verklaar en licht toe met een concreet voorbeeld.
De wiskundige uitdrukking **P(E ∩ F)** geeft de kans aan dat zowel gebeurtenis **E** als gebeurtenis **F** gelijktijdig plaatsvinden.  

Hoe **P(E ∩ F)** wordt berekend, hangt af van de afhankelijkheid tussen **E** en **F**:  
- **Onafhankelijke gebeurtenissen**:  
  *P(E ∩ F) = P(E) ⋅ P(F)*  
- **Afhankelijke gebeurtenissen**:  
  *P(E ∩ F) = P(E | F) ⋅ P(F)* of *P(F | E) ⋅ P(E)*, waarbij *P(E | F)* de kans is op **E** gegeven **F**.  

Voorbeeld: Spamdetectie  
- **Gebeurtenissen**:  
  - **E** = een e-mail bevat het woord "lottery".  
  - **F** = een e-mail is spam.  
- Gegeven dat 20% van de e-mails spam is (*P(spam) = 0.2*) en 75% van de spammails het woord "lottery" bevat (*P("lottery" | spam) = 0.75*), berekenen we:  

  **P("lottery" ∩ spam) = P("lottery" | spam) ⋅ P(spam) = 0.75 × 0.2 = 0.15**  

- Dit betekent dat in een dataset van 100 e-mails, 15 zowel spam zijn als het woord "lottery" bevatten.  

Dit laat zien hoe afhankelijkheid tussen gebeurtenissen invloed heeft op de kansberekening.
