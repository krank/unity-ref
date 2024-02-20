# Röststyrning

## Manuella projektinställningar

Kolla under Window → Package Manager så att paketet **MRTK Windows Speech** finns i projektet. Använd annars **Mixed Reality Feature Tool** för att lägga till det.

Gå till **Project Settings**.

Under **MRTK3**, se till så **MRTK Windows KeywordRecognition Subsystem** är ikryssat.

Under **Player**, gå till **Universal Windows Platform settings** och scrolla ner till **Publishing Settings**. Se till så att **Microphone** är ikryssad under Capabilities.

## Känna igen ett kommando

Många av MRTKs knappar och interaktionsobjekt har inbyggda stöd för att markera dem eller aktivera dem med rösten. Med nedanstående går det dock att lägga in egna kommandon.

### XRSubsystemHelpers.GetFirstRunningSubsystem<>()

Returnerar första bästa aktiva subsystem av angiven typ.

```csharp
// Hämtar första bästa KeywordRecognitionSubsystem
KeywordRecognitionSubsystem keywordSystem = XRSubsystemHelpers.GetFirstRunningSubsystem<KeywordRecognitionSubsystem>();
```

### CreateOrGetEventForKeyword()

Metod inuti KeywordRecognitionSubsystems som skapar ett nytt [unity event](../../grundfunktioner/unity-events.md) knutet till ett visst keyword om det inte redan finns en, eller hämtar en referens till det existerande om det redan finns.

```csharp
UnityEvent event = keywordRecognitionSubsystem.CreateOrGetEventForKeyword("cowabunga");
```

### Komplett exempel

```csharp
// Hämta första bästa "keyword recognition subsystem"
KeywordRecognitionSubsystem keywordRecognitionSubsystem = XRSubsystemHelpers.GetFirstRunningSubsystem<KeywordRecognitionSubsystem>();

// Om ett sådant system hittas...
if (keywordRecognitionSubsystem != null)
{
    // Använd systemet för att koppla samman ett kommando med en listener (en metod eller ett Lambda-uttryck)
    keywordRecognitionSubsystem.CreateOrGetEventForKeyword("your keyword").AddListener(() => Debug.Log("Keyword recognized"));
}
```

