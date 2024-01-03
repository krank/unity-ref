# CharacterController

CharacterController är en komponent för att hantera spelkaraktärer i 3D-spel. Med en CharacterController behöver karaktären ingen RigidBody eller Collider – istället sköter CharacterControllern kollisioner med hjälp av vad som i princip är en Capsule Collider.

CharacterControllers har ingen automatisk gravitation och påverkas normalt inte heller av andra fysik-krafter.

## Move()

Flytta objektet, ungefär som transform.Translate men arbetar normalt sett i den **globala** rymden, dvs förflyttningen är _inte_ relativt objektets rotation.

```csharp
Vector3 movement = inputVector.x * movementSpeed * transform.right
                     + inputVector.y * movementSpeed * transform.forward;

GetComponent<CharacterController>().Move(movement * Time.deltaTime);
```

## isGrounded

Kolla ifall karaktären står på marken.

{% hint style="info" %}
**OBSERVERA:** Fungerar bara om karaktären flyttade sig, eller försökte flytta sig, föregående frame! Därför är det bra att t.ex. inte nollställa eventuell vertikal hastighet helt…
{% endhint %}

```csharp
if (characterController.isGrounded)
{
  verticalVelocity = -1;
  if (jumpPressed)
  {
    verticalVelocity = jumpForce;
  }
}
```

## velocity

En [Vector3](../grundfunktioner/datatyper-och-synlighet.md#vector3) som är den hastighet karaktären har – eller snarare, _hade_ föregående frame. Kan inte ändras på; är bara ett passivt uträknat värde.

```csharp
if (characterController.velocity.y > 0)
{
  // Hoppar
}
else if (characterController.isGrounded)
{
  // Står på marken
}
else
{
  // Ramlar nedåt
}
```
