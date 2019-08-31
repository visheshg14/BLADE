#include <iostream.h>
#include<fstream.h>
#include<conio.h>
#include<stdio.h>
#include<stdlib.h>

class product
{
	 int pno;
	 char name[50];
	 float price,qty,tax,dis,nop,sale;

	 public:
				void create_product()
				{
					 cout<<endl<<"Please enter the product number of the product :";
					 cin>>pno;
					 cout<<"Please enter the name of the product :";
					 gets(name);
					 cout<<"Enter the price of the product :";
					 cin>>price;
					 cout<<"Please enter the discount(%) :";
					 cin>>dis;
                cout<<"Please enter the Number of Pieces avaliable :";
					 cin>>nop;
                cout<<"Please enter the Number of Pieces sold :";
					 cin>>sale;

				}

				void show_product()
				{
					 cout<<endl<<"The product number of the product :"<<pno;
					 cout<<"\nThe name of the product :";
					 puts(name);
					 cout<<"The price of the product :"<<price;
					 cout<<"\nDiscount :"<<dis<<"%";
                cout<<"\nNumber of Pieces left : "<<nop;
                cout<<"\nNumber of Pieces sold :"<<sale;
				}

            void incsale(int n)
            {
            	sale+=n;
            }

            void lnop(int n)
            {
            	nop-=n;
            }

				int retpno()
				{
					 return pno;
				}

            int retnop()
				{
					 return nop;
				}

            int retsale()
				{
					 return sale;
				}

				float retprice()
				{
					 return price;
				}

				char* retname()
				{
					 return name;
				}

				int retdis()
				{
					 return dis;
				}
};

//GLOBAL DECLERATION FOR STREAM OBJECT



fstream fp;
product pr;


void write_product()
{
	 fp.open("store.dat",ios::out|ios::app|ios::in);
	 pr.create_product();
	 fp.write((char*)&pr,sizeof(product));
	 fp.close();
	 cout<<endl<<endl<<"The product has been created";
	 getch();
}

void display_all()
{
    clrscr();
	 cout<<endl<<endl<<"\t\tDISPLAY ALL RECORDS!!!!"<<endl<<endl;
	 fp.open("store.dat",ios::in|ios::out|ios::binary);
	 while(fp)
	 {
		  fp.read((char*)&pr,sizeof(pr));
		  if(fp.eof())
				break;
		  pr.show_product();
		  cout<<endl;
	 }
	 fp.close();
	 getch();
}

void display_sp()
{
	 int n,flag=0;
	 cout<<"\n\nPlease enter the product number : ";
	 cin>>n;
	 fp.open("store.dat",ios::in|ios::out|ios::binary);
	 while(flag!=1)
	 {
		 fp.read((char*)&pr,sizeof(pr));
		  if((pr.retpno()==n)&&(fp.eof()))
		  {      clrscr();
            	pr.show_product();
					break;
				//flag=1;

		  }

	 }
	 fp.close();
	// if(flag==0)
	//	cout<<endl<<"Record does not exist";
}

void modify_product()
{
	 int no,found=0;
	 cout<<endl<<endl<<"\tTo modify";
	 cout<<endl<<endl<<"\nPlease enter the product number : ";
	 cin>>no;
	 fp.open("store.dat",ios::in|ios::out);
	 fp.read((char*)&pr,sizeof(product));
	 while((fp)&&(found==0))
	 {
		  if(pr.retpno()==no)
		  {
				pr.show_product();
				cout<<endl<<"Please enter the new details of the product"<<endl;
				pr.create_product();
				int pos=(-1*sizeof(pr));
				fp.seekp(pos,ios::cur);
				fp.write((char*)&pr, sizeof(product));
				cout<<endl<<endl<<"\t Record Updated";
				found=1;
		  }
		  fp.read((char*)&pr,sizeof(product));
	 }
	 fp.close();
	 if(found==0)
		  cout<<endl<<endl<<"Record not found";
}

void delete_product()
{
	 int no;
	 cout<<endl<<endl<<endl<<"\tDelete records";
	 cout<<endl<<endl<<"Please enter the product number of the product you want to delete : ";
	 cin>>no;
	 fp.open("store.dat",ios::in|ios::out);
	 fstream fp2;
	 fp.read((char*)&pr,sizeof(product));
	 fp2.open("temp.dat",ios::out);
	 while(!fp.eof())
	 {
		  if(pr.retpno()!=no)
				fp2.write((char*)&pr,sizeof(product));
				fp.read((char*)&pr,sizeof(product));
	 }
	 fp2.close();
	 fp.close();
	 remove("store.dat");
	 rename("temp.dat","store.dat");
	 cout<<"The product has been deleted ";
}

void menu1()
{


	 fp.open("store.dat",ios::in|ios::binary|ios::out);
	 if(!fp)
	 {
		  cout<<"ERROR file could not be opened"<<endl<<endl<<"Go to admin menu to create file";
		  cout<<"Program is closing";
		  exit(0);
	 }
	 cout<<"\n\n\tProduct Menu\n\n";
	 cout<<"======================================";
	 cout<<"\nP.NO\t\tNAME\t\tPRICE\n";
	 cout<<"======================================";

	 while(fp)
	 {
		  fp.read((char*)&pr,sizeof(pr));
		  if(fp.eof())
				break;
		  cout<<endl<<pr.retpno()<<"\t\t"<<pr.retname()<<"\t\t"<<pr.retprice()<<endl;
	 }
	 fp.close();
	 getch();
}

