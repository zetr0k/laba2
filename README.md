# laba2
#include<iostream>
#include<conio.h>
using namespace std;

//Структура для элемента односвязного списка
struct link
{
	double data;
	link* next;
};

//Класс, реализующий односвязный список
class linklist
{
	
private:
	link* head;
public:
	linklist()
	{
		head=NULL;
	}
	//Метод для добавления нового элемента в список
	void additem(double temp)
	{
		link*  newlink=new link;
		newlink->data=temp;
		newlink->next=head;
		head=newlink;
		this->sort();
	}
	void print(link* t)
	{
		cout<<"\n\n   "<<t->data;
	}
	//Метод для вывода списка на экран
	void show()
	{
		system ("cls");
		if (head==NULL)
		{
			cout<<"\n\n   List is empty";
		}
		else
		{
			link* temp=head;
			do
			{
				print(temp);
				temp=temp->next;
			}while(temp!=NULL);
		}
		getch();
	}
	//Метод для добавления элементов одного списка в другой
	void addSpis(linklist &tmp)
	{
		if (head==NULL)
		{
			exit;
		}
		else
		{
			link* temp=head;
			do
			{
				tmp.additem(temp->data);
				temp=temp->next;
			}while(temp!=NULL);
		}
		sort();
	}
	//Поменять местами два элемента списка(для метода сортировки)
	void swap(link* one,link* two)
	{
		double temp;
		temp=one->data;
		one->data=two->data;
		two->data=temp;
	}
	//Метод сортировки по невозрастанию
	void sort()
	{
		if (head==NULL)
		{
			return;
		}
		else if(head->next==NULL)
		{
			return;
		}
		bool b;
		link* one;
		link* two;

		do
		{
			b=true;
			one=head;
			two=head->next;
			while(two!=NULL)
			{
				if (one->data < two->data)
				{
					swap(one,two);
					b==false;
				}
				one=two;
				two=two->next;
			}

		}while (b==false);
		
	}
};



void main()
{
	{
		setlocale(LC_ALL, "RUS");
	}
	linklist spis1;
	linklist spis2;
	linklist spis3;
	char ch;

	do
	{
		//Меню для выбора действия пользователя
		system("cls");
		cout<<"\n\n\n     1 - Внесение элемента в первый список";
		cout<<"\n\n     2 - Внесение элемента во второй список";
		cout<<"\n\n     3 - Показать первый список";
		cout<<"\n\n     4 - Показать второй список";
		cout<<"\n\n     5 - Показать оба списка";
		cout<<"\n\n\n     Q - ВЫХОД";
		ch=getch();
		switch(ch)
		{
			case '1':
				{
					system("cls");
					double n=0;
					cout<<"\nВведите новое число: ";
					cin>>n;
					spis1.additem(n);
					break;
				}
			case '2':
				{
					system("cls");
					double n=0;
					cout<<"\nВведите новое число: ";
					cin>>n;
					spis2.additem(n);
					break;
				}
			case '3':
				{
					spis1.show();
					break;
				}
			case '4':
				{
					spis2.show();

					break;
				}
			case '5':
				{
					spis1.addSpis(spis3);
					spis2.addSpis(spis3);

					spis3.show();
					break;
				}
			default:;
		}



	}while ((ch != 'Q') && (ch != 'q'));
	
}
