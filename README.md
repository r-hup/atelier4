# atelier4
Ex1 :	
#include <iostream>

using namespace std;
class complex{
private:
    double real;
    double img;
public:
    complex(): real(0), img(0){}
    complex add(const complex& C2){
        complex somme(real+C2.real, img+C2.img);
        return somme;
    }
complex divise(const complex& C2){
    double denom=C2.real*C2.real + C2.img*C2.img
    complex divise(real*C2.real + img*C2.img/denom, real*C2.img - img*C2.real/denom);
    return devise;
}
complex multipl(const complex& C2){
    complex fois(real*C2.real - img*C2.img, real*C2.img + img*C2.real);
    return fois;
}
complex moins(const complex& C2){
    complex soustra(real-C2.real, img - C2.img);
    return soustra;
}
bool egal(const complex& C2){
    return real==C2.real && img==C2.img;
}
void display(){
    cout<< real << "+" << img << "i" <<endl;
}
void menu(){
    cout<< "choisissez une operation" <<endl;
    cout<< "2.soustraction" <<endl;
    cout<< "3.multiplication" <<endl;
    cout<< "4.division" <<endl;
    cout<< "5.egalite" <<endl;
    cout<< "6.quitté" <<endl;
}
};
int main()
{
    double r1, r2, i1, i2;
    cout<< "entrer le peremier nombre comlexe:partie réelle" <<endl;
    cin>> r1;
    cout<< "entrer le peremier nombre comlexe:partie imaginaire" <<endl;
    cin>> i1;
    cout<< "entrer le deuxieme nombre comlexe:partie réelle" <<endl;
    cin>> r2;
    cout<< "entrer le deuxieme nombre comlexe:partie imaginaire" <<endl;
    cin>> i2;
    complex C1(r1,i1);
    complex C2(r2,i2);
    complex result;
    int choice;
    cout<< "entrez le numéro de votre choix";
    cin>> choice;
    switch(choice){
    case 1:
        result=C1.add(C2);
        cout<< "addition" << result <<endl;
        break;
    case 2:
        result=C1.moins(C2);
        cout<< "soustraction" << result <<endl;
        break;
    case 3:
        result=C1.multipl(C2);
        cout<< "multiplication" << result <<endl;
        break;
    case 4:
        result=C1.divise(C2);
        cout<< "divition" << result <<endl;
        break;
    case 5:
        result=C1.egal(C2);
        cout<< "égalité" << result <<endl;
        break;
    case 6:
        cout<< "au revoir";
        break;
    }
    return 0;
}

Ex2 :
#include <iostream>
#include<string>

using namespace std;

class animal{
    protected:
    int age ;
    string nom ;
    public:
        set_value(const string& N,int A){
            nom=N;
            age=A;
        }
};
class zebra:public animal{
   private:
       string lieu;
   public:
       zebra(const string& L):lieu(L){};
       void afficher(){
       cout<< "le nom du zebre"<< nom << "age" << age << "le lieu d'origine " << lieu <<endl;
       }
};
class daulphine:public animal{
    private:
    string origine;
    public:
    daulphine(const string& O):origine(O){};
     void afficher(){
       cout<< "le nom du daulphine"<< nom << "age" << age << "le lieu d'origine " << origine <<endl;
       }
};

int main()
{
    zebra ray("foret");
    daulphine daulphin("océon");

    ray.set_value("zebre rayé", 6);
    daulphin.set_value("daulphin", 4);

    ray.afficher();
    daulphin.afficher();

    return 0;
}
Ex3 :
#include <iostream>
#include<string>

using namespace std;

