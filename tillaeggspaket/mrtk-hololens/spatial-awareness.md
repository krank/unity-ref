# Spatial awareness\*

* MRTK XR Rig -> Camera Offset
  * Skapa objekt med "ARMeshManager"-komponent
  * Skapa en prefab med ett MeshFilter och rätt material
    * (Exakta mesh:et kommer att ersättas av det som byggs upp)
* Simulering
  * Edit->Project Settings
    * XR Plug-in Management->Windows, Mac & Linux
      * Kryssa i XR Simulation
  * Window->XR->AR Foundation->XR Environment
    * Install sample environments
    * Import sample environments

{% embed url="https://localjoost.github.io/Using-ARMeshManager-for-Spatial-Awareness-with-MRTK3-on-HoloLens-2/" %}

{% embed url="https://localjoost.github.io/MRTK3-StatefulInteractable-gaze,-hover-and-select-events-and-how-to-use-them/" %}

OLD:

* MixedRealityToolkit
  * Spatial Awareness
    * Enable Spatial Awareness System (kräver egen övergripande Configuration Profile)
    * Observers
      * Alla ändringar kräver egen MixedRealitySpatialAwarenessSystemProfile
      * För simulering
        * Lägg till
        * Type: Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver → SpatialObjectMeshObserver
      * Alla ändringar i enskilda observers kräver egna Profiles för varje.
        * Display Settings – Visible / Occlusion
      * Ändra saker i Observers
        * using Microsoft.MixedReality.Toolkit;
        * using Microsoft.MixedReality.Toolkit.SpatialAwareness;&#x20;
        * using Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver;
        * var observers = (CoreServices.SpatialAwarenessSystem as IMixedRealityDataProviderAccess).GetDataProviders();
