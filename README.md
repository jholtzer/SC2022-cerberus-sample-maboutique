# Implémenter le Continuous Testing

Ce projet sert de support à l'atelier ***Implémenter le Continuous Testing***

\
&nbsp;

Plan : 
- [ETAPE 1 : FORK le projet cerberustesting/cerberus-sample-maboutique](https://github.com/cerberustesting/cerberus-sample-maboutique#etape-1--fork-le-projet-cerberustestingcerberus-sample-maboutique).
- [ETAPE 2 : Ajout d'une Github Actions Qualité de code](https://github.com/cerberustesting/cerberus-sample-maboutique#etape-2--ajout-dune-github-actions-qualit%C3%A9-de-code).
- [ETAPE 3 : Ajout des tests automatiques dans la CI](https://github.com/cerberustesting/cerberus-sample-maboutique#etape-3--ajout-des-tests-automatiques-dans-la-ci).



\
&nbsp;

Utiliser chrome ou firefox de préférence

- Url : <a href="https://jftl.cerberus-testing.fr" target="_blank">https://jftl.cerberus-testing.fr</a>

Read/Write pour ceux qui veulent pratiquer en live :)
- User : admin
- Pass : admin

\
&nbsp;

## ETAPE 1 : FORK le projet cerberustesting/cerberus-sample-maboutique
1. Depuis le projet github https://github.com/cerberustesting/cerberus-sample-maboutique, fork l’application sur votre repository perso


\
&nbsp;

<img width="766" alt="Capture d’écran 2022-06-11 à 00 22 09" src="https://user-images.githubusercontent.com/5376184/173158111-dd7de72e-fb0b-40c6-bfdb-c0db1aa3261e.png">

\
&nbsp;

2. Valider la creation du fork

\
&nbsp;

<img width="378" alt="Capture d’écran 2022-06-11 à 00 23 40" src="https://user-images.githubusercontent.com/5376184/173158234-68f72a2d-0130-43be-86c7-8a790113669c.png">

\
&nbsp;

Vous devriez être redirigé sur votre fork (Cf. ci dessous)

\
&nbsp;

<img width="758" alt="Capture d’écran 2022-06-11 à 00 35 05" src="https://user-images.githubusercontent.com/5376184/173159047-5136bc6b-58e5-4fbd-94b3-aba35671f274.png">

\
&nbsp;

Dans l'onglet Actions, activer les workflows

\
&nbsp;

<img width="557" alt="Capture d’écran 2022-06-27 à 22 33 04" src="https://user-images.githubusercontent.com/5376184/176030655-6f8270c8-4f3f-4986-9e11-e4c86d4034cd.png">

\
&nbsp;
---

## ETAPE 2 : Ajout d'une Github Actions Qualité de code

1. Aller sur la page https://sonarcloud.io/

2. Choisir de parser un nouveau projet github

\
&nbsp;

<img width="320" alt="Capture d’écran 2022-06-12 à 09 37 10" src="https://user-images.githubusercontent.com/5376184/173222554-58f36ff0-bf29-41f5-a587-a0840aa8d3e0.png">

\
&nbsp;

3. Cliquer sur + (ajouter un nouveau repository)

\
&nbsp; 

<img width="416" alt="Capture d’écran 2022-06-12 à 09 39 18" src="https://user-images.githubusercontent.com/5376184/173222632-4be3aa0d-e614-4c57-a107-fd997718d0f5.png">

\
&nbsp;

4. Choisir une organisation, choisir votre organisation perso, cliquer sur only select repository, choisir le projet "ma boutique" et cliquer sur install

\
&nbsp;

<img width="457" alt="Capture d’écran 2022-06-12 à 09 40 25" src="https://user-images.githubusercontent.com/5376184/173222660-48a0df75-8dbd-469f-a6f1-87550855550f.png">
<img width="408" alt="Capture d’écran 2022-06-12 à 09 40 57" src="https://user-images.githubusercontent.com/5376184/173222668-3e57b9eb-a8a0-4a40-b184-d9fcc6389011.png">
<img width="364" alt="Capture d’écran 2022-06-12 à 09 42 08" src="https://user-images.githubusercontent.com/5376184/173222704-d30d3892-ef93-486e-a516-9160415cbb8a.png">

\
&nbsp;

5.Créer une organisation

\
&nbsp;

<img width="798" alt="Capture d’écran 2022-06-12 à 09 43 25" src="https://user-images.githubusercontent.com/5376184/173222744-d36a1eeb-1b0d-4bc1-9098-90d07b8dd793.png">

\
&nbsp;

6. Choisir Free plan

\
&nbsp;

<img width="776" alt="Capture d’écran 2022-06-12 à 09 43 53" src="https://user-images.githubusercontent.com/5376184/173222761-7b8175b2-5f37-477b-9b34-dd1e992356ce.png">

\
&nbsp;

7. Selectionner et cliquer sur setup

\
&nbsp;

<img width="797" alt="Capture d’écran 2022-06-12 à 09 44 34" src="https://user-images.githubusercontent.com/5376184/173222775-90676be0-a2d0-4186-94cb-8b8c42ad7761.png">

\
&nbsp;

8. Dans Sonar, vous arrivez sur cette page

\
&nbsp;

<img width="512" alt="Capture d’écran 2022-06-27 à 22 39 03" src="https://user-images.githubusercontent.com/5376184/176031593-186c4968-547b-4089-bc23-cf5a8d494c32.png">

\
&nbsp;


### Configurer 
1. Cliquer sur With Github Actions

\
&nbsp;

2. Copier le Token SONAR_TOKEN
<img width="1066" alt="Capture d’écran 2022-06-12 à 20 58 26" src="https://user-images.githubusercontent.com/5376184/173249610-40b888cf-093d-440c-9e1c-f5612807d738.png">

\
&nbsp;

3. Choisir Other, et copier la configuration
<img width="1032" alt="Capture d’écran 2022-06-12 à 21 02 13" src="https://user-images.githubusercontent.com/5376184/173249665-6bd5d406-ecaf-46f1-89c4-cbc91c3341dd.png">

\
&nbsp;

```
sonarcloud:
    needs: build
    name: SonarCloud
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
        with:
          fetch-depth: 0  # Shallow clones should be disabled for a better relevancy of analysis
      - name: SonarCloud Scan
        uses: SonarSource/sonarcloud-github-action@master
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}  # Needed to get PR information, if any
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
```

\
&nbsp;

4. Copier les propriétés 
```
sonar.projectKey
sonar.organization
```

\
&nbsp;

<img width="736" alt="Capture d’écran 2022-06-12 à 21 19 45" src="https://user-images.githubusercontent.com/5376184/173249760-924a6856-3aa3-4567-81bf-d95765d23a24.png">


\
&nbsp;

## Configurer votre projet Github

\
&nbsp;

1. Dand Github, aller dans Settings > Secrets > Actions

\
&nbsp;

2. Cliquer sur New repository secret

\
&nbsp;

<img width="789" alt="Capture d’écran 2022-06-12 à 21 32 35" src="https://user-images.githubusercontent.com/5376184/173250157-ce5b9e25-3cf9-4acb-85e6-a6641128c7e0.png">

\
&nbsp;

- Name : SONAR_TOKEN
- Value : Le token sauvegardé

\
&nbsp;

3. Executer manuellement l'action Code Quality pour vérifier la bonne intégration

\
&nbsp;

<img width="740" alt="Capture d’écran 2022-06-27 à 22 48 27" src="https://user-images.githubusercontent.com/5376184/176032996-19bae884-62cc-474d-adf6-f702677eb05b.png">

\
&nbsp;

Dans Sonar Cloud, vous obtenez une première analyse neutre car aucune Quality Gate n'est configuré

\
&nbsp;

<img width="567" alt="Capture d’écran 2022-06-27 à 22 49 55" src="https://user-images.githubusercontent.com/5376184/176033196-b4cef4de-b74c-4bbd-b4b8-77f9c1273e69.png">

\
&nbsp;

Cliquez sur Set New Code Definition et choisir Previous Version

\
&nbsp;

<img width="573" alt="Capture d’écran 2022-06-27 à 22 51 14" src="https://user-images.githubusercontent.com/5376184/176033402-092714e4-e80b-4a78-9cac-9910bc6e3cbc.png">

\
&nbsp;

Depuis la page Actions, relancer une analyse. Dans Sonar, vérifier le résultat :

\
&nbsp;

<img width="749" alt="Capture d’écran 2022-06-12 à 11 17 34" src="https://user-images.githubusercontent.com/5376184/173226381-1dc7a317-62ab-41de-bcd7-bc04606307fe.png">

\
&nbsp;

## Lancer un changement pour tester la Quality Gate

\
&nbsp;

Créer un nouveau fichier 

\
&nbsp;

<img width="914" alt="Capture d’écran 2022-06-12 à 21 53 23" src="https://user-images.githubusercontent.com/5376184/173250771-a4b19e57-b648-4b79-bff4-0b309f094ddc.png">

\
&nbsp;

Nommez le Newfile.js et renseigner le contenu suivant

\
&nbsp;

```
var names = ["Mike","Matt","Nancy","Adam","Jenny","Nancy","Carl"];
var uniqueNames = [];
$.each(names, function(i, el){
    if($.inArray(el, uniqueNames) === -1) uniqueNames.push(el);
});
```

\
&nbsp;

<img width="1217" alt="Capture d’écran 2022-06-12 à 21 55 49" src="https://user-images.githubusercontent.com/5376184/173251082-5f57b582-2f0f-456f-aaa1-d3cc5ace40cf.png">

\
&nbsp;

Commit New File

\
&nbsp;

<img width="1229" alt="Capture d’écran 2022-06-12 à 21 56 05" src="https://user-images.githubusercontent.com/5376184/173251088-a3031c28-b36b-4a76-9d8c-b9b86799e3a1.png">

\
&nbsp;

Depuis la page Actions, vérifier l'execution de la CI. Vous devriez avoir un KO sur la scan Sonarcloud

\
&nbsp;

<img width="1408" alt="Capture d’écran 2022-06-12 à 21 58 30" src="https://user-images.githubusercontent.com/5376184/173251149-24afcf18-5b41-40b9-ae0c-08adb15f9a33.png">

\
&nbsp;

Dans Sonarcloud, vérifier la status

\
&nbsp;

<img width="1066" alt="Capture d’écran 2022-06-12 à 11 23 12" src="https://user-images.githubusercontent.com/5376184/173226663-faa3345c-37ab-4ca2-8c91-d6ec1bd1a0ae.png">

\
&nbsp;

cliquer sur "See full Analysis"

\
&nbsp;

<img width="1060" alt="Capture d’écran 2022-06-12 à 11 36 28" src="https://user-images.githubusercontent.com/5376184/173227111-ab74afba-0bab-4ea9-ab60-b61436f7014d.png">

\
&nbsp;

Cliquer sur A rating required

\
&nbsp;

Analyser les changements à appliquer

\
&nbsp;

<img width="1002" alt="Capture d’écran 2022-06-12 à 11 37 14" src="https://user-images.githubusercontent.com/5376184/173227139-e1c22d3c-0217-4ffe-8394-4b389a7dddf6.png">

\
&nbsp;

Dans github, modifier le fichier 

\
&nbsp;

```
let names = ["Mike","Matt","Nancy","Adam","Jenny","Nancy","Carl"];
let uniqueNames = [];
$.each(names, function(_i, el){
    if($.inArray(el, uniqueNames) === -1) uniqueNames.push(el);
});
```

\
&nbsp;

Commit, relancer une execution de l'action Code Analysis et vérifier la correction des erreurs

\
&nbsp;

<img width="1050" alt="Capture d’écran 2022-06-12 à 11 40 48" src="https://user-images.githubusercontent.com/5376184/173227263-86ee8590-3503-4c9f-89c5-9880361cd532.png">

## ETAPE 3 : Ajout des tests automatiques dans la CI

\
&nbsp;

1. Dans Github aller sur la page Settings > Secrets > Actions

\
&nbsp;
<img width="1228" alt="Capture d’écran 2022-06-13 à 11 26 41" src="https://user-images.githubusercontent.com/5376184/173323238-0919b466-c112-460a-b978-71b25c323b3c.png">

\
&nbsp;

2. Ajouter un nouveau "Repository Secret" 

\
&nbsp;

- Name : APIKEY
- Value : l'APIKEY réupéré dans [Cerberus > Administration > Parameters](https://jftl.cerberus-testing.fr/ParameterList.jsp). 

\
&nbsp;

<img width="1063" alt="Capture d’écran 2022-06-13 à 11 22 26" src="https://user-images.githubusercontent.com/5376184/173323827-228b13d5-db82-4109-a143-4cca19af6d2a.png">

\
&nbsp;

3. Aller sur l'onglet Action

\
&nbsp;

<img width="394" alt="Capture d’écran 2022-06-12 à 18 31 54" src="https://user-images.githubusercontent.com/5376184/173243328-08fad5c0-5e81-4652-a1ba-9cfd69c5e097.png">

\
&nbsp;

4. Cliquer sur Full_CI_to_complete.yml

\
&nbsp;

<img width="482" alt="Capture d’écran 2022-06-12 à 22 03 23" src="https://user-images.githubusercontent.com/5376184/173251289-bf5ebbcb-4eb7-46ce-99e2-3842cf5ebad1.png">

\&nbsp;

5. Cliquer sur edit et ajouter la configuration ci dessous

\
&nbsp;

```
  run_Tests_UAT:
    needs: sonarcloud
    name: Run_Tests_UAT
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: cerberus-action
      uses: cerberustesting/cerberus-github-action@v6
      with:
        host: https://jftl.cerberus-testing.fr
        campaign: SanityCheck
        apikey: ${{ secrets.APIKEY }}
        author: ${{ github.event.pusher.name }}
        environment: UAT
        tag: ${TAG}
```

\
&nbsp;

Vous obtenez ce resultat

\
&nbsp;

<img width="1237" alt="Capture d’écran 2022-06-12 à 22 11 05" src="https://user-images.githubusercontent.com/5376184/173251555-e01c730b-c1a4-4d9f-b36e-8a1fca9f5207.png">

\
&nbsp;

Commit ce changement. Et vérifier la bonne execution de la CI

\
&nbsp;

<img width="1403" alt="Capture d’écran 2022-06-12 à 22 16 12" src="https://user-images.githubusercontent.com/5376184/173251753-a3b29fcf-2edf-4ea6-82d8-c256ce9fb47b.png">



