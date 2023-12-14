# Animationer\*

* Animator: hanterar vilken animation som ska spelas
* Animator controller: state machine som styr en animator
* Animation clip: en specifik animation

## Skapa animationer

* Window->Animation->Animation
* Skapa clip & addera Animator-komponent
* Animera properties med keyframes

## Kod

### Animator

#### Play()

Spela upp en specifik namngiven animation.

```
GetComponent<Animator>().Play("WalkLeft");
```

#### SetTrigger(), SetBool(), SetFloat(), SetInteger()

#### runtimeAnimatorController

GetCurrentAnimatorClipInfo()

* Get en array

### AnimationClip

* name
* length

### RuntimeAnimatorController

* Klass som beskriver en AnimatorController
* animationClips: read-only array.
  * Kan göras till List och sedan Find:as för att hitta specifikt clip
