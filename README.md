# c++-Banking-deposit-

# this program creates two bank accounts with a balance and does random deposits and withdrawls while accounting for interests gained over 30 days

//sample code

#include <iostream>
#include <ctime>
#include <cstdlib>
#include "account.h"
#include "checking.h"
#include "savings.h"



void callSavings();
void callChecking();

using namespace std;

int Account::counter = 0;

int main()
{
	//to seed
	srand((unsigned)time(NULL));


	//to lable the account type
	cout << "----------------------------------------------------------------------------------------------\n";
	cout << "                                           Savings Account                                    \n";
	cout << "----------------------------------------------------------------------------------------------\n";

	callSavings();//function call to display savings
	
				  //to lable the account type
	cout << "---------------------------------------------------------------------------------------------------" << endl;
	cout << "                                       Checking Account                                            " << endl;
	cout << "---------------------------------------------------------------------------------------------------" << endl;

	callChecking();// function call to display checking

	cout << endl;// to create space
	//display accounts created
	cout << "Number of accounts created: " << Account::counter << endl;

	return 0;
}


void callSavings()
{
	Savings* a = new Savings;

	for (int i = 1; i < 31; i++)
	{
		cout << "\nDay " << i << " : " << endl;
		if (i % 2 == 0)
		{
			double amount = (rand()%1000 + 1 - 1)+1;
			a->set_deposit(amount);
			a->set_dailyInterest();
		}

		else
		{
			double amount2 = (rand() % 1000 + 1 - 1) + 1;
			a->set_withdraw(amount2);
			a->set_dailyInterest();
		}
		if (i == 30)
		{
			cout << endl;
			cout << "balance for the month: $" << a->savingsBalance << endl;
		}
	}
	delete  a;
}

void callChecking()
{
	Checking* c;
	c = new Checking;

	

	for (int i = 1; i < 31; i++)
	{
		cout << "\nDay " << i << " : " << endl;
		if (i % 2 == 0)
		{
			double amount = (rand() % 1000 + 1 - 1) + 1;
			c->set_deposit(amount);
			c->set_monthlyInterest();
		}
		else
		{
			double amount = (rand() % 1000 + 1 - 1) + 1;
			c->set_withdraw(amount);
			c->set_monthlyInterest();
		}

		if (i == 30)
		{
			cout << endl;
			cout << "balance for the month: $" << c->get_checkingBal() << endl;
		}
		
	}
	
	delete c;
	//c = NULL;

}
