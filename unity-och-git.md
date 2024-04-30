# Unity och git

Unityprojekt fungerar egentligen precis som vanliga C#projekt. Öppnas de i Visual Studio Code kan man alltså använda [samma steg](https://app.gitbook.com/s/-MHmNgpRz-b16wpwGwZI-887967055/mjukvara/git-and-github).

**En gång:**

* Ha Visual Studio Code installerat.
* Ha [Git installerat](https://app.gitbook.com/s/-MHmNgpRz-b16wpwGwZI-887967055/mjukvara/git-and-github).
* Ställ in [användarnamn och e-mail](https://app.gitbook.com/s/-MHmNgpRz-b16wpwGwZI-887967055/mjukvara/git-and-github#foersta-gangen-efter-ny-git-installation).
* Lägg in tillägget [gitignore ](https://marketplace.visualstudio.com/items?itemName=codezombiech.gitignore)till Visual Studio.

**En gång per projekt:**

* Gå till projektet i Visual Studio Code, öppna kommando-palletten (F1 eller Fn+F1) och sök "add gitignore". Välj "Unity".
* Gå till Source Control och väl Initialize Repository.
* Publicera projektet på Github.

**En gång per arbetstillfälle:**

* Gå till projektet i Visual Studio Code.
* Gå till Source Control.
* Skriv något i rutan för Message.
* Trryck på plusset till höger om "Changes" för att lägga till alla nya ändringar till din commit.
* Tryck på Commit, och sedan Sync.

**För projekt med stora filer (>100mb)**

* Gå till projektet i Visual Studio Code.
* Gå till terminalen
* Skriv in kommandot `git lfs install` för att aktivera Git LFS (Large File System)
* Skriv därefter in `git lfs track '*.fbx'` för att göra så att LFS sköter alla FBX-filer. Gör motsvarande för andra stora filtyper.
