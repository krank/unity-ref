# Unity Events\*

Unity Events är en variation på samma designmönster som C# [delegater](https://krank23.gitbook.io/csharp-ref/grundlaeggande/delegates#multicasting-delegat-variabler-med-flera-metoder). En händelse – en "event" – knyts till en eller flera metoder. Så när händelsen aktiveras, så körs alla metoder som kopplats till den.

Skillnaden mellan Events och delegater är att med Events sker anknytningen mellan händelse och metoder i första hand via Unity-editorns gränssnitt snarare än med kod.

Många system i Unity använder Events som ett sätt att bygga logik direkt i editorn. UI-systemet använder till exempel Events för att knyta knapptryck till metodanrop, utan att den som designar gränssnittet behöver skriva någon kod.

## I editorn

![](<../.gitbook/assets/image (5) (1).png>)

Bilden ovan visar tre exempel på UnityEvents som visas i Unity-editorn. Det första eventet har ännu inga metoder kopplade till sig – listan är tom. Listan utökas genom knappen +.

För att koppla en metod till ett Event behövs tre eller fyra bitar information:

* **När** eventet ska vara aktivt – normalt "Runtime only", alltså att eventet bara kan aktiveras när spelet körs.
* **Objektet** som innehåller den komponent vars metod ska anropas.
* **Komponenten** och **metoden** som ska anropas.
* Eventuellt: en **parameter** som skickas in i metoden när den anropas.

Eventet **"Normal Event"** i exemplet anropar metoden **SayHello** på komponenten **Hello**, som i sin tur befinner sig i objektet **TestObject**.

Eventet **"String Event"** anropar istället metoden **SaySomething**, med parametern **"What is Love?"**, på samma komponent (**Hello**) och samma objekt (**TestObject**).

Objektet behöver väljas först, därefter komponenten, metoden och det eventuella parametervärdet.

## UnityEvent

### AddListener()

### Invoke()

### UnityEvent<>
