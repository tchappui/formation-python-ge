# Formation Python

---
@snap[span-100]
## Thierry Chappuis, PhD
@snapend

Formateur Python et Professeur à la Haute Ecole d'Ingénierie de Fribourg

**thierry@chappuis.net**

---

## Module 1

Fondamentaux du langages

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

## Que peut-on faire?

- Programmation système avec la bibliothèque standard
- Interfaces graphiques avec Tkinter ou Qt
- Programmation web avec Flask ou Django
- Programmation réseau avec Twisted, ZeroMQ, Sockets
- Calculs scientifiques et data science

---

## Automatiser tout ce qui est ennuyeux

![](https://automatetheboringstuff.com/images/automate_cover_medium.png)

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

## Les Jupyter Notebooks: outils parfait pour explorer les possibilités de Python

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

---

```python
4, −24, 0, 99999999999999   # Entiers (espace illimité)
```

```python
1.23, 1., 3.14e-10, 4E210, 4.0e+210  # Floats
```

```python
0o177, 0x9ff, 0b101010  # Bases 8, 16, 2
```

```python
3+4j, 3.0+4.0j, 3J  # Nombres complexes
```

```python
Decimal('1.0'), Fraction(1, 3)
```

---

## Les outils

```python
+, -, *, /, >>, **, %, &  # Opérateurs
```

```python
random, math  # modules utilitaires
```

```python
# Fonctions intégrées
pow, abs, round, int, hex, bin
w, abs, round, int, hex, bin
```

---

## Les nombres en action

```
>>> a = 3             # Variable crée 
>>> b = 4
>>> a + 1, a − 1      # Addition (3 + 1), soustraction (3 − 1)
(4, 2)
>>> b * 3, b / 2      # Multiplication (4 * 3), division 
(12, 2.0)
>>> a % 2, b ** 2     # Modulo (reste), puissance (4 ** 2)
(1, 16)
>>> 2 + 4.0, 2.0 ** b  # Conversions
(6.0, 16.0)

```
---

## Les messages d'erreurs

```python
>>> c * 2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  NameError: name 'c' is not defined
```

---

## La précédence

```python
>>> b / 2 + a        # même chose que ((4 / 2) + 3) 
5.0
>>> b / (2.0 + a)    # même chose que (4 / (2.0 + 3))
0.8
```

---

## Les comparaisons

```python
>>> 1 < 2                  # Less than
True
>>> 2.0 >= 1               # Greater than or equal: mixed-type 1 converted to 1.0
True
>>> 2.0 == 2.0             # Equal value
True
>>> 2.0 != 2.0             # Not equal value
False
```
---

## Chainer des comparaisons

```python
>>> X = 2
>>> Y = 4
>>> Z = 6

>>> X < Y < Z           # Chained comparisons: range tests
True
>>> X < Y and Y < Z
True
```

---

```python
>>> X < Y > Z
False
>>> X < Y and Y > Z
False
>>> 1 < 2 < 3.0 < 4
True
>>> 1 > 2 > 3.0 > 4
False
```

```python
>>> 1 == 2 < 3        # Same as: 1 == 2 and 2 < 3
False                 # Not same as: False < 3 (which means 0 < 3, which is true!)
```
---

## La division classique et la division entière

```python
>>> 10 / 4         # Differs in 3.X: keeps remainder
2.5
>>> 10 / 4.0       # Same in 3.X: keeps remainder
2.5
>>> 10 // 4        # Same in 3.X: truncates remainder
2
>>> 10 // 4.0      # Same in 3.X: truncates to floor
2.0
```
---
# Précision des entiers

```python
>>> 2 ** 200
1606938044258990275541962092341162602522202993782792835301376
```

---
## Dans différentes bases

```python
>>> 0o1, 0o20, 0o377         # Octal literals: base 8, digits 0-7 (3.X, 2.6+)
(1, 16, 255)
>>> 0x01, 0x10, 0xFF         # Hex literals: base 16, digits 0-9/A-F (3.X, 2.X)
(1, 16, 255)
>>> 0b1, 0b10000, 0b11111111 # Binary literals: base 2, digits 0-1 (3.X, 2.6+)
(1, 16, 255)
```
---
## Decimal, Fraction

```python
>>> 1 / 3                           # Floating-point (add a .0 in Python 2.X)
0.3333333333333333
>>> (2/3) + (1/2)
1.1666666666666665

>>> import decimal                  # Decimals: fixed precision
>>> d = decimal.Decimal('3.141')
>>> d + 1
Decimal('4.141')

>>> decimal.getcontext().prec = 2
>>> decimal.Decimal('1.00') / decimal.Decimal('3.00')
Decimal('0.33')

>>> from fractions import Fraction  # Fractions: numerator+denominator
>>> f = Fraction(2, 3)
>>> f + 1
Fraction(5, 3)
>>> f + Fraction(1, 2)
Fraction(7, 6)
```
---

## Les chaines de caractères

```python
>>> S = 'Spam'     # Make a 4-character string, and assign it to a name
>>> len(S)         # Length
4
>>> S[0]           # The first item in S, indexing by zero-based position
'S'
>>> S[1]           # The second item from the left
'p'

>>> S[-1]          # The last item from the end in S
'm'
>>> S[-2]          # The second-to-last item from the end
'a'
```

---

## Découper une chaine avec les slices

```python
>>> S[1:]           # Everything past the first (1:len(S))
'pam'
>>> S               # S itself hasn't changed
'Spam'
>>> S[0:3]          # Everything but the last
'Spa'
>>> S[:3]           # Same as S[0:3]
'Spa'
>>> S[:-1]          # Everything but the last again, but simpler (0:-1)
'Spa'
>>> S[:]            # All of S as a top-level copy (0:len(S))
'Spam'
```
---

## Concaténer et répéter une chaine

```python

'Spam'
>>> S + 'xyz'             # Concatenation
'Spamxyz'
>>> S                     # S is unchanged
'Spam'
>>> S * 8                 # Repetition
'SpamSpamSpamSpamSpamSpamSpamSpam'
```

---?color=#E58537

## Attention! Les chaines ne sont pas mutables

```python

'Spam'

>>> S[0] = 'z'             # Immutable objects cannot be changed
...error text omitted...
TypeError: 'str' object does not support item assignment

>>> S = 'z' + S[1:]        # But we can run expressions to make new objects
>>> S
'zpam'
```

---

## Une chaine peut être convertie en liste

```python
>>> S = 'shrubbery'
>>> L = list(S)                                     # Expand to a list: [...]
>>> L
['s', 'h', 'r', 'u', 'b', 'b', 'e', 'r', 'y']
>>> L[1] = 'c'                                      # Change it in place
>>> ''.join(L)                                      # Join with empty delimiter
'scrubbery'
```
---

## Nombreuses opérations sur les chaines

```python
>>> line = 'aaa,bbb,ccccc,dd'
>>> line.split(',')              # Split on a delimiter into a list of substrings
['aaa', 'bbb', 'ccccc', 'dd']

>>> S = 'spam'
>>> S.upper()                    # Upper- and lowercase conversions
'SPAM'
>>> S.isalpha()                  # Content tests: isalpha, isdigit, etc.
True

>>> line = 'aaa,bbb,ccccc,dd\n'
>>> line.rstrip()                # Remove whitespace characters on the right side
'aaa,bbb,ccccc,dd'
>>> line.rstrip().split(',')     # Combine two operations
['aaa', 'bbb', 'ccccc', 'dd']
```
---
## Formater des chaines à la volée

```python
>>> '%s, eggs, and %s' % ('spam', 'SPAM!')          # Formatting expression (all)
'spam, eggs, and SPAM!'

>>> '{0}, eggs, and {1}'.format('spam', 'SPAM!')    # Formatting method (2.6+, 3.0+)
'spam, eggs, and SPAM!'

>>> '{}, eggs, and {}'.format('spam', 'SPAM!')      # Numbers optional (2.7+, 3.1+)
'spam, eggs, and SPAM!'
```

```python
>>> '{:,.2f}'.format(296999.2567)                   # Separators, decimal digits
'296,999.26'
>>> '%.2f | %+05d' % (3.14159, −42)                 # Digits, padding, signs
'3.14 | −0042'
```
---

## Obtenir de l'aide

Les fontions dir() et help():

```python
>>> help(S.replace)
Help on built-in function replace:

replace(...)
    S.replace(old, new[, count]) -> str
    
        Return a copy of S with all occurrences of substring
        old replaced by new.  If the optional argument count is
        given, only the first count occurrences are replaced.
```
---
## La puissance des expressions rationnelles

```python
>>> import re
>>> m = re.match('Hello[ \t]*(.*)world', 'Hello  Python world')
>>> m.group(1)
'Python '
```

---

## Les listes

Les actions sur les séquences sont valables:

```python
>>> L = [123, 'spam', 1.23] # A list of three different-type objects
>>> len(L)          # Number of items in the list
3
>>> L[0]            # Indexing by position
123
>>> L[:-1]          # Slicing a list returns a new list
[123, 'spam']

>>> L + [4, 5, 6]   # Concat/repeat make new lists too
[123, 'spam', 1.23, 4, 5, 6]
>>> L * 2
[123, 'spam', 1.23, 123, 'spam', 1.23]

>>> L               # We're not changing the original list
[123, 'spam', 1.23]
```
---

## Quelques actions spécifiques

```python
>>> L.append('NI')     # Growing: add object at end of list
>>> L
[123, 'spam', 1.23, 'NI']

>>> L.pop(2)            # Shrinking: delete an item in the middle
1.23
>>> L                   # "del L[2]" deletes from a list too
[123, 'spam', 'NI']
```

```python
>>> M = ['bb', 'aa', 'cc']
>>> M.sort()
>>> M
['aa', 'bb', 'cc']
>>> M.reverse()
>>> M
['cc', 'bb', 'aa']
```

---

## Vérification des limites

```python

>>> L
[123, 'spam', 'NI']

>>> L[99]
...error text omitted...
IndexError: list index out of range

>>> L[99] = 1
...error text omitted...
IndexError: list assignment index out of range
```
---

## Imbriquer des listes

```python
>>> M = [[1, 2, 3],  # A 3 × 3 matrix, as nested lists
         [4, 5, 6],  # Code can span lines if bracketed
         [7, 8, 9]]
>>> M
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]

>>> M[1]      # Get row 2
[4, 5, 6]

>>> M[1][2]   # Get row 2, then get item 3 within the row
6
```
---

## Les compréhensions

```python
w[1] for row in M] # Collect the items in column 2
>>> col2
[2, 5, 8]

>>> M               # The matrix is unchanged
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]

>>> [row[1] + 1 for row in M]                 # Add 1 to each item in column 2
[3, 6, 9]

>>> [row[1] for row in M if row[1] % 2 == 0]  # Filter out odd items
[2, 8]
```
---

```python
>>> list(range(4))           # 0..3 (list() required in 3.X)
[0, 1, 2, 3]
>>> list(range(−6, 7, 2))    # −6 to +6 by 2 (need list() in 3.X)
[−6, −4, −2, 0, 2, 4, 6]

>>> [[x ** 2, x ** 3] for x in range(4)] # Multiple values, "if" filters
[[0, 0], [1, 1], [4, 8], [9, 27]]
>>> [[x, x / 2, x * 2] for x in range(−6, 7, 2) if x > 0]
[[2, 1, 4], [4, 2, 8], [6, 3, 12]]
```
---

## Les générateurs

Un outils d'optimisation

```python
>>> G = sum(row) for row in M)  # Create a generator of row sums
>>> next(G)                     # iter(G) not required here
6
>>> next(G)                     # Run the iteration protocol next()
15
>>> next(G)
24
```

---

## Les dictionnaires

```python
>>> D = {
    'food': 'Spam', 
    'quantity': 4, 
    'color': 'pink'
}

>>> D['food']  
'Spam'

>>> D['quantity'] += 1 
>>> D
{'color': 'pink', 'food': 'Spam', 'quantity': 5}

>>> D = {}
>>> D['name'] = 'Bob'      # Create keys by assignment
>>> D['job']  = 'dev'
>>> D['age']  = 40

>>> D
{'age': 40, 'job': 'dev', 'name': 'Bob'}

>>> print(D['name'])
Bob
```

---

## Créer des dictionnaires

```python
>>> bob1 = dict(name='Bob', job='dev', age=40)                      # Keywords
>>> bob1
{'age': 40, 'name': 'Bob', 'job': 'dev'}

>>> bob2 = dict(zip(['name', 'job', 'age'], ['Bob', 'dev', 40]))    # Zipping
>>> bob2
{'job': 'dev', 'name': 'Bob', 'age': 40}
```

---

## Imbriquer des structures de données

```python
>>> rec = {'name': {'first': 'Bob', 'last': 'Smith'},
           'jobs': ['dev', 'mgr'],
           'age':  40.5}
```
---

## Accéder aux données imbriquées

```python
>>> rec['name'] 
{'last': 'Smith', 'first': 'Bob'}

>>> rec['name']['last']
'Smith'

>>> rec['jobs']
['dev', 'mgr']
>>> rec['jobs'][-1]
'mgr'

>>> rec['jobs'].append('janitor') 
>>> rec
{'age': 40.5, 'jobs': ['dev', 'mgr', 'janitor'], 'name': {'last': 'Smith',
'first': 'Bob'}}
```
---
## Clé manquante dans un dictionnaire

```python
>>> D = {'a': 1, 'b': 2, 'c': 3}
>>> D
{'a': 1, 'c': 3, 'b': 2}

>>> D['e'] = 99  # Assigning new keys grows dictionaries
>>> D
{'a': 1, 'c': 3, 'b': 2, 'e': 99}

>>> D['f']                           # Referencing a nonexistent key is an error
...error text omitted...
KeyError: 'f'
```

```python
>>> 'f' in D
False

>>> if not 'f' in D:      # Python's sole selection statement
       print('missing')

       missing
```

---

## Valeurs par défaut

```python
>>> value = D.get('x', 0)      # Index but with a default
>>> value
0
>>> value = D['x'] if 'x' in D else 0 # if/else expression form
>>> value
0
```
---

## Trier les clés d'un dictionnaire

```python
>>> Ks = list(D.keys())       
>>> Ks                       
['a', 'c', 'b']

>>> Ks.sort()                  
>>> Ks
['a', 'b', 'c']

>>> for key in Ks:  
        print(key, '=>', D[key])

a => 1
b => 2
c => 3
```
---

## Plus lisible avec sorted()

```python
>>> D
{'a': 1, 'c': 3, 'b': 2}

>>> for key in sorted(D):
        print(key, '=>', D[key])

a => 1
b => 2
c => 3
```
---

## La boucle for

```python
>>> for c in 'spam':
        print(c.upper())

S
P
A
M
```
---

## La boucle while

```python
>>> x = 4
>>> while x > 0:
        print('spam!' * x)
        x -= 1

spam!spam!spam!spam!
spam!spam!spam!
spam!spam!
spam!
```

---

## Itérations et optimisation (1)

```python
>>> squares = [x ** 2 for x in [1, 2, 3, 4, 5]]
>>> squares
[1, 4, 9, 16, 25]
```
---

## Itérations et optimisation (2)

```python
>>> squares = []
>>> for x in [1, 2, 3, 4, 5]:   
        squares.append(x ** 2) 

>>> squares
[1, 4, 9, 16, 25]
```
---

## Les tuples: une liste immutable

```python
>>> T = (1, 2, 3, 4)            # A 4-item tuple
>>> len(T)                      # Length
4

>> T + (5, 6)                   # Concatenation
(1, 2, 3, 4, 5, 6)

>>> T[0]                        # Indexing, slicing, and more
1
```
---

## Les ensembles: un outils sous utilisé

```python
>>> X = set('spam')
>>> Y = {'h', 'a', 'm'}  

>>> X, Y                
({'m', 'a', 'p', 's'}, {'m', 'a', 'h'})

>>> X & Y                           # Intersection
{'m', 'a'}

>>> X | Y                           # Union
{'m', 'h', 'a', 'p', 's'}

>>> X - Y                           # Difference
{'p', 's'}

>>> X > Y                           # Superset
False

>>> {n ** 2 for n in [1, 2, 3, 4]}  # Set comprehensions
{16, 1, 4, 9}
```
---
## Duplicats et différences

```python
>>> list(set([1, 2, 1, 3, 1]))      # Filtering out duplicates
[1, 2, 3]
>>> set('spam') - set('ham')        # Finding differences in collections
{'p', 's'}
>>> set('spam') == set('asmp')      # Order-neutral equality ('spam'=='asmp' False)
True
```
---

