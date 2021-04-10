lcm（a,b)即a,b的最小公倍数；gcd(a,b)即a,b的最大公约数
性质：
- 若a/m,b/m,则lcm(a,b)/m
- 若d/a,d/b,则d/gcd(a,b)

- lcm(a,b) = ab/gcd(a,b)
- 设m,a,b是正整数，则lcm(ma,mb) = m*lcm(a,b)
- 若m是非零整数a1,a2....am的公倍数则lcm(a1,a2....an)/m
- 若a*x + b*y = c,其中a,b,c是整数,a*b!=0,此方程有整数解的充要条件是gcd(a,b)/c

推理过程：
lcm == a*t1 == b*t2
设a和b的最大公约数=G
a == m*G, b == n*G
lcm == m*G*t1 == n*G*t2
m*t1 == n*t2
m/t2 == n/t1 == C (因为m,n互质，gcd(m,n)不可能再有因数，所以c==1)
m = Ct2, n = Ct1
Glcm = anG
lcm == ab/G -->lcm == ad/gcd(a,b)


辗转相除法：
辗转相除法给出了一个关系：gcd(a,b) == gcd(b,r),其中a,b,q,r都是整数，满足a == bq+r
证明(相减)：
int GCD(int a, int b) {
    return b==0?a:GCD(b,a%b);
}