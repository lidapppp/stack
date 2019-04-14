# stack
membuat stack dengan konsep linked list
#include <iostream>
#define MAX_STACK_SIZE 10

using namespace std;

struct Element{
	int data;
	int top;
	Element *next;
};

class myStack{
	private:
	Element tumpuk;
	Element *head = NULL;
	
	public:
	void setawal(){
		tumpuk.top = -1;
	}
	
	bool isEmpty(){
        if(tumpuk.top == -1){
			return 1;
		}else{
			return 0;
		}
    }
    
	bool isFull(){
        if(tumpuk.top == MAX_STACK_SIZE-1){
			return 1;
		}else{
			return 0;
		}
    }
    
    void push(int input){
		if(isFull()){
			cout << "Stack Penuh";
		}else{
			Element *tmp = new Element;
			tmp->data = input;
			tmp->next=NULL;
			if(isEmpty())
			{
				head=tmp;
				head->next=NULL;
			}else{
				tmp->next=head;
				head=tmp;
			}
			
			tumpuk.top++;
		}
	}
	
	void pop(){
		if (isEmpty()){
			cout<<"\nTumpukan Kosong\n";
		}else{
			Element *tmp = new Element;
			tmp = head;
			head = head->next;
			delete tmp;
			tumpuk.top--;
		}	
	}
		
	void getTop(){
		if(isEmpty()){
			cout << "Stack Kosong";
		}else{
			cout << head->data;
		}
	}
	
	void print(){
		if(isEmpty()){
			cout << "Stack Kosong" << endl;
		}else{
			cout << "Isi Stack: " << endl;
			Element *tmp = new Element;
			tmp = head;
			while(tmp!=NULL)
			{
				cout<<tmp->data<<endl<<"  ";
				tmp=tmp->next;
			}
		}
	}
};

int nama_menu();

int main(){
	myStack obj;
	int menu,val;
	obj.setawal();
	do{
		menu = nama_menu();
		switch(menu){
			case 1:
					cout << "Masukan Angka : ";cin>>val;
					obj.push(val);
					cin.ignore();
					cin.get();
					break;
			case 2:
					if(obj.isEmpty()){
						cout << "Stack Kosong" << endl;
					}else{
						cout << "Angka ";obj.getTop(); cout << " akan dihapus";
						cin.get();
						obj.pop();
					}
					break;
			case 3:
					if(obj.isEmpty()){
						cout << "Stack Kosong" << endl;
					}else{
						cout << "Elemen Paling Atas adalah ";obj.getTop();
						cin.get();
					}
					break;
			case 4:
					obj.print();
					cin.get();
					break;
			case 5:
					exit(0);
			default:
					cout <<"\t\nPilihan tidak ada, silahkan pilih 1-5";
					cin.get();
					break;
		}

	}while (menu != 5);
		cin.get();
		return 0;
}

int nama_menu(){
	cout<<"M.Fadhil.Azhari - 1817051062"<<endl<<endl<<endl;
	cout<<"\t\t     MODIFIKSI STACK DENGAN KONSEP LINKED LIST"<<endl<<endl;
	int menu;
	cout << "Pilih menu : "<<endl<<endl;
	cout << "1. Operasi push"<<endl;
	cout << "2. Operasi pop"<<endl;
	cout << "3. Get Top"<<endl;
	cout << "4. Cetak stack "<<endl;
	cout << "5. Keluar"<<endl<<endl;
	cout << "Pilihan : "; cin >> menu;
	cin.ignore();
	system("clear");
	return menu;
}


