# Knappar och axlar

Det finns ett antal fördefinierade axlar (Edit->Project Settings->Input).

En axel kan ha ett positivt och negativt värde, från -1 till +1 där 0 är "neutralt".

Varje axel kan sedan ha knappar som ändrar dess värde. Så för axeln "Horizontal" används vänsterpil och a för att ge den värdet -1, och högerpil eller d används för att ge den värdet +1.

I scripts kan man sedan [läsa av axlarnas nuvarande värde](../grundfunktioner/input/#input-getaxisraw).

Det här gör att man som spelskapare inte själv behöver anpassa sitt spel till både handkontroll och tangentbord, utan det sköts på ett centralt ställe av Unity.

Man kan skapa egna axlar och man kan ändra knapparna för de som finns.

Några axlar som finns:

* `Horizontal` (vänster/högerpil eller a/d)
* `Vertical` (upp/nerpil eller w/s)
* `Jump` (mellanslag)
* `Fire1` (vänster Ctrl)
