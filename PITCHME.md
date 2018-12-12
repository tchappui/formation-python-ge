# Formation Python

---
@snap[span-100]
## Thierry Chappuis, PhD
@snapend

Formateur Python et Professeur à la Haute Ecole d'Ingénierie de Fribourg

**thierry@chappuis.net**

---

@snap[span-100]
## Pourquoi Python est-il si populaire?
@snapend

- La qualité logicielle au centre
- Productivité accrue
- Portabilité
- Ecosystème très très riche
- Interface facile avec des composants externes
- Parce que c'est beau :)


---
@snap[span-100]
## Comment fonctionne un programme Python?
@snapend

![](https://gyazo.com/fad46ca33fe80b68f9e67a4231b8ba64.png)

---

## Performances ?

La bonne question est: est-ce **suffisant** pour ce que je veux?

---

## Variations

- **CPython: la version originale**
- PyPy: optimisée pour la vitesse
- IronPython: pour .Net
- Jython: pour la machine virtuelle Java
- Stackless: pour la concurrence

---

## Optimisation

- Cython
- Numba

---

## Comment exécuter vos premiers programmes Python ?

---

### Utiliser une invite de commande interactive

![](https://gyazo.com/7b11a332b107f67bdce747a0a29919f9.png)

---

@snap[north]
#### Sous Windows
@snapend

Exécutez la commande python dans un terminal:

- **Anaconda prompt** (si utilisation de anaconda)
- cmd.exe
- Powershell
- Idle

---
### Votre éditeur préféré vous donne accès à un terminal

![](https://i.gyazo.com/5c83d549925d98dac739b6bd5b5062a2.png)

--- 
## Exécuter un fichier Python depuis un terminal

```console
$ python monfichier.py
```

---

## Isoler vos dépendences dans un environnement virtuel

Sur windows (dans un terminal):

```console
$ python -m venv env
$ env\scripts\activate
(env) $
```
Sur les autres systèmes:

```console
$ python3 -m venv env
$ source env/bin/activate
(env) $
```

---

## Se simplifier la vie avec pipenv

```console
$ pip install pipenv
```

```console
$ pipenv install requests django gunicorn
$ pipenv shell
```

---

## Expérimentons depuis un interpréteur interactif

---

```python
>>> from pathlib import Path
```

```python
>>> p = Path('.')
>>> p
>>> list(p.glob('**/*.pdf'))
```

---
## Instructions sur plusieurs lignes

```python
>>> for x in 'Bonjour':
...     print(x) 
...
```
---

## Un premier script

```python
import sys            # importe un module de la bib standard
print(sys.platform)
print(2 ** 100)       # élève 2 à la puissance de 100
x = 'Spam!'
print(x * 8)          # répète une chaine 8 fois
```

```console
$ python premierscript.py
win32
1267650600228229401496703205376
Spam!Spam!Spam!Spam!Spam!Spam!Spam!Spam!
```

```console
$ python premierscript.py > saveit.txt
```

```console
$ py -3 premierscript.py
```

---

## Le shebang et l'encodage

```python
#!/usr/bin/env python
#-*- coding: utf8

...le reste du script vient ici...
```
---

## Importer et recharger

```python
>>> import premierscript
win32
1267650600228229401496703205376
Spam!Spam!Spam!Spam!Spam!Spam!Spam!Spam!
```

```python
...Changez premierscript dans un éditeur et tentez de ré-importer...
>>> import script1
>>> import script1
```

---

## reload() pour ce genre de situation

```python
>>> from imp import reload
>>> reload(premierscript)
win32
65536
Spam!Spam!Spam!Spam!Spam!Spam!Spam!Spam!
??? from here until ???END lines may have been inserted/deleted
<module 'script1' from '.\\script1.py'>
>>>
```
---

## Première introduction aux modules

```python
$  python
>>> import myfile
>>> myfile.title 
'The Meaning of Life'
```

```python
$  python
>>> from myfile import title
>>> title 
'The Meaning of Life'
```

---?color=#E58537

## Les modules sont des espaces de noms

---

## Types et opérations

---

## Les types numériques: la boite à outils

- Entier et nombres à virgule flottante
- Nombres complexes
- Decimal: nombres à précision fixe
- Fraction: nombres rationnels
- Sets: opérations sur des ensembles
- Booléens: True et False
- Fonctions intégrées: math, random
- Expressions: entier à précision infinie, opérations sur les bits, hex, octal, binaire
- Vecteurs, visualisation
