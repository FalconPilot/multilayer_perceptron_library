
# Descritpion du neuronne

# Valeur

tuple contenant les valeurs suivantes :

* Nb_inputs : nombre d'entrée conecté au neurone
* Weights : liste des poids à appliqué aux entrée pour le calcul. Cette liste doit être de taille Nb_inputs et les poids doivent être rangé dans l'ordre croissant de leurs indice.
* B : le biais du neurronne
* F : la fonction d'activation


# Messages

## Neurone

### reçut :

* {done, Result, {PID, Layer, Rank}} : reçoit une entrée du neuronne Layer,Rank
* {update, New_value} : reçoit une demande de mise a jour des poids de la part du trainer

### envoyé :

* {done, Result, {PID, Layer, Rank}} : envoi le resultat du calcul

## Input

* {input, Value} : envoi Value aux neurone conecté à cette entrée

## Trainer

### envoyé
* {update, New_value} : demande de mettre ajour la matrice de poids du neurone
* ok : le test est positif
* updated : le test est négatif et le neurone à été mis à jours. 

### reçut
* {train, From, Training_constants} : l'entraineur doit se mettre en attente d'un resultat du resaux de neuronne, 
Training_constants contient les élément suivant : {Threshold, Primus_F, Speed}
	* Threshold : marge d'erreur acceptable par l'entraineur
	* Primus_F : dérivée de la fonction d'activation du neuronne
	* Speed : vitesse d'aprentissage
	* Training_outputs : liste valeur attendut aux sortie du resaux de neurone
