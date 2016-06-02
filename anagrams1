from collections import defaultdict

import sys

import os.path

import re
def citeste_cuvintele(fisier):
 
   cuvinte = []
  
   with open(fisier) as f:
 
        #citim fisierul linie cu linie
   
      	for linie_text in f:
  
          	#fiecare linie o impartim in cuvinte
     
       	  	#un cuvant este orice sir de caractere delimitat de non-word characters ( \W ca regular expression) 
           
			      for cuvant in re.compile("\W").split(linie_text):
  
                    	#tinem doar cuvintele care nu sunt sir vid dupa ce le golim de caracterele whitespace
        
        		    if cuvant.strip():
                  
 	 			          cuvinte.append( cuvant.strip() )
  
       return cuvinte
def genereaza_anagramele(lista_cuvinte):
    """
    - structura de date in care tinem anagramele e un dictionar unde cheia e valoarea canonica a anagramei, iar valoarea e o lista ce contine toate aparitiile unei anagrame in lista de cuvinte 
    - pentru a afla numarul de aparitii al unei anagrame, e suficient sa ne uitam la lungimea listei de aparitii
    - "valoarea canonica" a anagramei o consideram a fi cuvantul format din sortarea alfabetica a literelor anagramei, dupa ce aceasta a fost convertita la litere mici
    """
    anagrame = defaultdict(list)
    for cuvant in lista_cuvinte:
        cuvant = cuvant.lower()
        anagrama = "".join( sorted( cuvant ) )
        anagrame[ anagrama ].append( cuvant )
    return anagrame
def anagramele_cuvantului_din_lista(lista_cuvinte, cuvant):
    anagrame = genereaza_anagramele( lista_cuvinte )
    cheia = "".join( sorted( cuvant.lower() ) )
    return anagrame[cheia]
def printeaza_toate_anagramele(lista_cuvinte):
    anagrame = genereaza_anagramele(lista_cuvinte)
    for cheia, cuvinte in anagrame.items():
        if len(cuvinte) > 1:
            print( cheia, ' apare de ' + str( len(cuvinte) ) + ' ori ca anagrama: ', cuvinte )

t1 = ['aab', 'aba', 'baa', 'AAB', 'AAC']
anagrame = genereaza_anagramele(t1)
#verificarea 1
if len( anagrame['aab'] ) == 4:
    print( 'aab apare de 4 ori ca anagrama in ', t1 )
#verificarea 2
if len( anagramele_cuvantului_din_lista(t1, 'BAA') ) == 4:
    print( 'BAA are 4 anagrame in lista: ', t1 )

if len(sys.argv) < 2:
    sys.exit('Numele fisierului din care sa citesc anagramele trebuie dat ca parametru')
    
fisier = sys.argv[1]

if not os.path.isfile(fisier):
   sys.exit('Nu pot citi fisierul ' + fisier + ' ( nu exista? )')

cuvinte = citeste_cuvintele(sys.argv[1])
anagrame = genereaza_anagramele( cuvinte )
#printeaza_toate_anagramele(cuvinte)

while True:
    cuvant = input("Cuvantul ('exit' pt terminare): ")
    cuvant = cuvant.strip()
    if cuvant == 'exit':
        break
    print('cuvantul ' + cuvant + ' (sau anagramele lui) apare de ' + str( len( anagramele_cuvantului_din_lista( cuvinte, cuvant ) ) ) + ' ori in fisierul ' + fisier)
