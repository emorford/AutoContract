
# AutoContract
Cis 230 c++ project
//Automobile final
//Emily Morford
//June 15, 2017

#include <iostream>
using namespace std;
#include <string>
#include <vector> 
#include <iomanip>  // precision , width
const double TAXRATE= .06;

//  check the box and add the following  ----- if needed -std=c++11  //

class Automobile{  //nothing virtual
	protected:
		string make;  
		string model; 
		string color;  
		int year; 
		long int miles; 
		float salesprice; 
		float rentalprice; //daily charge
		float leaseprice; //annual charge
		string trimdetails; //trim and car details
		float citympg; //city mpg
		float hwympg;  //highway mpg
		string VIN;  //vin number
		string engine; //engine type
	
	public:		
		string getMake(){ return make;}				void setMake(string m){ make = m;}		
		string getModel(){ return model;}			void setModel(string mo){ model = mo;}
		void setColor(string c){ color = c;}
		string getColor(){ return color;}
		void setYear(int y){ year = y;}
		int getYear(){ return year;}
		void setMiles(long int mi){ miles = mi;}
		long int getMiles(){ return miles;}		
		void setSalesprice(float s){ salesprice = s;}
		float getSalesprice(){ return salesprice;}		
		void setRentalprice(float r){ rentalprice = r;}
		float getRentalprice(){ return rentalprice;}		
		void setLeaseprice(float l){ leaseprice = l;}
		float getLeaseprice(){ return leaseprice;}
		void setTrimdetails(string t){ trimdetails = t;}
		string getTrimdetails(){ return trimdetails;}
		void setCitympg(float ci){ citympg = ci;}
		float getCitympg(){ return citympg;}		
		void setHwympg(float h){ hwympg = h;}
		float getHwympg(){ return hwympg;}
		void setVin(string v){ VIN = v;}
		string getVin(){ return VIN;}
		void setEngine(string e){ engine = e;}
		string getEngine(){ return engine;}
		void showAutos();
			
};

void Automobile::showAutos(){          //incomplete
	cout
	<<"This will show info about the "<< model << " car. ";	
}


class Person{
	protected:
		string lastname;
		string firstname;
		string id;   //technician id,salesperson id,customer account no.
		string phoneno; 
		string email; //employee email for employees
		string streetaddress; //home address
		string city; //home city
		string state; //home state
		string zip; //home zip
	public:
		string getLastname(){ return lastname;}		void setLastname(string l){ lastname = l;}		
		string getFirstname(){ return firstname;}	void setFirstname(string f){ firstname = f;}

};


class Customer: public Person{
	private:
		//hmm, does a customer need an auto??
		string phoneno2;  //second contact phone number
		string salesperson;	//preferred salesperson
		string dlno;  //drivers license number
		string dlstate; //drivers license state
		long int dlexpire;//drivers license expiration
		int creditscore;
		string insuranceco; //name of car insurance company
	public:
		void showCustomer();
		Customer();

};

Customer::Customer()     //incomplete
{
	lastname="this is the customer constructor";
	
}

void Customer::showCustomer(){          //incomplete
	cout
	<<"This will show info about the "<< lastname << " lastname of the customer. ";	
}


class Salesperson: public Person{
	private:
		int totalsales;  //number of auto sales
		int totalleases; //number of auto leases
		int totalrentals;  //number of auto rentals
		float salary;   //salesperson salary
		string jobdescription;   //job description
		int rating;
		string supervisor;
	public:
		int getTotalsales(){ return totalsales;}				void setTotalsales(int ts){ totalsales = ts;}	
		int getTotalrentals(){ return totalrentals;}			void setTotalrentals(int tr){ totalrentals = tr;}	
		void showSalesperson();
		Salesperson();
		
		//create two constructors??

};

Salesperson::Salesperson()     //incomplete
{
	lastname="this is the salesperson constructor";
	
}

void Salesperson::showSalesperson(){          //incomplete
	cout
	<<"This will show info about the "<< lastname << " lastname of the salesperson. ";	
}

