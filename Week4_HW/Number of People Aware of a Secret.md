#### Number of People Aware of a Secret

class Solution {

  public int peopleAwareOfSecret(int n, int delay, int forget) {

​    long MOD = 1000000007L;

​    long[] dp = new long[n + 1];

​    dp[1] = 1;

​    long sharing = 0; 

​    for (int day = 2; day <= n; day++) {

​      int startShare = day - delay;

​      if (startShare >= 1)

​        sharing = (sharing + dp[startShare]) % MOD;

​      int forgetDay = day - forget;

​      if (forgetDay >= 1)

​        sharing = (sharing - dp[forgetDay] + MOD) % MOD;

​      dp[day] = sharing;

​    }

​    long res = 0;

​    for (int i = n - forget + 1; i <= n; i++) {

​      if (i >= 1)

​        res = (res + dp[i]) % MOD;

​    }

​    return (int) res;

  }

}