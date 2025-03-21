# Chapter 7: Accuracy of machine learning classification models

## Wat bedoelt men met de‘accuracy’ van een ML model? Waarom volstaat ‘accuracy’ niet om een optimaal model te selecteren?
Met de 'accuracy' van een machine learning model wordt de maat waarin het model correcte voorspellingen maakt bedoeld. Het is de verhouding tussen het aantal correcte voorspelde datapunten en het totaal aantal datapunten. De 'accuracy' is echter niet altijd de beste maatstaf om een optimaal model te selecteren, omdat het alle fouten als gelijkwaardig beschouwt. 
In bijvoorbeeld de medische sector is bij een accuracy van 99% niet altijd het beste model, omdat een fout positief resultaat (een ziekte niet detecteren) zwaarder weegt dan een fout negatief resultaat (een gezond persoon als ziek bestempelen). Bij ham/spam classificatie is een fout positief resultaat (een spam mail als ham bestempelen) zwaarder dan een fout negatief resultaat (een ham mail als spam bestempelen).

## Confusionmatrix:
**Wat is een confusion matrix?**
De confusion matrix is een tabel die wordt gebruikt om de prestaties van een classificatiemodel visueel te evalueren. Bij een binair classificatiemodel is dit zeer handig, omdat het de classificatie van de voorspellingen in vier categorieën weergeeft: True Positive (TP), True Negative (TN), False Positive (FP) en False Negative (FN).
**Hoe bepaal je zeer snel het aantal correct en fout geclassificeerde punten?**
Het aantal correct geclassificeerde punten bevind zich op de diagonaal van de confusion matrix, het aantal true positives in de linker bovenhoek en het aantal true negatives in de rechter onderhoek. 
Het aantal fout geclassificeerde punten bevind zich buiten de diagonaal van de confusion matrix, het aantal false positives in de rechter bovenhoek en het aantal false negatives in de linker onderhoek.

## Metrics:
**Wat is de definitie van de parameter ‘recall’ en hoe wordt deze bepaald via de confusion matrix?**
De 'recall' definieert de capaciteit van een model om de positief gelabelde datapunten correct te identificeren. Het wordt berekend als de verhouding tussen het aantal true positives en de som van true positives en false negatives, dus recall = TP / (TP + FN).

**Wat is de definitie van de parameter ‘precision’ en hoe wordt deze bepaald via de confusion matrix?**
De 'precision' definieert de gevallen die het model als positief heeft geclassificeerd en die ook daadwerkelijk positief zijn. Het wordt berekend als de verhouding tussen het aantal true positives en de som van true positives en false positives, dus precision = TP / (TP + FP).

**Wat is de definitie van de parameter ‘specificity’ en hoe wordt deze bepaald via de confusion matrix?**
De 'specificity' definieert de capaciteit van een model om de negatief gelabelde datapunten correct te identificeren. Het wordt berekend als de verhouding tussen het aantal true negatives en de som van true negatives en false positives, dus specificity = TN / (TN + FP).

**Hoe wordt de F-score van een classificatie model?**
De F-score is een maatstaf die de recall en de precisie combineert tot één waarde. De meest gebruikelijke vorm van de F-score is de F1-score, die het harmonisch gemiddelde van de recall en de precisie berekent. De F1-score wordt berekend als $$F_{\beta} = \frac{(1 + \beta^2) \cdot (\text{Precision} \times \text{Recall})}{(\beta^2 \cdot \text{Precision}) + \text{Recall}}$$

Als $\beta = 1$, is de Fb-score gelijk aan de F1-score, waarbij precisie en recall even zwaar wegen.
Als $\beta > 1$, wordt de recall zwaarder gewogen dan de precisie.
Als $\beta < 1$, wordt de precisie zwaarder gewogen dan de recall.


![confusionMatrix](/Images/confusionMatrix.png)

## Wat is de receiver operating characteristic (ROC) en hoe helpt de parameter AUC om de parameters specificity en sensitivity te optimaliseren?
De Receiver Operating Characteristic (ROC) curve is een grafiek die de prestaties van een binair classificatiemodel visualiseert bij verschillende classificatiedrempels. Het is een hulpmiddel om de balans te vinden tussen de sensitiviteit (true positive rate) en de (1 - specificiteit) of false positive rate van het model. De ROC-curve toont de trade-off tussen de sensitiviteit en de specificiteit van het model bij verschillende drempelwaarden.

De Area Under the Curve (AUC) is de oppervlakte onder de ROC-curve. De AUC is een enkele scalaire waarde tussen 0 en 1 die de prestaties van het classificatiemodel samenvat. Hoe hoger de AUC, hoe beter het model presteert. De AUC helpt om de parameters specificiteit en sensitiviteit te optimaliseren door de prestaties van het model te evalueren en te vergelijken met andere modellen.

![ROCcurve](/Images/ROCcurve.png)