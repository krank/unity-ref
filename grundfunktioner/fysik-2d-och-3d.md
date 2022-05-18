# Fysik (2D och 3D)\*

I Unity är det fysikmotorn som sköter gravitation och andra fysikaliska krafter, och hindrar objekt från att clippa in i varandra. Den sköter dessutom andra kollisioner – sådana som inte har med fysikaliska krafter att göra alls, utan där det bara finns anledning att avgöra ifall två objekt överlappar varandra.

Det finns två helt separata fysikmotorer – 2D och 3D. Båda kan finnas med i samma projekt, men de kan inte påverka eller känna av samma objekt.

## Fysikuppdatering

Fysikmotorn uppdaterar normalt inte objektens position varje bildruta, utan har en egen frekvens. Som standard är denna 50 ggr/sekund. Det går att ställa in under **Edit → Project Settings**, och sedan **Time**. Där finns **"Fixed Timestep"**, som normalt är 0.02.

Metoden **FixedUpdate** körs varje fysik-timestep.

```csharp
void FixedUpdate()
{
  Debug.Log("Doing all the physics!");
}
```

## Rigidbody/Rigidbody2D

RigidBody-komponenterna är kärnan i fysikmotorn. Bara objekt med en RigidBody omfattas av fysikmotorns simuleringar. Undantaget är objekt som kolliderar med dem – de påverkas också, om de har rätt sorts collider.

TL,DR: för att ett objekt ska ges **gravitation** etc behöver det en RigidBody. För att en **kollision** ska kunna avläsas med kod (eller märkas av i fysikmotorn) behöver minst ett av de inblandade objekten ha en RigidBody.

### Velocity

Velocity är en property som beskriver objektets nuvarande hastighet – hur mycket dess position förändras över tid. Man bör vara försiktig med att modifiera den direkt.

```csharp
void Update()
{
  RigidBody rigidbody = GetComponent<RigidBody>();
  
  float xMovement = rigidbody.Velocity.x;
}
```

### AddForce()

Används för att applicera ny kraft till en RigidBody, och därmed påverka dess Velocity. Hur mycket velocityn påverkas beror på vilken ForceMode som används och eventuellt på objektets massa.

Unity-enheter fungerar här som meter, och Force-värdet anges i newtons eller newtonsekunder.

```
// Applicera 700 newtons i riktning framåt.
rigidBody.AddForce(Vector3.forward * 700);

// Applicera en impuls av 900 newtonsekunder åt höger
rigidBody.AddForce(Vector3.right * 900, ForceMode.Impulse);
```

* **ForceMode.Impulse:** applicerar en omedelbar mängd kraft (kraften som adderas är per timestep), och tar massan med i beräkningen.
* **ForceMode.Force:** applicerar en mängd kraft per sekund, och tar massan med i beräkningen.
* **ForceMode.VelocityChange:** applicerar en omedelbar mängd kraft (kraften som adderas är per timestep), men struntar i massan.
* **ForceMode.Acceleration:** applicerar en mängd kraft per sekund, men struntar i massan.

[Här är en tråd på Unitys forum](https://answers.unity.com/questions/696068/difference-between-forcemodeforceaccelerationimpul.html) som går igenom den exakta matten, för den som vill läsa mer.

{% hint style="info" %}
**OBS:** För Rigidbody2D-komponenter används ForceMode2D istället för ForceMode.
{% endhint %}

## Fysikuppdatering

## Colliders

* BoxCollider2D
* CapsuleCollider2D

## 2D-metoder

### OnTriggerEnter2D()

### OnCollisionEnter2D()

## 3D-metoder

### OnTriggerEnter()

### OnCollisionEnter2D()

###