class Technician: public Person{
	private:
		string degree;  //assoc, bachelors, masters
		long int datehired; //date of hire
		long int birthdate; //technician birth date
		float hourlypay; //technician hourly pay
	public:

};

class Contract{
	protected:
		Automobile car;
		Customer cust;
		long int invoiceno;
		long int contractdate; //date of contract
		long int completiondate; // date car is ready for customer
		long int deliverydate; //date customer claims car
		float tax;
		float total;		
	public:
		void setInvoiceno(long int i){ invoiceno = i;}
		long int getInvoiceno(){ return invoiceno;}	
		void setContractdate(long int con){ contractdate = con;}
		long int getContractdate(){ return contractdate;}	
		void setCompletiondate(long int com){ completiondate = com;}
		long int getCompletiondate(){ return completiondate;}	
		void setDeliverydate(long int del){ deliverydate = del;}
		long int getDeliverydate(){ return deliverydate;}		
		void setTax(float t){ tax = t;}
		float getTax(){ return tax;}
		void setTotal(float to){ total = to;}
		float getTotal(){ return total;}
};

class Sales: public Contract{
	private:
		Salesperson seller;
		float monthlypayment; 
		float downpayment;	
		int months;  //no of months to pay off
		long int firstpayment;//date of first payment
	public:
		
		long int getFirstpayment(){ return firstpayment;}	void setFirstpayment(long int fp){ firstpayment = fp;}		
		int getMonths(){ return months;}					void setMonths(int m){ months = m;}				
		float getDownpayment(){ return downpayment;}		void setDownpayment(float dp){ downpayment = dp;}		
		float getMonthlypayment(){ return monthlypayment;}	void setMonthlypayment(float mp){ monthlypayment = mp;}
		
		void calculateAmounts();//
		void showContract();  //
		Sales (Automobile, Customer, Salesperson);   // constructor
		void printContract();  //
		Sales();  //
};
Sales::Sales( ){    //
		invoiceno=0;
		contractdate=12312000; //date of contract
		completiondate=12312000; // date car is ready for customer
		deliverydate=12312000; //date customer claims car
		tax= 0;
		total=0;
		monthlypayment=0;
		downpayment=0;
		months=0;
		firstpayment=0;		
		} 
		
void Sales::printContract(){   //
	cout
	<<"\t\t\tCustomer Name:\t"<< cust.getFirstname() <<" "<<cust.getLastname()
	<<"\t\t\tSalesperson Name:\t"<<seller.getFirstname() <<" "<<seller.getLastname()
	<<" The VIN number is: "<<  car.getVin() <<"\n"<<
	" The car is a : "<< car.getYear() << " " <<car.getColor()<< " " << car.getMake()<< " " << car.getModel()<<" with "<<car.getMiles() <<" miles."<<"\n"<<
	" Salesperson Total sales: " <<  seller.getTotalsales() <<" \n"<<
	" The selling price is $"<< car.getSalesprice() <<" and the downpayment is $"<<downpayment<< ".\n"<<
	" There will be " << months <<"  monthly payments of $"<< monthlypayment <<".\n"<<	
	 "\n\n";
    }
Sales::Sales(Automobile c, Customer cu , Salesperson sa){   //
		car=c;
		cust=cu;
		seller=sa;}
void Sales::showContract(){	  //
 car.showAutos();  
 cust.showCustomer();
 seller.showSalesperson();
   //don't put cout because its in show functions
 
 }
	
void Sales::calculateAmounts(){
	
	tax = car.getSalesprice()*TAXRATE;
	total= car.getSalesprice() + tax;
	monthlypayment = (total-downpayment)/months;
	seller.setTotalsales(seller.getTotalsales()+1);																					///			???????????????	
}
class Rental: public Contract{
	private:
		Salesperson seller;
		int checkouttime; 
		int timedueback;  
		long int datedueback;
		int returntime;  
		long int returndate;
		float mileagelimit;
		float penaltyfee;
		string paymentmethod;
		long int cardnum;
		long int cardexpdate;
		int cardseccode;
	public:		
		
