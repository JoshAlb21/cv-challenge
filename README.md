# cv-challenge

## Zusaezliche Fragen
1. "Wählen Sie eine geeignete Modellarchitektur und Parameter sowie Metriken zur Bewertung Ihres Modells. Begründen Sie ihre Wahl."
Ich entscheide mich für die Implementierung eines Multi-Regressionsmodells. Im Gegensatz zur Klassifikation wird hierbei ein wertekontinuierlicher Wertebereich vorhergesagt. Beide Zielgrößen (hood, backdoor_left) müssen unabhängig von einander vorhergesagt werden und können nicht mit einer Softmax-Aktivierung (Summe=1) verarbeitet werden. Multioutput-Regression mit 2 Ausgängen. MSE (Mean Squared Error) als Metrik zur Loss-Berechnung. Falls Konvergenz Probleme auftreten sollten, versuche ich den MAE (weniger Probleme bei Outlier). Für die Bewertung der Modellperformance allerdings schaue ich mir verschiedene Metriken an. Besonders die Visualisierung bestimmter Größen ist für mich hilfreich sowohl die Performance zu bewerten als auch Probleme zu erkennen.


2. "Überlegen Sie sich, ohne dies umzusetzen, wie Sie Ihr Modell weiter optimieren könnten."
* Hyperparameter-Suche auf Rechencluster (vorzugsweise Random Search mit plausiblen Parametergrenzen)
* zusätzliche Verbesserungen wie Lernraten Scheduler (Hilft bei Konvergenzproblemen), Augmentierung (Overfitting vermeiden und Modelle mit mehr Parametern trainieren) etc.
* Als Daumenregel geht man davon aus das mehr (qualitative!) Daten zu einer besseren Modellperformance führen, da Deep Learning Modelle datenintensiv sind. Die Vergrößerung des Datensatz würde helfen das Modell weiter zu verbessern
* Die Verwendung von Modellen die bereits auf Datensätzen (eventuell sogar auschließlich) mit Auto-Bildern trainiert wurden könnten wieder verwendet werden. Dabei kann auch lediglich der Head des Modells ausgewechselt werden (für Regression) wenn das Modell davor für andere Anwendungen verwendet wurde (Detection, Segmentierung).
* Es wäre möglich ein Segmentierungsmodell (Annotationen natürlich benötigt) zu trainieren um Vorhersagen mit mehr Informationsgehalt zu geben. D.h. das Modell könnte die hintere linke Autotür pixelgenau markieren. Diese Segmentierung kann dann weiter verwendet werden um dem Kunden beim Hochladen bereits zu sagen: "Nur x% Der Türfläche ist auf dem Bild." "Die Tür ist vollständig abgebildet aber eine starke Spiegelung verhindert die Schadensanalyse"

3. "Welche weiteren Anwendungsfälle für Deep Learning mit Fahrzeugfotos können Sie sich im Versicherungskontext vorstellen?"
* siehe letzter Punkt in Frage 2
* Eine Möglichkeit wäre die Regression der Schadenssumme (z.B. in €) oder falls eine grobe Einschätzung ausreicht eine Klassifikation (<1000€, 1k€< Summe< 5k€ usw.)
* Automatisches Schadensprotokoll und Abgleich mit dem manuell erstellten in der Werkstatt (wird vielleicht etwas reperariert was garnicht kaputt ist?)
* Erkennung von Deep Fakes oder klassisch manipulierten Bildern. (Noch keine Fachwissen in dem Bereich aber denkbar wäre die Verwendung von Videos -> nicht so leicht zu faken und mehr Information)

## Setup
Create new conda environment using requirements.txt file:
```bash
conda create --name cv-challenge --file requirements.txt
```