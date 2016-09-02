# Shunting-Yard
#include <bits/stdc++.h>
using namespace std;
#define S second
#define F first
#define MOD 1000000007
typedef  long long llint;
typedef pair<int,int> pii;

int main()
{



string e;
getline(cin,e);

stack<int> val;
stack<char> oper;

int pres[150] = {0};
pres['(']=1;
pres['+']=2;
pres['-']=2;
pres['*']=4;
pres['/']=4;

for(int i = 0;i < e.size();i++)
{
    if(e[i]==' ') continue;
    if(isdigit(e[i]))
    {
        int curr = 0;
        while(isdigit(e[i]))
        {
            curr = (curr*10) + (e[i] - '0');
            i++;
        }
        val.push(curr);
    }
    if(pres[e[i]]>0)
    {
        if(e[i]=='(')
        {
            oper.push(e[i]);
            continue;
        }
        while(!oper.empty()&&pres[oper.top()]>=pres[e[i]])
        {
            int drugi=val.top();val.pop();
            int prvi=val.top();val.pop();
            int res=0;
            char top=oper.top();oper.pop();
            if(top=='*') res=prvi*drugi;
            else if(top=='/') res=prvi/drugi;
            else if(top=='+') res=prvi+drugi;
            else res = prvi - drugi;
            val.push(res);
        }
        oper.push(e[i]);
    }

    if(e[i]==')')
    {

        while(oper.top()!='(')
        {
        int drugi=val.top();val.pop();
            int prvi=val.top();val.pop();
            int res=0;
            char top=oper.top();oper.pop();
            if(top=='*') res=prvi*drugi;
            else if(top=='/') res=prvi/drugi;
            else if(top=='+') res=prvi+drugi;
            else res = prvi - drugi;
            val.push(res);
        }
        oper.pop();
    }

//cout<<i<<"}\n";
   // cout<<val.top()<<endl;
  //  if(!oper.empty()) cout<<oper.top()<<endl;
}


while(!oper.empty())
        {
        int drugi=val.top();val.pop();
            int prvi=val.top();val.pop();
            int res=0;
            char top=oper.top();oper.pop();
            if(top=='*') res=prvi*drugi;
            else if(top=='/') res=prvi/drugi;
            else if(top=='+') res=prvi+drugi;
            else res = prvi - drugi;
            val.push(res);
        }
cout<<val.top()<<endl;

return 0;
}