		int getCheckouttime(){ return checkouttime;} 		void setCheckouttime( int ct){ checkouttime = ct;}
		int getTimedueback(){ return timedueback;} 			void setTimedueback( int tb){ timedueback = tb;}
		long int getDatedueback(){ return datedueback;} 	void setDatedueback( long int db){ datedueback = db;}
		int getReturntime(){ return returntime;} 			void setReturntime( int rt){ returntime = rt;}
		long int getReturndate(){ return returndate;} 		void setReturndate( long int rd){ returndate = rd;}		
		float getMileagelimit(){ return mileagelimit;}		void setMileagelimit(float ml){ mileagelimit = ml;}
		float getPenaltyfee(){ return penaltyfee;}			void setPenaltyfee(float pf){ penaltyfee = pf;}
		string getPaymentmethod(){ return paymentmethod;}	void setPaymentmethod(string pm){ paymentmethod = pm;}
		long int getCardnum(){ return cardnum;} 			void setCardnum( long int cn){ cardnum = cn;}
		int getCardseccode(){ return cardseccode;} 			void setCardseccode( int cs){ cardseccode = cs;}
		long int getCardexpdate(){ return cardexpdate;} 	void setCardexpdate( long int cd){ cardexpdate = cd;}
		
		void calculateAmounts();
		void showContract();
		Rental (Automobile, Customer, Salesperson);   // constructor
		void printContract();
		Rental();
};
Rental::Rental( ){
		invoiceno=0;
		contractdate=12312000; //date of contract
		completiondate=12312000; // date car is ready for customer
		deliverydate=12312000; //date customer claims car
		tax= 0;
		total=0;
		checkouttime=0; 
		timedueback=0;   
		datedueback=0; 
		returntime=0;   
		returndate=0; 
		mileagelimit=0; 
		penaltyfee=0; 
		paymentmethod="";
		cardnum=0; 
		cardexpdate=0; 
		cardseccode=0; 
		} 
		
void Rental::printContract(){
	cout
	<<"\t\t\tCustomer Name:\t"<< cust.getFirstname() <<" "<<cust.getLastname()
	<<"\t\t\tSalesperson Name:\t"<<seller.getFirstname() <<" "<<seller.getLastname()
	<<" The VIN number is: "<<  car.getVin() <<"\n"<<
	" The car is a : "<< car.getYear() << " " <<car.getColor()<< " " << car.getMake()<< " " << car.getModel()<<" with "<<car.getMiles() <<" miles."<<"\n"<<
	" Salesperson Total rentals: " <<  seller.getTotalrentals() <<" \n"<<
	" The total rental price is $"<< car.getRentalprice() <<"\n"<<
	" The total for " << returndate-deliverydate+1 <<"  days is $"<< total <<"\n"<<
	
	
	 "\n\n";
    }
Rental::Rental(Automobile c, Customer cu , Salesperson sa){
		car=c;
		cust=cu;
		seller=sa;}
		
void Rental::showContract(){	
 car.showAutos();  
 cust.showCustomer();
 seller.showSalesperson();
   //doesn't put cout because its in show functions
 
 }
	
void Rental::calculateAmounts(){
	
	tax = car.getRentalprice()*TAXRATE;
	total= (car.getRentalprice() + tax)*(returndate-deliverydate+1);
	seller.setTotalrentals(seller.getTotalrentals()+1);																					///			???????????????
	
}
void displayMenu(int &);  

//void getSalescontract()

int main ()

