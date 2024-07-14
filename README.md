# cv-challenge

## Zusaezliche Fragen
1. "Wählen Sie eine geeignete Modellarchitektur und Parameter sowie Metriken zur Bewertung Ihres Modells. Begründen Sie ihre Wahl."
Ich entscheide mich für die Implementierung eines Multi-Regressionsmodells. Im Gegensatz zur Klassifikation wird hierbei ein wertekontinuierlicher Wertebereich vorhergesagt. Beide Zielgrößen (hood, backdoor_left) müssen unabhängig von einander vorhergesagt werden und können nicht mit einer Softmax-Aktivierung (Summe=1) verarbeitet werden.
-> Multioutput-Regression mit 2 Ausgängen

MSE (Mean Squared Error) als Metrik. Falls Konvergenz Probleme auftreten sollten, versuche ich den MAE. (weniger Probleme bei Outlier)


2. "Überlegen Sie sich, ohne dies umzusetzen, wie Sie Ihr Modell weiter optimieren könnten."

3. "Welche weiteren Anwendungsfälle für Deep Learning mit Fahrzeugfotos können Sie sich im Versicherungskontext vorstellen?

## Setup
Create new conda environment using requirements.txt file:
```bash
conda create --name cv-challenge --file requirements.txt
```