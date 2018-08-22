# Shallow-Deep-copy
/******************************************************************************

                              Online C++ Compiler.
               Code, Compile, Run and Debug C++ program online.
Write your code in this editor and press "Run" button to compile and execute it.

*******************************************************************************/

#include <iostream>
#include <string.h>
using namespace std;
//shallow copy and deep copy
class pay{
    public:
    pay(char na[45]="");
    pay(pay &);
    pay & operator =(const pay &);
    char *name;
    ~pay();
    
};
pay::~pay(){
   delete [] name;
}
pay::pay(char nam[45]){
    name=new char[strlen(nam)];
   strcpy(name,nam);
}

pay &pay::operator=(const pay &s){
    //cout<<"assignment";
    if(this==&s)
    return *this;
   delete [] name;
    if(s.name){
        name=new char[strlen(s.name)];
        strcpy(name, s.name);
    }
    else
    name=NULL;
    cout<<"assignment";
    return *this;

}
pay::pay(pay &s){
    //name=new char[strlen(s.name)];
    strcpy(name,s.name);
    cout<<"copy constructure"<<s.name;
}
int main(){
    pay p((char*)"avij");
    //pay s(p);
    pay s;
    s=p;
    cout<<p.name<<s.name;
    return 0;
}
