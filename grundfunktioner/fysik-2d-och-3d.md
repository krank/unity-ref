# Fysik (2D och 3D)\*

I Unity är det fysikmotorn som sköter gravitation och andra fysikaliska krafter, och hindrar objekt från att clippa in i varandra. Den sköter dessutom andra kollisioner – sådana som inte har med fysikaliska krafter att göra alls, utan där det bara finns anledning att avgöra ifall två objekt överlappar varandra.

Det finns två helt separata fysikmotorer – 2D och 3D. Båda kan finnas med i samma projekt, men de kan inte påverka eller känna av samma objekt.

## Rigidbody/Rigidbody2D

RigidBody-komponenterna är kärnan i fysikmotorn. Bara objekt med en RigidBody omfattas av fysikmotorns simuleringar. Undantaget är objekt som kolliderar med dem – de påverkas också, om de har rätt sorts collider.

TL,DR: för att ett objekt ska ges **gravitation** etc behöver det en RigidBody. För att en **kollision** ska kunna avläsas med kod (eller märkas av i fysikmotorn) behöver minst ett av de inblandade objekten ha en RigidBody.

### Velocity

Velocity är en propertobjektets nuvarande hastighet – hur mycket dess position förändras över tid. Man bör vara försiktig med att modifiera den direkt.

```csharp
void Update()
{
  RigidBody rigidbody = GetComponent<RigidBody>();
  
  float xMovement = rigidbody.Velocity.x;
}
```

### AddForce()

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
