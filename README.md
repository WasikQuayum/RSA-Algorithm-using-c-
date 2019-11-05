# RSA-Algorithm-using-c-
#include<iostream>
#include<math.h>
using namespace std;
int gcd(int a, int b) {
   int t;
   while(1) {
      t= a%b;
      if(t==0)
      return b;
      a = b;
      b= t;
   }
}
int main()
{
    int p,q,n,e,f,i,j,phin,message;
    double trc,c,m,d1,d;

    int count=0;
    cout<<"Enter message"<<endl;
    cin>>message;

    cout<<"Enter 1st number"<<endl;
    cin>>p;
    cin>>q;

    for(i=2,j=2;i<=p/2,j<=q/2;i++,j++)
    {
        if(p%2==0&&q%2==0)
        {
            count++;
            break;
        }
    }
    if(count ==0)
    {
        n=p*q;
        cout<<"n: "<<n<<endl;
        phin=(p-1)*(q-1);
        cout<<"Phi(n): "<<phin<<endl;
        cout<<"Enter e for encryption"<<endl;
        cin>>e;
        while(e<phin) {
       trc= gcd(e,phin);
      if(trc==1)
         break;
      else
        e++;

}
    d1=1/e;
    d=fmod(d1,phin);
    c = pow(message,e); //encrypt the message
    m = pow(c,d);
   c=fmod(c,n);
   m=fmod(m,n);

   //cout<<"\n"<<"d = "<<d;
   cout<<"\n"<<"Encrypted message = "<<c;
   //cout<<"\n"<<"Decrypted message = "<<m;

   }

    else{
        cout<<"INVALID"<<endl;
    }
}
