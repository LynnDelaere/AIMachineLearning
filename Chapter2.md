# Chapter 2: Types of Machine Learning

## Bespreek de essentiële verschillen tussen:
- **Supervised Machine Learning**

    Supervised Machine Learning werkt met gelabelde data. Dit betekent dat de data die gebruikt wordt om het model te trainen, voorzien is van het juiste label. Het model voorspelt de output op basis van de input en de labels.
- **Unsupervised Machine Learning**

    Unsupervised Machine Learning werkt met ongelabelde data. Dit betekent dat de data die gebruikt wordt om het model te trainen, niet voorzien is van het juiste label. Het model probeert patronen te ontdekken in de data.
- **Reinforcement Learning**

    Reinforcement Learning werkt op basis van feedback. Het model leert door te experimenteren en te leren van de resultaten. Het model probeert een bepaalde taak uit te voeren en krijgt feedback op basis van de resultaten.

## Wat is het verschil tussen een regressie model en een classificatie model?
- **Regressie modellen**

    Regressie modellen worden gebruikt om een continue waarde te voorspellen. Ze proberen de relatie tussen de input features en een continue output te modelleren. Bijvoorbeeld, het voorspellen van de prijs van een huis op basis van kenmerken zoals grootte, locatie en aantal kamers.

- **classificatie modellen**

    Classificatie modellen worden gebruikt om een discrete waarde te voorspellen. Ze proberen de relatie tussen de input features en een discrete output te modelleren. Bijvoorbeeld, het voorspellen of een e-mail spam is of niet op basis van kenmerken zoals de afzender, het onderwerp en de inhoud van de e-mail.

## Wat is het doel van:
- **Clustering algorithm?**

    Het doel van een clustering algorithm is om data te groeperen in clusters op basis van overeenkomsten tussen de data punten. Dit helpt bij het ontdekken van patronen en structuren in de data zonder dat er labels nodig zijn.

- **Dimensionality reduction algorithm?**

    Het doel van een dimensionality reduction algorithm is om de complexiteit van de data te verminderen door het aantal features te verminderen, terwijl de belangrijkste informatie behouden blijft. Dit helpt bij het verbeteren van de prestaties van het model en het verminderen van overfitting.

- **Generative algorithm?**

    Het doel van een generative algorithm is om nieuwe data te genereren die lijkt op de training data. Dit kan worden gebruikt voor taken zoals het genereren van afbeeldingen, tekst of muziek. Generative modellen leren de onderliggende distributie van de data en kunnen nieuwe voorbeelden creëren die passen bij deze distributie.

## Bespreek bondig de techniek van dimensionality reduction bij unsupervised learning? Verklaar wat matrix factorization en singular value decomposition is en waar deze techniek concreet wordt toegepast.

**Dimensionality reduction** is een techniek die wordt gebruikt in unsupervised learning om de complexiteit van data te verminderen door het aantal features te verlagen, terwijl de belangrijkste informatie behouden blijft. 

**Matrix factorization** wordt gebruikt om een grote matrix van data uit te drukken als een product van kleinere matrices. Dit helpt bij het ontdekken van verborgen structuren in de data en wordt vaak toegepast in aanbevelingssystemen.

**Singular value decomposition (SVD)** is een specifieke vorm van matrix factorization die wordt gebruikt om de structuur van een matrix te analyseren. Het decomprimeert een matrix in drie componenten: de linker-singuliere vectoren, de singuliere waarden en de rechter-singuliere vectoren. SVD wordt toegepast in toepassingen zoals beeldcompressie.

## Bespreek het principe van reinforcement Machine Learning?

Reinforcement learning is een type machine learning waarbij geen data wordt gegeven, maar waarbij een computer een taak moet uitvoeren. In plaats van data ontvangt het model een omgeving en een agent die in deze omgeving moet navigeren. De agent heeft een doel of een reeks doelen. De omgeving heeft beloningen en straffen die de agent begeleiden om de juiste beslissingen te nemen om zijn doel te bereiken