import java.util.*;
import java.lang.*;

public class TD2marinIvre {

    
    public static void main (String[]args)
    {
        menuMarin();
        
    }

     // ///////////////////////////// fonctions tirés du fichier Ut.java /////////////////////////////////////////////

    public static int randomMinMax (int min, int max)
    {
	    // Resultat : un entier entre min et max choisi aleatoirement
	    Random rand = new Random();
	    int res = rand.nextInt(max - min + 1) + min;
	    // System.out.println(res + " in [" + min + "," + max + "]");
	    // assert min <= res && res <= max : "tirage aleatoire hors des bornes";
	    return res;
    }

    public static void clearConsole()
    {
        	// Action : efface la console (le terminal)
            System.out.print("\033[H\033[2J");
    }
   

    public static void pause (int timeMilli) {
	// Action : suspend le processus courant pendant timeMilli millisecondes
	try {
	    Thread.sleep(timeMilli); 
	} catch(InterruptedException ex) {
	    ex.printStackTrace();
	}
    }
    
    public static void sautLigne(){
        System.out.println("");
    }

    // /////////////////////////////////////////////////////////////////////////////////////////////////////////////////

    public static void menuMarin ()
    {

        Scanner scanner = new Scanner (System.in);

        // Choix config
        int longClavier;
        int largClavier;
		
        int longMinClavier;
        int longMaxClavier;
        int largMinClavier;
		int largMaxClavier;
		
        int nbMarinsClavier;
        boolean traceClavier;
		
        float probaMinClavier;

        sautLigne();sautLigne();sautLigne();
        System.out.println("    Bienvenue dans le Jeu du Marin Ivre !"); 

        sautLigne();sautLigne();sautLigne();
        
        System.out.println("    Simulation Marin Ivre avec affichage :                      [1]");
        sautLigne();
        System.out.println("    Simulation Marin Ivre sans affichage :                      [2]");
        sautLigne();
        System.out.println("    Proba de n Marins Ivres arrivent au bateau :                [3]");
        sautLigne();
        System.out.println("    Proba de n Marins arrivent au bateau                        [4]");
        System.out.println("    pour un ensemble de largeur de planche :                       ");
        sautLigne();
        System.out.println("    Largeur minimal de la planche à partir                      [5]");
        System.out.println("    de n proba qu'un Marin arrive au bateau :                   ");
        sautLigne();
        System.out.println("    Quitter le progamme :                                       [0]");

        sautLigne();sautLigne();sautLigne();
        
        System.out.print("    Saisissez le chiffre correspondant au mode souhaité : "); 
        
        while (true)
        {
            System.out.print("    ");
            int touche = scanner.nextInt(); // Choix menu
            
            if (touche == 1)
            { 
				traceClavier=true; sautLigne();
                System.out.print("    Longeur   ");
                longClavier = scanner.nextInt();
                
                sautLigne();
                System.out.print("    Largeur   ");
                largClavier = scanner.nextInt();
                
                clearConsole();
                arivobato(longClavier,largClavier,traceClavier);
                restart();
            }
            else if (touche == 2)
            {   
				traceClavier=false; sautLigne();
                System.out.print("    Longeur   ");
                longClavier = scanner.nextInt();
                
                sautLigne();
                System.out.print("    Largeur   ");
                largClavier = scanner.nextInt();
                
                clearConsole();
                arivobato(longClavier,largClavier,traceClavier); 
                restart();
            }
            else if (touche == 3)
            {   
                sautLigne();
                System.out.print("    Longeur   ");
                longClavier = scanner.nextInt();
                
                sautLigne();
                System.out.print("    Largeur   ");
                largClavier = scanner.nextInt();
                
                sautLigne();
                System.out.print("    Nombre de marins   ");
                nbMarinsClavier = scanner.nextInt();
                clearConsole();
                
                probaEmpirique(longClavier,largClavier,nbMarinsClavier);
                restart();
            }
            else if (touche == 4)
            {   
                sautLigne();
                System.out.print("    Largeur   ");
                largClavier = scanner.nextInt();
                
                sautLigne();
                System.out.print("    Longeur minimal   ");
                longMinClavier = scanner.nextInt();

                sautLigne();
                System.out.print("    Longeur maximal   ");
                longMaxClavier = scanner.nextInt();
                
                sautLigne();
                System.out.print("    Nombre de marins   ");
                nbMarinsClavier = scanner.nextInt();
                
                clearConsole();
                afficheProba(largClavier,longMinClavier,longMaxClavier,nbMarinsClavier);
                restart();
            }
            else if (touche == 5)
            {   
                sautLigne();
                System.out.print("    Longeur   ");
                longClavier = scanner.nextInt();
                
                sautLigne();
                System.out.print("    Nombre de marins   ");
                nbMarinsClavier = scanner.nextInt();
                
                sautLigne();
                System.out.print("    Probabilité minimal   ");
                probaMinClavier = scanner.nextFloat();
                clearConsole();
                largeurMin(longClavier,nbMarinsClavier,probaMinClavier); 
                restart();
            }
            else if (touche == 0)
            {   
                clearConsole();
                sautLigne();
                sautLigne();
                System.out.println("    Fin du programme...");
                pause(1500);
                
                clearConsole();
                System.exit(1);
            }
			else 
			{
				sautLigne();
				System.out.print("    Saisissez le chiffre correspondant au mode souhaité ");
			}
        }
    }

