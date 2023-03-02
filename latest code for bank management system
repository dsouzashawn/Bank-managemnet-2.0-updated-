#include<stdio.h>
#include<stdlib.h>     // account number--> 0 to 100
#include<time.h>
#include<string.h>
#include<unistd.h>
#include<ctype.h>
#include<conio.h>


int person=0;
int b,j=0,a=0;

int choice;
int select;

int verifyaccountnum;
char names[30];
int ccountnumber;
int total_balance=0;

int dip_amt;
int with_amt;
int trans_amt;
int ac;
int count;


void divider();
void bank();
void entermenu();
void create();
void login();
void mainmenu();
void deposit_money();
void withdraw_money();
void transfer_money();
void account_details();
void transaction_details();
void last_details();


struct user
{
    char name[30],surname[30];
    int dobdate,dobmonth,dobyear,age;
    char phonenumber[30];
    char address[100];
    char aadhar[30],pan[30];
    char acc_type[20];
    int bankdep;
    int useraccountnum;
}users[101];



void main()
{
    bank();
}



void bank()
{
    while(1)
    {
        entermenu();
        printf("\n\nPlease enter your choice:-");
        scanf("%d",&choice);

        if(choice==1)
        {
            create();
        }

        else if(choice==2)
        {
            login();

        }
    }
}




void divider()
{
    for(int d=0;d<50;d++)
    {
        printf("-");
    }
}



void entermenu()
{
     divider();
     printf("\n\tWELCOME TO NITTE BANKING SYSTEM\n");

     divider();
     printf("\n1.Create an account");
     printf("\n2.Login to your account");
}



void create()
{
    printf("\nCreate account\n");
    divider();

    printf("\nEnter your name:-");
    scanf("%s",&users[j].name);

    printf("\nEnter your surname:-");
    scanf("%s",&users[j].surname);

    printf("\nEnter date of birth:-\n");
    printf("Date: ");
    scanf("%d",&users[j].dobdate);
    printf("Month: ");
    scanf("%d",&users[j].dobmonth);
    printf("Year: ");
    scanf("%d",&users[j].dobyear);

    printf("\nEnter your phonenumber:-");
    scanf("%s",&users[j].phonenumber);

    printf("\nEnter your address:-");
    scanf("%s",&users[j].address);

    printf("\nEnter your aadhar number:-");
    scanf("%s",&users[j].aadhar);

    printf("\nEnter your pan number:-");
    scanf("%s",&users[j].pan);

    printf("\nAccount type (Select 1 for savings and 2 for current): ");
    scanf("%s",&users[j].acc_type);

    label:
    printf("\nInitial bank deposition:-");
    printf("\nPlease note a minimum of Rs500 or above must be deposited in the bank account:-");
    printf("\nPlease enter the amount:-");
    scanf("%d",&users[j].bankdep);
    if(users[j].bankdep<500)
    {
        goto label;
    }

    printf("\nAccount created successfully!!!");
    users[j].useraccountnum = a;
    printf("\nAccount number alloted is:- %d\n\n",a);
    a++;
    j++;
    person++;
}




void login()
{

     retry:
     verify:
     per:

     printf("\nEnter your account number:- ");
     scanf("%d",&verifyaccountnum);
     if(verifyaccountnum<0||verifyaccountnum>100)
     {
         goto verify;
     }

     b = verifyaccountnum;

     if(b>=person)
     {
         printf("\nAccount is not yet created. ");
         goto per;
     }

      strcpy(names,users[b].name);
      ccountnumber = users[b].useraccountnum;
      total_balance = users[b].bankdep;



     if(total_balance==0)
     {
         printf("\nWrong account number");
         goto retry;
     }


     while(1)
     {
          mainmenu();
          printf("\nSelect your choice:-");
          scanf("%d",&select);
          switch(select)
                {
                    case 1:
                        deposit_money();
                        break;

                    case 2:
                        withdraw_money();
                        break;

                    case 3:
                        transfer_money();
                        break;

                    case 4:
                        account_details();
                        break;

                    case 5:
                        transaction_details();
                        break;

                    case 6:
                        last_details();
                        exit(0);

                    default:
                        printf("*****INVALID CHOICE*****");
                        break;
                }
      }
}




void mainmenu()
{
    printf("\n\n");
    divider();
    printf("\n\tMENU\n");

    divider();
    printf("\n1.Deposit Money\n");
    printf("2.Withdraw Money\n");
    printf("3.Transfer Money\n");
    printf("4.Account details\n");
    printf("5.Transaction details\n");
    printf("6.Exit\n");
    divider();
}



