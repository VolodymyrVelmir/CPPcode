<
#include <iostream>
#include <string>
using namespace std;

class Animal {
public:
	Animal(string name) {
		this->name = name;
	};
  
	string getName() const { return  name;}
	string getSpec() const { return  Type; }
	virtual int leng()const = 0;
	virtual string lvoice()const = 0;

protected:
	string Type, name;
	friend ostream& operator <<(ostream &s, const  Animal &k) {
		s << k.getSpec() << " " << k.getName()  << ", legs " << k.leng() << ", voice: " << k.lvoice();
		return s;
	}
  
	friend ostream& operator <<(ostream &s, const Animal *k) {
		s << k->getSpec() << " " << k->getName() << ", legs " << k->leng() << ", voice: " << k->lvoice();
		return s;
	}
};

class Cat :public Animal {
public:
	Cat(string name) :Animal(name) { Type = "Cat"; }
		virtual int leng()const { return 4; }
		virtual string lvoice()const { return "meow"; };
};

class Snake :public Animal {
public:
	Snake(string name) :Animal(name) { Type = "Snake"; }
	virtual int leng()const { return 0; }
	virtual string lvoice()const { return "sss"; };
};

int main34() {
	Cat cat1("Oliwer"), cat2("shopi");
	Snake snak1("wife");
	Animal* mm[] = {&cat1,&cat2,&snak1};
	for (const auto& e : mm)cout << *e << endl;
	cout  << endl;
	for (const auto& e : mm)cout << e << endl;
	return 0;
}
>
