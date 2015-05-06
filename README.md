# Expo-Sciences #

*Je participe aussi à [Crée Ta Ville](http://www.creetaville.com/)*

**Une copie des scripts utilisés lors de la présentation Powerpoint durant l'expo-science, et Crée Ta Ville.**

[PiFM *par ](https://github.com/rm-hull/pifm), modifié en français.

Licence [GPU GENERAL PUBLIC LICENCE](http://www.gnu.org/copyleft/gpl.html).

Le code utilisé dans la présentation PowerPoint est le suivant;

**PiFM.cpp**

    // GPIO setup macros. Always use INP_GPIO(x) before using OUT_GPIO(x) or SET_GPIO_ALT(x,y) 
    #define INP_GPIO(g) *(gpio+((g)/10)) &= ~(7<<(((g)%10)*3)) 
    #define OUT_GPIO(g) *(gpio+((g)/10)) |= (1<<(((g)%10)*3)) 
    #define SET_GPIO_ALT(g,a) *(gpio+(((g)/10))) |= (((a)<=3?(a)+4:(a)==4?3:2)<<(((g)%10)*3)) 
      
    #define GPIO_SET *(gpio+7) // sets bits which are 1 ignores bits which are 0 
    #define GPIO_CLR *(gpio+10) // clears bits which are 1 ignores bits which are 0 
    #define GPIO_GET *(gpio+13) // sets bits which are 1 ignores bits which are 0 
      
    #define ACCESS(base) *(volatile int*)((int)allof7e+base-0x7e000000) 
    #define SETBIT(base, bit) ACCESS(base) |= 1<<bit 
    #define CLRBIT(base, bit) ACCESS(base) &= ~(1<<bit) 
      
    #define CM_GP0CTL (0x7e101070) 
    #define GPFSEL0 (0x7E200000) 
    #define CM_GP0DIV (0x7e101074) 
    #define CLKBASE (0x7E101000) 
    #define DMABASE (0x7E007000) 
    #define PWMBASE (0x7e20C000) /* PWM controller */
    
*Le code n'est pas complet, veuillez regardez le fichier au complet [ici](https://github.com/felixinx/Expo-Science/blob/master/pifm.cpp).*

**Pour ajouter le scipt au démarrage**

Lancer le terminal et exécuter;

    chmod 755 launch.sh   #Permission au fichier
    mkdir logs            #Création d'un dossier "logs"
	sudo crontab -e       #Ouverture du fichier Démarrage à l'aide de NANO
    #Ajouter la ligne suivante à la fin du fichier
	@reboot sh /home/pi/pifm/launch.sh >/home/pi/pifm/logs/cronlog 2>&1
    #Modifier au besoin selon les emplacements de vos fichiers

##TODO
- [x] Traduire en français (*voir le prochain*)
- [ ] Régler les problèmes d'affichages des accents
- [ ] Construire l'interface web
- [ ] Ajouter un message lors de la lecture de la chanson

Merci!