{
	string make, model, color, trimdetails, VIN, engine;
	int year;
	long int miles;
	float rentalprice, leaseprice, salesprice, citympg, hwympg;

	int choice; 
	
	
	Automobile myAutomobile;
//	myAutomobile.displayAutoForm();

//	myAutomobile.displayAutos();
	
	vector <Automobile> automobiles;
	
	
	do
{
	//function call to choose menu option
	displayMenu(choice);	
	switch(choice)
{	
	case 1: 
		cout<<"AUTO FORM"<<endl;
	//cout<<"Please enter make of car # " << make<< "\t";
	//	getline(cin, make);
	cin.ignore(1000, '\n');
	
	cout<<"Please enter the MAKE : \t";						getline (cin, make);				myAutomobile.setMake(make);
	cout<<"Please enter the MODEL :\t";						getline (cin, model);				myAutomobile.setModel(model);
	cout<<"Please enter the COLOR :\t";						getline (cin, color);				myAutomobile.setColor(color);
	cout<<"Please enter the YEAR :\t";						cin >> year;						myAutomobile.setYear(year);
	cout<<"Please enter the MILES : \t";					cin >> miles;						myAutomobile.setMiles(miles);
		
	cin.ignore(1000, '\n');
		
	cout<<"Please enter the TRIM DETAILS :\t";				getline (cin, trimdetails);			myAutomobile.setTrimdetails(trimdetails);
	cout<<"Please enter the VIN :\t";						getline (cin, VIN);					myAutomobile.setVin(VIN);
	cout<<"Please enter the Engine :\t";					getline (cin, engine);				myAutomobile.setEngine(engine);
	cout<<"Please enter the SALES PRICE :\t";				cin >> salesprice;					myAutomobile.setSalesprice(salesprice);
	cout<<"Please enter the DAILY RENTAL PRICE :\t";		cin >> rentalprice;					myAutomobile.setRentalprice(rentalprice);
	cout<<"Please enter the MONTHLY LEASE PRICE :\t";		cin >> leaseprice;					myAutomobile.setLeaseprice(leaseprice);
	cout<<"Please enter the CITY MILEAGE:\t";				cin >> citympg;						myAutomobile.setCitympg(citympg);
	cout<<"Please enter the HIGHWAY MILEAGE :\t";			cin >> hwympg;						myAutomobile.setHwympg(hwympg);
	
	cout<<"\n\n";
	cin.ignore(1000, '\n');
	automobiles.push_back(myAutomobile);
	
		break;
	
	case 2:  
	//this needs to do go to a function-send the vector
	
	cout<<"READY TO CONSTRUCT SALES CONTRACT:\n\n";	
cout<<"Please enter the VIN of car that will be purchased\t";						getline (cin, VIN);					

	
	int x;
	for (int x=0; x<automobiles.size(); ++x)      
		{
			if ( automobiles.at(x).getVin()== VIN )
			{
			cout<< "BINGO:  "<<VIN<<endl;
			}	
		} 
		 cout<<"x:"<< x;
		Automobile myAuto;
		myAuto=automobiles.at(x);
		myAuto.showAutos();
		
		
		
		
//	Customer myCustomer;
//	Salesperson mySalesperson;
	
//	Sales myContract ( myAuto, myCustomer, mySalesperson);
//myContract calculate
//myContract showContract
//myContract printContract
//myContract showContract
		break;
	case 3:   
		cout<<"DO nothing for case3 yet\t";
		break;
	case 4:   
		cout<<"DO nothing for case4 yet\t";
		break;
	case 5:   
			for (Automobile x : automobiles)      
		{
			cout<< x.getVin();
			cout<<"\n\n"<<endl;
		} 
		break;	

	case 0:
		cout<<"\t\t\tExiting the menu!!"<<endl;
		break;
}
		
}
while ((choice >0)&&(choice <6));
	
	return 0;
	
	
}

void displayMenu(int& choice)
{
cout <<"\n\t\t\tPlease select from the menu:\n" <<endl;
cout<< "\t\t\t1: Enter AUTOMOBILE data:\n"<<endl;
cout<< "\t\t\t2: Enter SALES CONTRACT data:\n"<<endl;
cout<< "\t\t\t3: Enter RENTAL CONTRACT data:\n"<<endl;
cout<< "\t\t\t4: Enter LEASE CONTRACT data:\n"<<endl;
cout<< "\t\t\t5: Display VIN numbers:\n"<<endl;
cout<< "\t\t\t0: Exit- NO data to be entered at this time\n"<<endl;
cout<< "\t\t\tPlease enter your choice:\n"<<endl;
cin>>choice;

if ( (choice < 0)||(choice >5)){
				do 
					{
					cout<< "Please enter 0,1,2,3,4, or 5"<<endl;
					cin>>choice;	
					}
			while ((choice < 0)||(choice >5));}
}
