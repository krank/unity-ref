# Hitta spelobjekt

{% hint style="info" %}
**OBSERVERA:** Detta bör inte göras mer än nödvändigt – alltså helst inte av många objekt samtidigt och helst inte varje frame. Det är systemmässigt kostsamt!
{% endhint %}

## Find

Find tar emot ett namn som parameter och returnerar det objekt som matchar. Om inget matchar, returneras null.

```
GameObject player = GameObject.Find("Player");
```

## FindWithTag

FindWithTag tar emot namnet på en tag som parameter och returnerar ett objekt som har taggen. Om inget matchar, returneras null.

```
GameObject player = GameObject.FindWithTag("StartPosition");
```

## FindGameObjectsWithTag

FindGameObjectsWithTag är en metod inbyggd i GameObject-klassen, som tar emot namnet på en tag som parameter och returnerar en array med de objekt som har taggen.

```
GameObject[] enemies = GameObject.FindWithTag("Enemy");
```