    public static void restart ()
    {
        Scanner scanner = new Scanner (System.in);
        sautLigne(); sautLigne();
        System.out.println("    Appuyer sur 1 pour retourner au menu.");
        System.out.print("    ");
        
        while (true)
        {
            int touche = scanner.nextInt(); // Choix menu
            if (touche== 1)
            {
                clearConsole();
                menuMarin();
            }
            else
            {
                System.out.println("    Appuyer sur 1 pour retourner au menu.");
                System.out.print("    ");
            }
        }
    }
    
    public static boolean arivobato (int Long,int Larg,boolean trace)
    {
        int marinX= Larg/2; // Coordonés de départ du marin
        int marinY=0;
        boolean estArrive=false;
        int vr; // valeur random

        while(marinX<Larg && marinX>=0 && marinY<Long)
        { // marin n'est pas à l'eau
        
            if (trace==true) 
            {
                clearConsole();
                sautLigne();
                affichePlanche(Long, Larg, marinX, marinY);
                pause(1000);
            }
        
            vr = randomMinMax(1, 100);

            if (vr< 50) // Vers l'avant 
            {
                marinY+=1;
            }
            else if (vr <=70) { // Vers la gauche  
                marinX-=1;
            }
            else if (vr <=90){ // Vers la droite
                marinX+=1;
            } 
            else if (vr <= 100)
            { // Vers l'arrière
            marinY-=1;
            }       
            
            if (marinY<0) // Marin ne peut pas sortir par derrière
            {
                marinY=0;
            }
        } 

        if (marinX==Larg || marinX<0 || marinY<0) 
        {
            estArrive=false; sautLigne();
            System.out.println("    Le marin est tombé à l'eau ! ");
        }
        else 
        {
            estArrive=true; sautLigne();
            System.out.println("    Le marin est arrivé sur le bateau !");
        }
    
        
        return estArrive;
    }

    public static void affichePlanche (int Long, int Larg, int posX, int posY) 
    {
        
        System.out.println("    X: " + posX + " Y: " + posY);
        System.out.print("  ");
        for (int i=0; i < Larg+8; i++) // Affichage Mer
        {
            System.out.print("-");
        }
        System.out.print("      PORT"); // Bordure gauche planche
        sautLigne();
            
        for (int i=0;i<Long;i++) { // Dim X
            System.out.print("  ~~~|"); // Bordure gauche planche
            
                
            for (int j=0;j<Larg;j++) // Dim Y
            {
                if (i==posY && j==posX) // position marin 
                {
                    System.out.print("O"); // Marin
                }
                else
                {
                    System.out.print("-"); // Planche
                }
                
            }
            System.out.println("|~~~"); // Bordure droite planche
        }
        
        System.out.print("  ");
        for (int i=0; i < Larg+8; i++) // Affichage Bateau
        {
        System.out.print("-");
        }
        System.out.println("      BATEAU"); 
        sautLigne();
    }
 
    public static float probaEmpirique (int Long, int Larg, int nbMarins)
    {
        float probaNbMarins=0;
        int sMarins=0; // somme de marins arrivé au bateau 
        int nbMarinsTombe; // nombre de marins tombé à l'eau
        int vr; // valeur aleatoire
        boolean estArrive;
        int varPourcent = 100;

        for (int i=0; i<nbMarins; i++)
        {
            estArrive = arivobato(Long,Larg,false);
         
            if (estArrive==true) // arrivé au bateau
            {
                sMarins = sMarins + 1;
            }
            clearConsole();
        }
        
        probaNbMarins = sMarins/varPourcent;
        nbMarinsTombe = nbMarins-sMarins;
        
        
        sautLigne();
        System.out.println("    Proba de marins arrivé au bateau sur " + nbMarins + " marins : " + probaNbMarins );
        System.out.println("    Marins tombés à l'eau : " + nbMarinsTombe);
        return probaNbMarins;
    }
    
    public static void afficheProba (int Larg, int longMin, int longMax, int nbMarins) 
    {
        float probaNb=0;
        
        for (int i=longMin;i<=longMax;i++)
        {
            probaNb = probaEmpirique(longMax,Larg,nbMarins);
            
            sautLigne();
            System.out.println("    Proba marin arrive au bateau pour longueur = "+ i + " : " + probaNb);
        }
    }
    
    public static int largeurMin (int Long, int nbMarins, float probaMin) 
    {
        int largMin=0;
        float probaNb;
        
        for (int i=1; i<Long; i++) 
        {
            probaNb = probaEmpirique(Long, i, nbMarins);
            if (probaNb<=probaMin)
            {
                largMin = i;
                i=Long;
                
            }
            clearConsole();
        }
        sautLigne();
        System.out.println("    Largeur minimal pour une probabilité minimal de " + probaMin +" : "+largMin);
        return largMin;
    }
}
