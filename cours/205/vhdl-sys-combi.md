
**Introduction au VHDL : instructions concurrentes**
==========================

## [Mamadou Lamine Ndiaye](mailto:mamadoulamine.ndiaye@ucad.edu.snp), ESP Dakar

> Document en cours de relecture, version du 2015/01/25

## Introduction au VHDL ##

#### Introduction ####

Les méthodes de conception des circuits logiques ont beaucoup évoluées depuis les premiers circuits programmables par l’utilisateur apparus dans les années 90. Les circuits logiques standard avec les technologie TTL et CMOS sont suivis des circuits logiques à fonctionnement programmables avec les microprocesseurs et les microcontrôleurs et les circuits intégrés spécifiques (ASICs) fabriqués en grande série. 

Le VHDL peut être utilisé pour la modélisation, la simulation et la synthèse des circuits logiques.
Le VHDL permet de faire la synthèse logique des circuits en facilitant le passage de la description comportementale à la vue structurelle. Le VHDL permet aussi de faire la synthèse physique des circuits en générant la vue physique du circuit à partir de la description structurelle. La synthèse physique aboutit à la liste des portes logiques nécessaires à la réalisation du circuit ainsi qu’à leurs interconnexions. 


### VHDL: Les concepts de base ###

 

L’entité (Entity) permet de déclarer les modes des ports en entrée et/ou sortie (in, out, inout, buffer)
IN pour dire que le port est à lecture seule
OUT port à écriture seule
INOUT port à lecture/écriture
BUFFER écriture/lecture sur un port

L’architecture (Architecture) permet de décrire le comportement de la fonction à synthétiser, définir les signaux internes, les composants, ….
A une entité peut correspondre plusieurs architectures.

VHDL considère deux domaines d'instructions disjoints: les instructions concurrentes et séquentielles. Chaque domaine possède ses propres instructions qu'il n'est pas permis d'utiliser dans l'autre domaine.

![Figure : Structure programme vhdl](images/Structure_programme.png "Structure programme VHDL")

Les instructions concurrentes modélisent des comportements asynchrones s’executant en parallèle.
Les instructions séquentielles font intervenir la notion d’ordre et de durée et modélisent des comportements procéduraux. Les instructions séquentielles ne peuvent être utilisées que dans le corps d'un processus ou d'un sous-programme.







sauf à l’intérieur d’un processus. Seuls les signaux peuvent communiquer entre plusieurs processus dans une architecture et avec le monde extérieur.

![Figure : Declaration des types de base](images/declaration-type-base.png "Type de base")


Le symbole d’affectation est :=. Si l ’on a écrit a:=b la valeur de b est affectée à a et si b évolue par la suite, a  ne changera pas pour autant. 
Exemple:    Signal s_entier : integer range  0 to 31;





* 2 Opérateurs de multiplication :      *, /, mod, rem
* 3 Opérateurs d’addition :          	  +, -, &
* 4 Opérateurs  relationnels :          =, /=, < , <= , >, >=
* 5 Opérateurs de décalage :   	  sll, srl , sla,sra,rol,ror
* 6 Opérateurs logiques: 		  and , or, nand, nor, xor, xnor



### Les littéraux(valeurs explicitées) ###

Un litteral est un mot du langage attaché à des types (entier, réel, caractère, chaine de caractère, etc.)


* Caractères :	 		’1’, ’c’,’b’,’#‘
* Chaînes: 			"10110100", "bonjour", "x@&"
* Chaînes de bits:		B"1010_1101", X "6F", O "265"
* Décimaux: 			27, -5, 4e3, 76_562, 4.25
* Basés: 			2#1001#, 8#65_07, 16#C5#e2
  

Pour la lecture et l’interprétation de 16#C5#e2, on peut lire en base 16, C5 multiplié par 16^2. 



## Logique combinatoire : Instructions concurrentes ##








		 ………
		
		 signal2  when expresion2 else
 
 Pour l’exemple avec la carte DEII de Altera on pourra faire les associations suivantes:
![Figure : Instructions concurrentes : affectation conditionnelle](images/affectation-conditionnelle.png "Affectation conditionnelle")


### Instructions concurrentes : Affectation sélective  WITH…….SELECT ###


with  expression  select 

		signal2 when   	valeur2,
		signal3 when 	others ;


C’est une affectation d’une  valeur suivant  l’état de l’expression testée. Au niveau de la syntaxe, l’expression testée peut prendre les valeurs valeur1, valeurs2, etc.




![Figure : Decodeur BCD 7 Sgments ](images/decodeur-bcd-7segment.png "Decodeur BCD 7 Segments")



### Instructions concurrentes : Génération conditionnelle IF ……GENERATE / FOR …..GENERATE ###

L'instruction generate est une instruction concurrente qui permet la description de comportements ou de structures régulières.
Elle permet de multiplier des instructions, soit un nombre fixe de fois (forme itérative), soit selon une condition (forme conditionnelle). Elle s’utilise avec for (itérative) ou if (conditionnelle)









### Les composants ### 


* Interconnexions hiérarchiques des composants (entité) que l’on mappe dans une l’entité "TOP" sous forme de components.

![Figure : Synthaxe component  ](images/synthaxe-component.png "Synthaxe Component")

Le programme de la figure utilise les composants (component) pour créer un prototype de décodeur Bcd7Segment à partir du programme de la figure précedente pour instancier quatre composants (afficheurs digit0, digit1, digit2, digit3). La partie encadrée en vert permet de déclarer le composant, la syntaxe est presque identique à celle de l’entité (Bcd7Segment). 
![Figure : Exemple utilisant la directive component  ](images/exemple-component.png "Exemple Synthaxe Component")
