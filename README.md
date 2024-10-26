# TP1-POO
## Exercice 1 :Gestion des notes des étidiants 
Ce programme permet de gérer les notes des étudiants en effectuant les opérations suivantes :
1. Saisie des notes.
2. Tri et affichage des notes.
3. Calcul de la note moyenne.
4. Affichage des notes maximales et minimales.
5. Nombre d'étudiants.
## code 1:
package Poo_tp1;
import java.util.Arrays;
import java.util.Scanner;
public class EX1 {
	public static void main(String[] args) {
	float notes[];
	Scanner s=new Scanner(System.in);
	System.out.println("Donner le nombre des étudiants ?");
	int nbr=s.nextInt();
	notes=new float[nbr];
	for(int i=0;i<notes.length;i++) {
		System.out.println("Donner la note de l'étudiant  "+(i+1));// Saisie des notes 
		notes[i]=s.nextFloat(); }
Arrays.sort(notes);//tri des notes
System.out.println("les notes triées "+Arrays.toString(notes));	//Affichage de la liste des notes
//la note moyenne
float som=0;
for(int i=0;i<notes.length;i++) {
	som+=notes [i];	
}
System.out.println("la moyenne est: "+(som/notes.length));
//Recherche de la note max et la note min 
//1ére methode 
//Initialisation de max avec la première note
float max=notes[0];
for(int i=0;i<notes.length;i++) {
if(notes[i]>=max) {max=notes[i];}	
}
System.out.println("la note maximal est "+max);
//methode2 
// La note minimale est le premier élément du tableau trié
System.out.println("la note minimale est "+notes[0]);
// le nombre d’étudiants ayant une note saisie par l’utilisateur 
System.out.println("le nombre d’étudiants est "+notes.length);
	}}  
 
### Exercice 2 : Conjugaison des verbes du premier groupe
Ce programme permet de lire un verbe du premier groupe et d'afficher sa conjugaison au présent de l'indicatif. Le programme vérifie que le verbe se termine par "er", ce qui est caractéristique des verbes réguliers du premier groupe.
### code1 :
package Poo_tp1;
import java.util.Scanner;
public class EX2 {

	public static void main(String[] args) {
		Scanner s=new Scanner(System.in);
		System.out.printf("Entrez un verbe du premier groupe : ");
		 // Lecture et suppression des espaces inutiles
		String verbe=s.nextLine().trim();
		// Récupération des deux derniers caractères
		String subverbe=verbe.substring(verbe.length()-2,verbe.length());
		//Extraction du radical du verbe
		String radical=verbe.substring(0,verbe.length()-2 );
		 // Vérification que le verbe se termine par "er"
		if(! subverbe.equals("er")) {
			System.out.printf("Ce n'est pas un verbe du premier groupe (il doit se terminer par 'er'). ");
		
		}
		else {
			System.out.println("je "+radical+"e");
			System.out.println("tu "+radical+"es");
			System.out.println("il "+radical+"e");
			System.out.println("nous "+radical+"ons");
			System.out.println("vous "+radical+"ez");
			System.out.println("ils "+radical+"ent");
			
		}
	}
}
   

#### Exercice 3 : Opérations sur une chaîne de caractères
Ce programme permet d'effectuer plusieurs opérations sur une chaîne de caractères saisie par l'utilisateur. Un menu interactif permet de choisir l'opération à réaliser.
#### code3 :
package Poo_tp1;

import java.util.Scanner;

public class EX3 {

	public static void main(String[] args) {
		Scanner s1=new Scanner(System.in);
		Scanner s=new Scanner(System.in);
		int opération;// Variable pour stocker le choix de l'utilisateur
		String chaine="";// Variable pour stocker la chaîne saisie
			 do {   System.out.println("Menu des opérations :");
		            System.out.println("1. Saisir une chaîne");
		            System.out.println("2. Afficher la chaîne");
		            System.out.println("3. Inverser la chaîne");
		            System.out.println("4. Compter le nombre de mots");
		            System.out.println("5. Quitter");
		            System.out.print("Veuillez choisir une option : ");
		opération=s1.nextInt();
		
			switch(opération) {
			case 1 :
			System.out.print("Entrez une chaîne de caractères : ");
            chaine = s.nextLine();
            break;
			case 2 : if (chaine.isEmpty()) {//si user pas saisie une chaine 
                System.out.println("La chaîne est vide. Veuillez saisir d'abord une chaîne (choix 1).");
            } else {
                System.out.println("Chaîne saisie : " + chaine);
            }
			break;
			case 3 : if (chaine.isEmpty()) {
                System.out.println("La chaîne est vide. Veuillez saisir d'abord une chaîne (choix 1).");
            } else {
                String invch = new StringBuilder(chaine).reverse().toString();
                System.out.println("Chaîne inversée : " + invch);
            }break;
			case 4 :
				  if (chaine.isEmpty()) {
                      System.out.println("La chaîne est vide. Veuillez saisir d'abord une chaîne (choix 1).");
                  } else {
                      String mots[] = chaine.trim().split("\\s+");
                      System.out.println("Nombre de mots : " + mots.length);
                  }break;
			case 5 :System.out.println("vous quittez ");break;
			default :
				System.out.println("Choix invalide. Veuillez réessayer.");break;
			}
			if (opération != 5) {// Retour au menu après chaque opération
                System.out.println("Frappez une touche pour revenir au menu:");
                s.nextLine();// Attente de la saisie de l'utilisateur 
            }
		}while(opération!=5);
	}

}
##### Exercice 4 : Comptage des occurrences des lettres
Ce programme permet de lire une chaîne de caractères saisie par l'utilisateur et de compter les occurrences des lettres de l'alphabet, sans tenir compte des majuscules et minuscules. Le résultat est stocké dans un tableau et seules les lettres apparaissant au moins une fois dans la chaîne sont affichées.
#####  code 4:
package Poo_tp1;

import java.util.Scanner;
public class EX4 {

	public static void main(String[] args) {
		Scanner s=new Scanner(System.in);
		int nb_occurreances[]=new int [26];// Tableau pour stocker le nombre d'occurrences de chaque lettre
		System.out.println("Entrez une ligne de texte (max. 100 caractères) :   ");
		String ch=s.nextLine();
		if(ch.length()>100) { // Limite la chaîne à 100 caractères si nécessaire
			ch = ch.substring(0, 100);
			
		}
		 for(int i=0;i<ch.length();i++) {
			char car=ch.charAt(i);// Récupère le caractère à l'index i
			if(Character.isLetter(car)) {
			car=Character.toLowerCase(car);// Convertit le caractère en minuscule
			// Calcule l'index correspondant dans le tableau (ex :0 pour 'a', 1 pour 'b', etc.)
			int j=car - 'a';
			// Incrémente le compteur pour cette lettre
			nb_occurreances[j]++;	} 
		 } 
		 System.out.println("La chaîne "+ch+" contient : ");
			for(int i=0;i<nb_occurreances.length;i++) {
				// Vérifie si la lettre a au moins une occurrence
			if (nb_occurreances[i] > 0) {
				char l=(char)(i+'a');// Convertit l'index en lettre
				System.out.println(nb_occurreances[i] + " fois la lettre '" + Character.toUpperCase(l)+"'");
				
			}
		}
	}
}
  