void menu()
{


	 fp.open("store.dat",ios::in|ios::binary|ios::out);
	 if(!fp)
	 {
		  cout<<"ERROR file could not be opened"<<endl<<endl<<"Go to admin menu to create file";
		  cout<<"Program is closing";
		  exit(0);
	 }
	 cout<<"\n\n\tProduct Menu\n\n";
	 cout<<"=================================================================================================================";
	 cout<<"\nP.NO\t\tNAME\t\tPRICE\t\tNUMBER OF PIECES LEFT\t\tNUMBER OF PIECES SOLD\n";
	 cout<<"=================================================================================================================";

	 while(fp)
	 {
		  fp.read((char*)&pr,sizeof(pr));
		  if(fp.eof())
				break;
		  cout<<endl<<pr.retpno()<<"\t\t"<<pr.retname()<<"\t\t"<<pr.retprice()<<"\t\t\t"<<pr.retnop()<<"\t\t\t"<<pr.retsale()<<endl;
	 }
	 fp.close();
	 getch();
}


class invoice
{

};

void place_order()
{
	 int order_arr[50],quan[50],c=0;
    long ptr=sizeof(product);
	 float amt,damt,total=0;
	 char ch='Y';
	 menu1();
	 cout<<"\n===================";
	 cout<<"\nPLACE YOUR ORDER";
	 cout<<"\n===================\n";
	 do{
		  cout<<"\n\nEnter the product number of the product : ";
		  cin>>order_arr[c];
		  cout<<"\nQuantity in number : ";
		  cin>>quan[c];
		  c++;
		  cout<<"\nDo you want to order another product ?(y/n)";
		  cin>>ch;
				}while(ch=='y'||ch=='Y');
		  cout<<"Thank you";
		  cout<<"\n                INVOICE\n";
		  cout<<"\nPr No.\tPr Name\tQuantity\tPrice\tAmount\tAmount after discount \n";
		  for(int x=0;x<=c;x++)
		  {
				fp.open("store.dat",ios::in|ios::out|ios::binary);
				fp.read((char*)&pr,sizeof(product));
				cout<<endl;
				while(!fp.eof())
				{
					 if(pr.retpno()==order_arr[x])
					 {
						  amt=pr.retprice()*quan[x];
						  damt=amt-(amt*pr.retdis()/100);
						  cout<<"\n"<<order_arr[x]<<"\t"<<pr.retname()<<"\t"<<quan[x]<<"\t\t"<<pr.retprice()<<"\t"<<amt<<"\t\t"<<damt;
						  total+=damt;
                    fp.seekp(-ptr,ios::cur);
                    		pr.incsale(quan[x]);
                        pr.lnop(quan[x]);
                        fp.write((char*)&pr,sizeof(product));

					 }
					 fp.read((char*)&pr,sizeof(product));
					 if(fp.eof())
						  break;

				}
				fp.close();
		  }
		  cout<<"\n\n\t\t\t\tTOTAL="<<total;
}


void admin_menu()
{
	 char ch2;
    int c=0;
	 char pass[6];
 	 char r[6] = "booyha";
 	 int p;
		 cout<<"Password: ";
    for (int i=0;i<6;i++)
    {
  		pass[i] = getch();
  		cout<<"*";
    }
 	 for (int j=0;j<6;j++)
  	 {
    	if (pass[j] == r[j])
    	c = c+1;
 	 }

	if (c == 6)
	{
	 cout<<"\n\n\n\tADMIN MENU";
	 cout<<"\n\n\t1.CREATE PRODUCT";
	 cout<<"\n\n\t2.DISPLAY ALL PRODUCTS";
	 cout<<"\n\n\t3.QUERY";
	 cout<<"\n\n\t4.MODIFY PRODUCT";
	 cout<<"\n\n\t5.DELETE PRODUCT";
	 cout<<"\n\n\t6.VIEW PRODUCT MENU";
    cout<<"\n\n\t7.VIEW MONTHLY SALES";
	 cout<<"\n\n\t8.BACK TO MAIN MENU";
	 cout<<"\n\n\tPlease enter your choice(1-8) : ";
	 cin>>ch2;
	 switch(ch2)
	 {
		  case '1':write_product();
		  break;
		  case '2':display_all();
		  break;
		  case '3':display_sp();
		  break;
		  case '4':modify_product();
		  break;
		  case '5':delete_product();
		  break;
		  case '6': {clrscr();
						menu(); }
		  break;
        case '7':break;
		  break;
		  case '8':break;
		  default:cout<<"\a";

	 }}
    else
    {
     	cout<<"\n\tWRONG PASSWORD";
      getch();
    }
}

void main()
{
	 char ch;
 	 clrscr();

	 do{
         clrscr();
				cout<<"\n\t\tMAIN MENU";
				cout<<"\n1.CUSTOMER";
				cout<<"\n2.ADMINISTRATOR";
				cout<<"\n3.EXIT";
				cout<<"\nPlease select your option(1-3) : ";
				ch=getche();
				switch(ch)
				{
					 case '1':   clrscr();
									 place_order();
									 getch();
								break;
					 case '2':  clrscr();
									 admin_menu();
								break;
					 case '3':exit(0);
					 default:cout<<"\a";
				}

	 }while(ch!='3');}
