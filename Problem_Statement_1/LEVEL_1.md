#include<stdio.h>
#include<string.h>
#include<ctype.h>

void Encode(char Message[],int Shift) {
 for(int i=0;Message[i]!='\0';i++)  {
 char m = Message[i];
 if(isalpha(m)) {
  char base = isupper(m)?'A':'a';
  Message[i]=(m-base+Shift+26)%26+base;
  }
 }
}
void Decode(char Message[],int Shift) {
 for(int i=0;Message[i]!='\0';i++)  {
 char m = Message[i];
 if(isalpha(m)) {
  char base = isupper(m)?'A':'a';
  Message[i]=(m-base-Shift+26)%26+base;
  }
 }
}
int main() {
 char Message[1000];    
 int Choice,Shift;

 printf("\nEnter the Message : ");
 scanf(" %[^\n]",Message);

 printf("\nEnter the Shift value : ");
 scanf("%d",&Shift);
 
 printf("Choose an option:\n1.Encode\n2.Decode\nEnter Choice: ");
 scanf("%d",&Choice);

 if(Choice==1) {
  Encode(Message,Shift);  
  printf("Encoded Message:%s\n",Message);
 } else if(Choice==2) {
  Decode(Message,Shift);  
  printf("Decoded Message:%s\n",Message);
 }
  else {
    printf("Invalid choice.\n");
  }
}
