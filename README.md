#include <iostream>

using namespace std;
struct Uczen {
    int ID;
    string imie;
    int wyniki[3];
    float srednia;
};

Uczen uczniowie[17];
int liczba_uczniow = 0;

void DodajWpis() {
    if (liczba_uczniow>=17) {
        cout<<" Limit dodanych uczniow zostal osiagniety !!!\n";
        return;
    }

    cout<<" Podaj ID ucznia: ";
    cin>> uczniowie[liczba_uczniow].ID;
    cout<<" Podaj imie ucznia: ";
    cin>>uczniowie[liczba_uczniow].imie;
    cout<<"Podaj wyniki z 3 kolokwiow: ";
    for(int i=0; i<3; i++){
        cin>>uczniowie[liczba_uczniow].wyniki[i];
    }
    uczniowie[liczba_uczniow].srednia=(uczniowie[liczba_uczniow].wyniki[0]+uczniowie[liczba_uczniow].wyniki[1]+uczniowie[liczba_uczniow].wyniki[2]) / 3.0;
    liczba_uczniow++;
}

void UsunWpis() {
    int id;
    cout << "ID ucznia do usuniecia: ";
    cin >> id;
    int i;
    for (i=0; i<liczba_uczniow; i++){
        if (uczniowie[i].ID==id){
            break;
        }
    }
    if (i<liczba_uczniow){
        for (int j=i; j< liczba_uczniow-1; j++) {
            uczniowie[j]=uczniowie[j+1];
        }
        liczba_uczniow--;
    } else{
        cout<<"Brak ucznia o takim ID.\n";
    }
}

void AktualizujWpis(){
    int id;
    cout<< "ID ucznia do aktualizacji: ";
    cin>>id;
    int i;
    for (i=0; i<liczba_uczniow; i++){
        if (uczniowie[i].ID == id){
            cout<< "Nowe wyniki 3 kolokwiow: ";
            for (int j=0; j<3; j++){
                cin>>uczniowie[i].wyniki[j];
            }
            uczniowie[i].srednia=(uczniowie[i].wyniki[0]+uczniowie[i].wyniki[1]+uczniowie[i].wyniki[2])/3.0;
            break;
        }
    }
    if (i==liczba_uczniow){
        cout<< "Brak ucznia o podanym ID.\n";
    }
}

void PokazWszystkieWpisy(){
    for (int i=0; i<liczba_uczniow; i++){
        cout <<"ID: "<<uczniowie[i].ID<< ", Imie: "<<uczniowie[i].imie<< ", Srednia: "<<uczniowie[i].srednia<< "\n";
    }
}

void SredniaWszystkichUczniow(){
    float suma=0;
    for (int i=0; i<liczba_uczniow; i++) {
        suma+=uczniowie[i].srednia;
    }
    cout << "Srednia wszystkich uczniow: " <<suma/liczba_uczniow<<"\n";
}

void NajlepszyINajgorszyWynik(){
    int najlepszyWynik=0, najgorszyWynik=0;
    for (int i=1; i<liczba_uczniow; i++) {
        if (uczniowie[i].srednia>uczniowie[najlepszyWynik].srednia){
            najlepszyWynik=i;
        }
        if (uczniowie[i].srednia<uczniowie[najgorszyWynik].srednia){
            najgorszyWynik=i;
        }
    }
    cout<< "Najlepszy wynik: "<<uczniowie[najlepszyWynik].srednia<< ", Uczen: "<<uczniowie[najlepszyWynik].imie<<"\n";
    cout<< "Najgorszy wynik: "<<uczniowie[najgorszyWynik].srednia<< ", Uczen: "<<uczniowie[najgorszyWynik].imie<<"\n";
    }

int main(){
    int wybierz;
    do{
        cout<<"MENU\n";
        cout<<"1.Dodaj wpis\n";
        cout<<"2.Usun wpis\n";
        cout<<"3.Aktualizuj wpis\n";
        cout<<"4.Pokaz wszystkie wpisy\n";
        cout<<"5.Srednia wszystkich studentow\n";
        cout<<"6.Wyswietl najlepszy i najgorszy wynik\n";
        cout<<"7.Zakoncz dzialanie\n";
        cin>>wybierz;

    switch(wybierz){
        case 1:
            DodajWpis();
            break;
        case 2:
            UsunWpis();
            break;
        case 3:
            AktualizujWpis();
            break;
        case 4:
            PokazWszystkieWpisy();
            break;
        case 5:
            SredniaWszystkichUczniow();
            break;
        case 6:
            NajlepszyINajgorszyWynik();
            break;
        case 7:
            cout<<"Zakonczono\n";
            break;
        default:
            cout<<"Brak takiej opcji wybierz inna !!!\n";
            break;
        }
    }while(wybierz!= 7);

    return 0;
}
