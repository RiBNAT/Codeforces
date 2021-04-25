

// Tanbir Ahmed  << RiBNAT >>       //
// University of Barisal, Bangladesh  //



#include<bits/stdc++.h>
#include <ext/pb_ds/assoc_container.hpp>
#include <ext/pb_ds/tree_policy.hpp>
using namespace std;
using namespace __gnu_pbds;
#define     fast            ios_base::sync_with_stdio(false);cin.tie(NULL)
#define     in1(X)          scanf("%lli",&(X))
#define     ins(S)          scanf("%s",(S))
#define     out(X)          printf("%lli",(X))
#define     outs(S)         printf("%s",(S))
#define     Pnl             printf("\n")
#define     End             return 0
#define     ll              long long int
#define     Pair            pair<ll,ll>
#define     F               first
#define     S               second
#define     all(v)          v.begin(),v.end()
#define     mem(a,v)        memset(a,v,sizeof(a))
#define     Max             1000000000000000014
#define     Min             -1000000000000000014
#define     mod             1000004119//1000000007 //1000000000000000009//9223372036854775807//10000019 //1000000007//1000033
#define     range           100007
#define     pb              push_back
#define     Vector          vector<ll>
#define     mp              make_pair
#define     PI              3.14159265358979323846 // acos(-1)
#define     min_heap        priority_queue <ll, vector<ll>, greater<ll> >
#define     ordered_set     tree<ll, null_type,less<ll>, rb_tree_tag,tree_order_statistics_node_update>  //*(x.find_by_order(k)),x.order_of_key(k)

/*************** #Template FUNCTIONS# **************/

 ll pc;void PrintCase(){printf("Case #%lli: ",++pc);}
// ll GCD(ll a,ll b){if(a<0) a*=-1;if(b<0) b*=-1;if(a<b)swap(a,b);if(b==1) return 1;if(!b) return a;if(!(a%b)) return b;else return GCD(b,a%b);}
// ll LCM(ll a,ll b){ll x=GCD(a,b);return (a/x)*b;}
 ll bigmod(ll n,ll p){if(p==0) return 1;if(p==1)return (n+mod)%mod;if(p%2)return (bigmod(n,p-1)*n+mod)%mod;else{ll x=bigmod(n,p/2);return (x*x+mod)%mod;}}
 ll power(ll n,ll p){if(p==0) return 1;if(p==1)return n;if(p%2)return power(n,p-1)*n;else{ll x=power(n,p/2);return x*x;}}
 ll modinverse(ll n){return bigmod(n,mod-2)%mod;}
 ll Check(ll n,ll i){return (n&(1LL<<i));}
 ll Set(ll n,ll i){return (n|(1LL<<i));}
 ll status[(ll)range/64+5];Vector primes;void sieve(){for(ll i=3;i<=sqrt(range);i+=2){if(Check(status[i/64],i%64)==0){for(ll j=i*i;j<range;j+=2*i){status[j/64]=Set(status[j/64],j%64);}}}primes.pb(2);for(ll i=3;i<range;i+=2)if(Check(status[i/64],i%64)==0)primes.pb(i);}

// ll dx[] = {-2, -1, 1, 2,  2,  1, -1, -2};
// ll dy[] = { 1,  2, 2, 1, -1, -2, -2, -1};

// ll X[]= {0,0,1,-1,1,1,-1,-1};
// ll Y[]= {1,-1,0,0,1,-1,1,-1};

//    #define check(n,pos)  (n & (1<<pos))
//    #define setup(n,pos)  (n | (1<<pos))
//    #define unset(n,pos)  (n & !(1<<pos))
//  bool chk(ll mask) {return (bool)(mask & ((1<<10)-1))}; //if last 10 bit of mask is on, then return true. otherwise return false

/********************** F-King Start **********************/






ll node_id[7000007][2],end_word[7000007],n;

void insert_in_trie(string s){
    ll par_node=0;
    for(ll i=0;i<s.size();i++){
        if(node_id[par_node][s[i]-'0']==-1){
            node_id[par_node][s[i]-'0']=++n;
        }
        par_node=node_id[par_node][s[i]-'0'];
        end_word[par_node]++;
    }
}

ll search_in_trie(string s){
    ll par_node=0;
    string p="";
    for(ll i=0;i<s.size();i++){
        ll k=s[i]-'0';
        if(k) k=0;
        else k=1;

        if(node_id[par_node][k]!=-1 and end_word[ node_id[par_node][k] ] > 0){
            p+="1";
            par_node=node_id[par_node][k];
        }
        else if(node_id[par_node][!k]!=-1 and end_word[ node_id[par_node][!k] ] > 0 ){
            p+="0";
            par_node=node_id[par_node][!k];
        }
        else{
            for(ll j=i; j<s.size(); j++){
                p+=s[j];
            }
            break;
        }
        
    }
    ll ans=0;
    reverse(all(p));
    for(ll i=0; i<35; i++){
        ans+=(p[i]-'0')*power(2,i);
    }
    return ans;
}

void delete_word_in_trie(string s){
    ll par_node=0;
    for(ll i=0;i<s.size();i++){
        par_node=node_id[par_node][s[i]-'0'];
        end_word[par_node]--;
    }
}

int main()
{   
    memset(node_id,-1,sizeof(node_id));
    ll q;
    cin>>q;

    string p="";
    for(ll i=0; i<35; i++){
        p+="0";
    }
    insert_in_trie(p);

    while(q--){
        char c;
        string s;
        ll x,i,j,k;
        cin>>c>>x;

        while(x>0){
            k=x%2;
            s+=k+'0';
            x/=2;
        }
        for(i=s.size(); i<35; i++){
            s+='0';
        }
        //cout<<s.size()<<endl;
        reverse(all(s));
        //cout<<s<<endl;

        if(c=='+') insert_in_trie(s);
        if(c=='-') delete_word_in_trie(s);
        if(c=='?'){
            ll ans=search_in_trie(s);
            cout<<ans<<endl;
        }
    }

    return 0;
}




/********************** Happy F-King **********************/
