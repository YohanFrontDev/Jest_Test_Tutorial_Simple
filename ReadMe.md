<!-- Preview = Ctrl + Maj + V on VsCode-->
 <br />
<div align="center">
<image src="./assets/jest_icon.png" style="width:75px"></image>
  <h3 >Cleansheet Jest </h3>
  <p align="center">
    Comprendre comment utiliser Jest de manière conventionnelle.
    <br />
    <br />
    <br />
  </p>
</div>

* #### Mise en place de l'environnement de test.

```bash
# 1:  Installer Jest sur son projet:

- npm add -D jest 

## 2: Créer un fichier de test dans un dossier "test".

- nomFichier.test.js  # Convention de nommage
```

* #### Les méthodes de test.
_Il existe plusieurs méthodes pour tester son code. Dans un premier temps, voyons comment fonctionne les méthodes: ```test()``` et ```describe()```._

* ##### Comment tester une fonction ?
 
```js 
    test('Démo somme', function() {

        const a = 2 + 2 
        expect(a).toBe(4)  # -> attendsLaRéponse(a).QuiDoitÊtre(4) 
    })
```
<!-- Résultats  -->
```bash
# Résultat obtenu lors d'un test réussi :

    Test Suites: 1 passed, 1 total
    Tests:       1 passed, 1 total
    Snapshots:   0 total
    Time:        0.298 s
    Ran all test suites. 
```

_Quand tout se passe bien, c'est parfait ! Mais comment cela se déroule lorsque notre test est incorrect ?  Nous allons voir cela ensemble juste en dessous._
```bash 
    test('Démo somme', function() {

        const a = 2 + 5     ## Nous avons une somme égale à 7.
        expect(a).toBe(4)   ## Nous attendons un résultat égal à 4.
    })
```
_J'ai volontairement inscrit une valeur différente de manière à créer une erreur lors de notre test. Voici maintenant l'affichage dans la console de VSCode lorsqu'un test échoue._
<!-- Résultats  -->
```bash
# Résultat obtenu lors d'un test non réussi :

     FAIL  test/somme.test.js  # Notre test a échoué, Pourquoi ?
  × Démo somme (3 ms)

  ● Démo somme

    expect(received).toBe(expected) // Object.is equality   ## l'objet de notre erreur -> l'égalité.

    Expected: 4 # Nous attendions 4.
    Received: 7 ## Nous avons obtenu 7.

      1 | test('Démo somme', function() {
      2 |     const a = 2 + 5
    > 3 |     expect(a).toBe(4)   ## On nous indique l'endroit de l'erreur.
        |               ^
      4 | })

      at Object.toBe (test/somme.test.js:3:15)

Test Suites: 1 failed, 1 total  ##Résultat de notre test "failed" -> a échoué.
Tests:       1 failed, 1 total
Snapshots:   0 total
Time:        0.335 s, estimated 1 s
Ran all test suites. 
```
_Maintenant que nous avons vu comment déchiffrer un test qui échoue, nous pouvons passer à la deuximème méthode de test qui est la méthode ```describe()```._

* #### À quoi sert la méthode Describe() ?
  
_La méthode describe() va tout simplement nous permettre rassembler plusieurs tests dans une même fonction.  Regardons ensemble ci-dessous comment l'utiliser._

```js
    describe('Pack démo', function() {

        test('Démo somme', function() {
            const a = 2 + 2
            expect(a).toBe(4)
        })

        it('Démo soustraction', function() { 
            const b = 2 - 2
            expect(b).toBe(0)
        })
    })
```
_PS: Il est possible d'utiliser ```"it()"``` à la place de ```test()```._


<!-- Résultats  -->
```bash
# Résultat obtenu :

  PASS  test/somme.test.js
  Pack démo
    √ Démo somme (1 ms) # le test "somme" a fonctionné 
    √ Démo soustraction # le test "soustraction" a fonctionné

Test Suites: 1 passed, 1 total
Tests:       2 passed, 2 total  # nous obtenons bien 2 tests de valides !
Snapshots:   0 total
Time:        0.32 s, estimated 1 s
Ran all test suites.
```
 