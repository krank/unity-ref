# Raycasting\*

## (Camera) ScreenPointToRay()

Skapar en ray som utgår från kamerans position och går "igenom" en viss punkt på skärmen.

```csharp
Ray mouseRay = Camera.main.ScreenPointToRay(Input.mousePosition);
```

## Physics.Raycast()

```csharp
RaycastHit hit;
Physics.Raycast(
  cameraObject.transform.position, 
  cameraObject.transform.forward, 
  out hit, 
  maxInteractionDistance);
```



```csharp
Physics.Raycast(mouseRay, out RaycastHit hit)
```
