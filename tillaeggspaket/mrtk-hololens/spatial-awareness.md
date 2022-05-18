# Spatial awareness\*

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
