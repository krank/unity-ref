# Invoke, Couroutines

## Invoke

Invoke för att man kan köra en metod efter en viss tid. Passar bra när man vill att något ska göras exakt en gång.

Tar emot en string och en float – namnet på metoden som ska köras och hur långt in i framtiden den ska köras.

```csharp
void Start()
{
  Invoke("EndGame", 60);
}

void EndGame()
{
  SceneManager.LoadScene(0);
}
```

## Coroutines

Coroutines är metoder som körs _vid sidan av_ resten av koden. De kan till exempel användas ifall man att något ska ske med jämna mellanrum.

En coroutine-metod behöver ha IEnumerator som returtyp och för att "pausa" körningen av den används "yield return".

Om man yield-returnar null fortsätter metoden köras nästa frame. Annars brukar man ofta yield-returna en new WaitForSeconds() med ett antal sekunder angivna som en float mellan parenteserna.

```csharp
[SerializeField] GameObject enemyPrefab;
[SerializeField] PlayerController player;

void Start()
{
  StartCoroutine(SpawnEnemy());
}

IEnumerator SpawnEnemy()
{
  while(player.IsAlive())
  {
    Instantiate(enemyPrefab);
    yield return new WaitForSeconds(2.5f);
  }
}
```
