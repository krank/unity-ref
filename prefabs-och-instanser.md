# Prefabs och instanser

En **prefab** är ett spelobjekt (med komponenter) som inte finns i en scen utan istället finns i Assets. Prefabs fungerar som mallar för nya objekt.

En prefab skapas genom att ett spelobjekt i scenen dras ner till Assets. Då skapas en prefab av objektet, och i scenen finns nu istället en **instans** av den.

## Instanser

En instans är ett spelobjekt som bygger på och är kopplat till en prefab. När instansen skapas är den först identisk med prefaben. Därefter kan ändringar göras till instansen, som då blir alltmer olik prefaben.

Med andra ord blir prefaben som en mall eller som en [klass](https://krank23.gitbook.io/csharp-ref/klasser-och-objektorientering/klasser-och-instanser).

![](<.gitbook/assets/image (5) (2).png>)

Instanser får en extra rad med knappar högst upp i Inspectorn.

* **Open** gör att prefaben öppnas för redigering.
* **Select** markerar prefaben i Assets.
* Ändringar som görs till en instans kallas **Overrides**. Overrides kan återställas (**revert**) så att de blir lika som prefaben igen, eller så kan prefaben ändras så att samma ändringar görs där (**apply**).
