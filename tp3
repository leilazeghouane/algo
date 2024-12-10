#include <stdio.h>
#include <stdlib.h>

// Définition de la structure d'un élément de la liste
typedef struct element {
    int val;
    struct element *suivant;
} element;

// Fonction pour créer une liste vide
element *creerListe() {
    return NULL; // Une liste vide est représentée par un pointeur NULL
}

// Fonction pour construire une liste à partir d'un tableau
element *chargerListe(int Tab[], int taille, element *liste) {
    for (int i = taille - 1; i >= 0; i--) { // On insère les éléments en début
        element *nouveau = (element *)malloc(sizeof(element));
        if (!nouveau) {
            printf("Erreur d'allocation mémoire\n");
            exit(EXIT_FAILURE);
        }
        nouveau->val = Tab[i];
        nouveau->suivant = liste;
        liste = nouveau;
    }
    return liste;
}

// Procédure pour afficher les éléments d'une liste
void afficherListe(element *liste) {
    if (liste == NULL) {
        printf("La liste est vide\n");
    } else {
        while (liste != NULL) {
            printf("%d -> ", liste->val);
            liste = liste->suivant;
        }
        printf("NULL\n");
    }
}

// Fonction pour supprimer un élément à la fin de la liste
element *supprimerEnFin(element *liste) {
    if (liste == NULL) {
        printf("La liste est déjà vide\n");
        return NULL;
    }

    if (liste->suivant == NULL) { // Cas où la liste contient un seul élément
        free(liste);
        return NULL;
    }

    element *temp = liste;
    while (temp->suivant->suivant != NULL) {
        temp = temp->suivant;
    }

    free(temp->suivant);
    temp->suivant = NULL;
    return liste;
}

// Fonction pour ajouter un élément au début de la liste
element *ajouterEnDebut(element *liste, int valeur) {
    element *nouveau = (element *)malloc(sizeof(element));
    if (!nouveau) {
        printf("Erreur d'allocation mémoire\n");
        exit(EXIT_FAILURE);
    }
    nouveau->val = valeur;
    nouveau->suivant = liste;
    return nouveau;
}

// Procédure pour vider une liste
void viderListe(element *liste) {
    element *temp;
    while (liste != NULL) {
        temp = liste;
        liste = liste->suivant;
        free(temp);
    }
    printf("La liste est vide\n");
}

// Fonction main pour tester les fonctions
int main() {
    int Tab[10] = {1, 3, 5, 7, 8, 10, 9, 11, 13, 20};
    element *liste = creerListe();

    liste = chargerListe(Tab, 10, liste);
    afficherListe(liste);

    liste = supprimerEnFin(liste);
    afficherListe(liste);

    liste = ajouterEnDebut(liste, 40);
    afficherListe(liste);

    viderListe(liste);

    return 0;
}
