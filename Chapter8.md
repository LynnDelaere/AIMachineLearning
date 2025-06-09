# Chapter 8: The naive Bayes model

## Het naive Bayes theorema is gebaseerd op prior probability, posterior probability en event.
**Hoe staan deze drie in relatie tot elkaar en geef een concreet voorbeeld?**

- **Prior probability:** 

De initiële kans op een bepaalde uitkomst, voordat er enige informatie over de uitkomst bekend is. Voorbeeld: Wat is de kans dat een mail spam is voordat we weten of het woord 'sale' erin voorkomt?

- **Event:** 

Een gebeurtenis die plaatsvindt en nieuwe informatie oplevert. Voorbeeld: Een mail ontvangen met het woord 'sale' erin.

- **Posterior probability:** 

De uiteindelijke kans die we berekenen nadat we de prior probability hebben gecombineerd met de informatie van het event. Voorbeeld: Wat is de kans dat een mail spam is nadat we weten dat het woord 'sale' erin voorkomt?

![Naive Bayes](./Images/NaiveBayes.png)


**Wat veronderstelt het naive Bayes theorema?**

Het naive Bayes theorema veronderstelt dat de features onafhankelijk zijn van elkaar. Dit betekent dat de aanwezigheid van een bepaalde feature geen invloed heeft op de aanwezigheid van een andere feature. In de context van spamdetectie betekent dit dat de aanwezigheid van het woord 'sale' in een mail geen invloed heeft op de aanwezigheid van het woord 'discount'.

## Toon aan dat P(spam|'sale') = 0.60 als volgende gegevens beschikbaar zijn:
- **de dataset bestaat uit 100 mails**
- **P(spam) = 20/100**
- **6/20 van de spam mails bevat het woord 'sale'**
- **4/80 van de ham mails bevat het woord 'sale’**
- **Wat betekent P(spam|’sale’)?**

P(spam | 'sale') is de kans dat een mail spam is, gegeven dat het woord 'sale' in de mail voorkomt. Dit is een voorbeeld van een posterior probability, omdat we de kans berekenen nadat we informatie hebben over het event (het woord 'sale' in de mail).
Om P(spam | 'sale') te berekenen, gebruiken we het Bayes-theorema:

$$P(spam | 'sale') = \frac{P('sale' | spam) \times P(spam)}{P('sale')}$$

We hebben de volgende gegevens:
- **P(spam) = 20/100 = 0.20** (de kans dat een mail spam is)
- **P(ham) = 80/100 = 0.80** (de kans dat een mail geen spam is)
- **P('sale' | spam) = 6/20 = 0.30** (de kans dat een mail het woord 'sale' bevat, gegeven dat het spam is)
- **P('sale' | ham) = 4/80 = 0.05** (de kans dat een mail het woord 'sale' bevat, gegeven dat het geen spam is)

We hebben P('sale') nodig om de posterior probability te berekenen. We kunnen P('sale') berekenen met de wet van de totale kans:
$$P('sale') = P('sale' | spam) \times P(spam) + P('sale' | ham) \times P(ham)$$
$$P('sale') = (0.30 \times 0.20) + (0.05 \times 0.80)$$
$$P('sale') = 0.06 + 0.04 = 0.10$$

Nu kunnen we P(spam | 'sale') berekenen met het Bayes-theorema:

$$P(spam | 'sale') = \frac{P('sale' | spam) \times P(spam)}{P('sale')}$$
$$P(spam | 'sale') = \frac{0.30 \times 0.20}{0.10}$$
$$P(spam | 'sale') = \frac{0.06}{0.10} = 0.60$$


## Wat omschrijft de ‘rule of complementary probabilities’?
De **rule of complementary probabilities** beschrijft dat voor een gebeurtenis A, de kans op de complementaire gebeurtenis (niet-A) gelijk is aan 1 min de kans op A. Dit kan worden uitgedrukt als:

