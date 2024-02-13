# Röststyrning\*

* Mixed Reality Feature Tool
  * MRTK Windows Speech
* Project Settings
  * MRTK → Aktivera keyword recognition
  * Player Settings
    * UWP → Publishing settings → Capabilities

[https://localjoost.github.io/MRTK2-to-MRTK3-simple-global-speech-recognition/](https://localjoost.github.io/MRTK2-to-MRTK3-simple-global-speech-recognition/)

```csharp
// Get the first running phrase recognition subsystem.
var keywordRecognitionSubsystem = XRSubsystemHelpers.GetFirstRunningSubsystem<KeywordRecognitionSubsystem>();

// If we found one...
if (keywordRecognitionSubsystem != null)
{
    // Register a keyword and its associated action with the subsystem
    keywordRecognitionSubsystem.CreateOrGetEventForKeyword("your keyword").AddListener(() => Debug.Log("Keyword recognized"));
}
```
