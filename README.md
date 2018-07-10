Sebastian Cojocariu 311CB UPB ACS
					
				                Trie Data Structure


In implementare am utilizat urmatoarele functii:

1) void Insert(Trie *trie,char *string)
Functie de insert care insereaza un string dat ca parametru in trie
Daca cuvantul e null se iese din functie.Parcurgem trie-ul in functie de cuvantul
dat litera cu litera pana cand intalnim o litera care nu e in trie.Daca am ajuns 
la sfarsit de cuvant marcam cu 1 la sfarsit si iesim din functie.Daca raman litere ,
creem celule pentru fiecare astfel de litera si facem legaturile.Sortam alfabetic 
vectorul de fii dupa litera din fiecare celula;

2)TCelula *find_prefix(Trie *trie,char *prefix)
Functie care returneaza celula de sfarsit al unui prefix primit ca parametru
sau NULL daca nu a gasit prefixul.Parcurgem litera cu litera prefixul dat si
cautam drumul corect.Returnam rezultatul dupa caz.

3)void afisare_cuvinte_de_la_o_celula_anume(FILE *out,TCelula *a,char *cuvant,int dimensiune)
Functie recursiva care afiseaza cuvintele existente in trie de la o celula anume.
Daca am gasit cuvant la acest pas afisam in fisier.Parcurgem recursiv pentru fii 
lui a(celula la care ne aflam).Creem o copie a lui aux pe care o vom da ca parametru 
pentru functia de mai jos.
Vom folosi functia in implementarea functiilor care  urmeaza.

4)void find_all_with_prefix(FILE *out,Trie *trie,char *cuvant,char *prefix)
functia returneaza toate cuvintele din trie care inceput cu un prefix dat
e o functie recursiva care construieste in stringul cuvant dat ca parametru
litera cu litera cuvintele (celulele care au sfarsit_cuvant=1 si le afiseaza unul dupa altul)
Metoda:cautam prefixul dat in trie cu functia find_prefix.Daca e null inseamna ca nu exista si 
deci nu exista nici cuvintele care sa inceapa cu el.Altfel facem o copie a prefixuli si o trimitem mai departe 
in functia afisare_cuvane_de_la_o_celula_anume.

5)void mean_length(TCelula *celula,float *suma,int dimensiune,int dimensiune_prefix,int *nr)
Functie de tip void care ne va furniza suma si nr de elemente care incep de la o celula anume
primita ca parametru.la inceput suma si nr sunt 0,dimensiunea este tot 0(tine cat de multe litere am 
inaintat de la celula data ca parametru),iar dimensiune_prefix va fi tinut pe post de strlen(prefix)
Metoda:daca avem cuvant marim suma si nr (nr de cuvinte de la celula data ca parametru).Parcurgem recursiv 
pt fii,daca exista.

6)void remove_celula(Trie *trie,char *cuvant)
Functie care sterge un cuvant din trie.
Metoda:cautam cuvantul in trie.Daca cuvantul e null sau prefixul nu e gasit iesim din functie
Altfel inseamna ca am gasit cuvantul.Marcam cu 0 sfarsit_cuvant.Parcurgem de jos in sus cat 
timp nu gasim o celula cu sfarsit_cuvant=1 .Cautam in vectorul de fii al lui aux->parinte indicele
la care se gaseste aux si nr_fii==0.Translatam la stanga vectorul de fii de la pozitia j;
ultimul din vectorul de fii va fi NULL(cel de pe pozitia nr_fii-1)
acutalizam aux->nr_fii--.

7)void find(FILE *out,Trie *trie, char *element_cautat)
Functie care cauta un element in trie si returneaza True sau False
Metoda:Daca trie-ul e compus doar dintr-o celula(cea cu litera='\0') afisam False si iesim.
Cautam litera cu litera in trie in functie de literele elementului_cautat dat ca parametru.
Verificam daca am ajuns la sfarsitul cuvantului si afisam mesajul corespunzator.

8)void find_longest_prefix(FILE *out,Trie *trie,char *prefix)
Functie care returneaza cel mai mare cuvant cel mult egal cu un prefix dat sau None daca nu exista.
Daca trie-ul e null sau prefixul e null afisam None si iesim din functie.
Apelam find_prefix pentru prefix cat timp nu il gasim in trie
si micsoram cu cate o litera prefixul la fiecare pas(punem '\0' la sfarsit si facem count--)
Daca aux nu e null afisam litera cu litera prefixul,altfel afisam "None"

Main:citim nr de linii.Cu un for de la i=1 la nr_linii citim operatia si stringul asociat ei
(string realocat la fiecare pas,in functie de citirea facuta cu fgetc) 
