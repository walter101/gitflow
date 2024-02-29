### Git - gitflow
Branches
Main
Develop
feaute/bugfix
release/280220241948

### Hoe werkt het?
Git flow bestaat uit twee branches
- main
- develop

De main branch is de release branch.  
De develop branch is de basis voor de feature branches.

### Start repository
- Maak een repository aan in je github account
- Clone de repository met `git clone https://github.com/xxx/repo.git`
- nieuwe develop branch maken `git branch develop`

## Add remote origin
git remote add origin https://github.com/walter101/gitflow.git

## Maak de release branch aan op de repository in github en haal die lokaal op  
- Aanmaken branch in github
- git branch -r (lees de remote branches)  
- git checkout release  

## cherry-pick  
Met cherry-pick kun je een commit uitzoeken

De develop branch wordt op acceptatie deployed
Developer-A heeft feature/A naar develop gemerged (zodat de klant deze code op acceptatie kan testen)  
Developer-B heeft feature/B naar develop gemerged (zodat de klant deze op acceptatie kan testen)  

Developer-C MOET een fatale bug fixen
feature/C wordt ontwikkeld en gemerged naar develop en de klant geeft akkoord  
Nu wil je develop naar Main mergen om de bug te releasen ..  
Dat kan niet omdat daar nog twee features A en B staan die ook lvie gezet zouden worden  

Git checkout main
git cherry-pick hash van de merrge van feature/C in develop  
Nu haal je alleen de commit van feature/C in main op  
Die kun je nu veilig deployen op productie  

### Test scenario  
1. checkout develop
2. Maak file 123.php
3. commit en push naar repository
4. checkout main
5. merge develop in main
6. push main naar repository
7. maak branch feature/a
8. maak file a.php
9. commit en push
10. checkout develop
11. merge feature/a in develop
12. maak branh feature/b
13. maak file b.php
14. commit en push naar repository
15. checkout develop
16. merge feature/b in develop
17. commit en push develop naar repository
18. checkout branch

Nu willen we alleen b.php live zetten
We kunnen niet develop in main mergen
dus moeten we een cherry-pick uitvoeren
We picken de commit(s) warin de file b.php is toegevoegd


*checkout develop en maak een file 123.php en commit en push naar repository*  
* git checkout develop  
* Maak een file 123.php  
* git add 123.php  
* git commit -m "commit 123.php"  

- checkout main en merge develop in main en push naar repository
git checkout main
git merge develop
git push origin main

*feature/456 branch*


Main branch heeft een file 123.php



Ik heb filea.php en file b.php klaar vanuit feature branches in de develop branch    
Hoe kan ik nu zien wat ik zou mergen vanuit  
Als featue/a en feature/b en develop allemaal up-to-date zijn qua commit en push  
Dan kan ik middels een pull request zien wat er van develop naar main zou gaan ..  



[//]: # (<img src="gitflow/assets/images/img.png"/>)