$$P(A') = 1 - P(A)$$

Bijvoorbeeld, als de kans op regen 0.30 is, dan is de kans op geen regen 0.70.

## Wat is de wiskundige vorm van het Bayes theorem?
Het Bayes-theorema kan worden uitgedrukt als:

$$P(F | E) = \frac{P(E | F) \times P(F)}{P(E)}$$

Waarbij:
- **P(F | E)** de posterior probability is: de kans dat gebeurtenis F plaatsvindt gegeven dat gebeurtenis E heeft plaatsgevonden.
- **P(E | F)** de likelihood is: de kans dat gebeurtenis E plaatsvindt gegeven dat gebeurtenis F heeft plaatsgevonden.
- **P(F)** de prior probability is: de initiële kans op gebeurtenis F voordat er enige informatie over gebeurtenis E bekend is.
- **P(E)** de normaliseringsconstante is: de kans op gebeurtenis E.

## Wat omschrijft de ‘product rule for independent probabilities’?

De **product rule of independent probabilities** omschrijft wat de kans is dat twee onafhankelijke gebeurtenissen tegelijkertijd plaatsvinden. Volgens deze regel is de kans op de intersectie van twee onafhankelijke gebeurtenissen gelijk aan het product van de afzonderlijke kansen van elk van die gebeurtenissen. Dit kan worden uitgedrukt als: 

$$P(E ∩ F) = P(E) × P(F)$$

## Wat betekent de wiskundige uitdrukking 𝑃 (𝐸 ∩ 𝐹) en aan wat kan dit worden gelijkgesteld? Verklaar en licht toe met een concreet voorbeeld.

De wiskundige uitdrukking **P(E ∩ F)** staat voor de kans dat zowel gebeurtenis **E** als gebeurtenis **F** gelijktijdig plaatsvinden. Dit wordt ook wel de kans op de intersectie van de twee gebeurtenissen genoemd.

De waarschrijnlijkheiden kan op verschillende manieren gelijk worden gesteld, afhankelijk van de context en de afhankelijkheid tussen de gebeurtenissen **E** en **F**.
- **Onafhankelijke gebeurtenissen**:  
  In het geval dat **E** en **F** onafhankelijk zijn, kan de kans op de intersectie worden berekend als het product van de individuele kansen:  
  $$P(E ∩ F) = P(E) × P(F)$$

- **Afhankelijke gebeurtenissen**:
  Als **E** en **F** afhankelijk zijn, kan de kans op de intersectie worden berekend met behulp van de voorwaardelijke kans:

  $$P(E ∩ F) = P(E | F) × P(F)$$
  $$of$$
  $$P(E ∩ F) = P(F | E) × P(E)$$

  Hierin is **P(E | F)** de kans op gebeurtenis **E** gegeven dat gebeurtenis **F** heeft plaatsgevonden, en vice versa.

Voorbeeld:
Stel dat we twee gebeurtenissen hebben:
- **E** = een e-mail bevat het woord "lottery".
- **F** = een e-mail is spam.

De kans dat een e-mail spam is, is 20% (*P(spam) = 0.2*), en de kans dat een spam e-mail het woord "lottery" bevat, is 75% (*P("lottery" | spam) = 0.75*). We willen nu de kans berekenen dat een e-mail zowel spam is als het woord "lottery" bevat.
We kunnen dit berekenen met de formule voor afhankelijke gebeurtenissen:
$$P("lottery" ∩ spam) = P("lottery" | spam) × P(spam)$$
In dit geval is dat:
$$P("lottery" ∩ spam) = 0.75 × 0.2 = 0.15$$

Of met de formule voor onafhankelijke gebeurtenissen, als we aannemen dat de kans op het woord "lottery" onafhankelijk is van de spamstatus:
$$P("lottery" ∩ spam) = P("lottery") × P(spam)$$
In dit geval moeten we de kans op het woord "lottery" kennen, laten we zeggen dat deze 10% is (*P("lottery") = 0.1*):
$$P("lottery" ∩ spam) = 0.1 × 0.2 = 0.02$$