class Personne{
private:
    string nom;
    string prenom;
    string datenaissance;
public:
    Personne(const string& N, const string& P, const string& D):nom(N), prenom(P), datenaissance(D){}
    virtual void afficher() const{
     cout<<"le nom est:" << nom << "le prenom est:" << prenom << "la date de naissance est:" << datenaissance << endl;
     }
};
class Employe : public Personne{
private:
    int salaire;
public:
    Employe(const string& N, const string& P, const string& D, int S) : Personne(N, P, D), salaire(S){}
    double get_salaire(){
    return salaire;
     };
    void set_salaire(int S){
        salaire=S;
    }
    void afficher() const override{
        Personne::afficher();
     cout<< "salaire:" << salaire << endl;
     }
};
class Chef : public Employe{
private:
    string service;
public:
    Chef(const string& N, const string& P, const string& D, int S, const string& ser): Employe(N, P, D, S),service(ser){}
    string get_service(){
    return service;}
    void set_service(const string& ser){
        service=ser;
    }
  void afficher() const override{
      Employe::afficher();
  cout<< "service:" << service <<endl;
}
};
class Directeur : public Chef{
private:
    string societe;
public:
    Directeur(const string& N, const string& P, const string& D, int S, const string& ser, const string& soc): Chef(N, P, D, S,ser),societe(soc){}
    string get_societe(){
    return societe;}
    void set_societe(const string& soc){
        societe=soc;
    }
  void afficher() const override{
       Chef::afficher();
  cout<< "societe:" << societe <<endl;
}
};
int main()
{
    Personne P( "lero", "sofia", "15/08/1990");
    P.afficher();
    Employe E("soney", "marwa", "20/11/2000", 5000);
    E.afficher();
    Chef C("mert", "ahmed", "01/05/1999", 7000, "cuisinier");
    C.afficher();
    Directeur D("alice", "said", "02/10/2001", 8000, "informatique", "global");
    D.afficher();
    return 0;
}
Ex4 :
#include <iostream>
#include<cmath>

using namespace std;

class vecteur3d{
private:
    float x, y, z;
public:
    vecteur3d(float x=0, float y=0, float z=0):x(x), y(y),z(z){}
    void afficher()const{
    cout<< "(" << x << "," << y << "," << z << ")" <<endl;
    }
   vecteur3d add(const vecteur3d& V2)const{
       vecteur3d somme(x+V2.x, y+V2.y, z+V2.z);
       return somme;
   }
   float produitscalaire(const vecteur3d& V2)const{
   float multi = (x * V2.x)+(y * V2.y)+(z * V2.z);
   return multi;
   }
   bool coincide(const vecteur3d& V2){
   return (x == V2.x && y == V2.y && z == V2.z);
   }
   float norme() const{
    float nor = sqrt(x*x + y*y + z*z);
    return nor;
   }
   vecteur3d normax(const vecteur3d& V2) const {
    return (norme() >= V2.norme()) ? *this : V2;
}
EX 5 :
#include <iostream>

using namespace std;

class test{
private:
    static int cmp;
public:
    void call(){
        cmp++;
        cout<< "la fonction a été appelé"<<endl;
    }
    static int get_cmp(){
    return cmp;
    }
};
int test::cmp=0;


int main()
{
    test T1;
    test T2;

    T1.call();
    T2.call();
    T2.call();

    cout<< "nombre d'appele est :" << test::get_cmp() <<endl;
    return 0;
}
EX 6 :
#include <iostream>

using namespace std;

class point{
private:
    float x;
    float y;
public:
    point(float X, float Y):x(X), y(Y){}
   void deplace( point& p, float a, float b){
        p.x=p.x + a;
        p.y=p.y + b;
    }
 void afficher()const{
  cout<< "(" << x << "," << y << ")" <<endl;
 }
};

int main()
{
  point p(2.3, 7.9);
  p.afficher();
  p.deplace(p, 3.4, 7.9);
  p.afficher();
    return 0;
}
Ex 7 :
#include <iostream>
#include<vector>


using namespace std;

class pile{
private:
    vector<int>elms;
public:
    pile(){}
void push(int elm){
    elms.push_back(elm);
}
void pop(int elm){
    if(elm.size==0)
        cout<< "la pile est vide" <<endl;
    else
    int lastelm=elms.back()
    elms.pop_back(elm);
    return lastelm;
}
};

  int main{
      pile P1, P2;
      P1.push(15);
      P1.push(20);
      P2.push(16);
      P2.push(19);



  return 0;
  }
EX 11 :
#include <iostream>
#include<vector>
using namespace std;
class Traitement{
    public:
   void Initialise(){
        vector<int>entiers;
        int number ;
        while (entiers.size() < 15){
                cout << "entrer un entier" <<endl;
                cin >> number;
            if((number % 2) == 0 && (number != 0) ){
          entiers.push_back(number);
          }   
        else 
        cout << "la valeur que vous avez entre n'est pas valable" << endl;
        }
    }
     void show( const vector<int>& entiers ,int i){
        if (i>entiers.size()){
                return;
        }
        cout<<"les nombre :";
        cout << " " << entiers[i]<< endl;
        show ( entiers , i+1 ) ;
    }
    friend double moyenne(Traitement &);
   
}; 

    double moyenne(Traitement &T){
        if(T.entiers.empty()){
            return 0.0;
        }   
         double somme=0;
         int i=0;
       while( i < t.entiers.size() ){
         somme = somme+t.entiers[i];
          i++;
       }
              return somme/t.entiers.size();
        }