void deposit_money()
{

    time_t tm;        //this is used to display current date and time in transaction details function
    time(&tm);
    FILE *fp = fopen("Account.txt","a");    //all the transaction details will be stored in this file
    printf("\n\n*****DEPOSITING MONEY*****\n");
    divider();
    dip:
    printf("\nEnter the amount to be deposited:- ");
    scanf("%d",&dip_amt);
    if(dip_amt<=0)
    {
        printf("\n Error!!! Renter");
        goto dip;
    }

    total_balance += dip_amt;
    printf("*****MONEY DEPOSITED*****\n");
    printf("Current balance : %d\n",total_balance);
    fprintf(fp,"\nRs%d had been deposited to your account\n",dip_amt);
    fprintf(fp,"Date /time of transaction : %s\n",ctime(&tm));
    count++;

    fclose(fp);
    printf("Press any key.....\n");
    getch();

}




void withdraw_money()
{
    time_t tm;
    time(&tm);
    FILE *fp = fopen("Account.txt","a");
    printf("\n\n*****WITHDRAWING MONEY*****\n");
    divider();
    label:
    with:
    printf("\nEnter the amount you want to withdraw:- ");
    scanf("%d",&with_amt);
    if(with_amt<0)
    {
        printf("\nError!!! Renter");
        goto with;
    }

    if((total_balance-with_amt)<500)
    {
        printf("*****Transaction Declined*****\n (A minimum of Rs500 must be kept in the bank)\n");
        goto label;
    }

    else
    {
        total_balance = total_balance - with_amt;
        printf("*****Money withdrawn*****\n");
        printf("Current balance : %d\n",total_balance);
        fprintf(fp,"\nRs%d had been withdrawn from your account \n",with_amt);
        fprintf(fp,"Date /time of transaction : %s\n",ctime(&tm));
        count++;
    }

    fclose(fp);
    printf("Press any key....\n");
    getch();
}



void transfer_money()
{

    time_t tm;
    time(&tm);
    FILE *fp = fopen("Account.txt","a");
    printf("\n\n*****TRANSFERRING MONEY*****\n");
    divider();

    invalid:
    creation:
    printf("\nEnter the account no. in which money has to be transferred:- ");
    scanf("%d",&ac);
    if(ac<0||ac>100)
    {
        printf("Invalid account number!! Renter");
        goto invalid;
    }

    if(ac>=person)
    {
        printf("\nAccount is not yet created. ");
        goto creation;
    }


    transfering:
    trans:
    printf("\nEnter the amount you want to transfer:- ");
    scanf("%d",&trans_amt);
    if(trans_amt<=0)
    {
        printf("\nError!!! Renter");
        goto trans;
    }

    if((total_balance-trans_amt)<500)
    {
        printf("*****Transaction Declined*****\n (Please maintain atleast Rs 500 in bank account)");
        goto transfering;
    }

    else
    {
        users[ac].bankdep = users[ac].bankdep + trans_amt;
        total_balance = total_balance-trans_amt;
        printf("*****Money Transferred*****\n");
        printf("Current balance : %d\n",total_balance);
        fprintf(fp,"\nRs%d had been transferred from your account to %d\n",trans_amt,ac);
        fprintf(fp,"Date /time of transaction : %s\n",ctime(&tm));
        count++;
    }

    fclose(fp);
    printf("Press any key....\n");
    getch();
}




void transaction_details()
{
    FILE *fp;
    fp = fopen("Account.txt","r");
    char c = fgetc(fp);
    if(c==EOF)                  //when no text is present in the file Account.txt
    {
        printf("\n\nTRANSACTION DETAILS\n");
        divider();
        printf("\n*****NO RECENT TRANSACTION*****\n");
    }

    else
    {
        printf("\n\nTRANSACTION DETAILS\n");
        divider();
        printf("\n%d Transactions have been made so far.\n",count);
        while(c!=EOF)
        {
            printf("%c",c);
            c = fgetc(fp);
        }
    }

    printf("\nPress any key......\n");
    getch();
}




void account_details()
{

    printf("\n\nACCOUNT DETAILS\n");
    divider();

    printf("\nName : %s\n",names);
    printf("Account No. : %d\n",ccountnumber);
    printf("Total balance = %d\n",total_balance);
    printf("\n%d Transactions have been made so far.\n",count);
    printf("Press any key....");
    getch();

}



void last_details()
{
    users[ccountnumber].bankdep = total_balance;
    bank();

}
