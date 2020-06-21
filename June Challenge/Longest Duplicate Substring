class Solution {
    public String longestDupSubstring(String S) {
        int lo = 1;
        int hi = S.length();
        while (lo != hi) {
            int mi = lo + (hi - lo) / 2;
            if (possible(S, mi) != -1)
                lo = mi + 1;
            else
                hi = mi;
        }
        int start = possible(S, lo - 1);
        return start != -1 ? S.substring(start, start + lo - 1) : "";
    }
    public int possible(String s, int len) {
        long hash = 0;
        int a = 26;
        int n = s.length();
        final long mod = (long)Math.pow(2, 32);
        for(int i = 0; i < len; ++i) 
            hash = (hash * a + (s.charAt(i)-'a')) % mod;

        HashSet<Long> set = new HashSet();
        set.add(hash);
        long global = 1;
        for (int i = 0; i < len; ++i) 
            global = (global * a) % mod;

        for(int start = 1; start < n - len + 1; ++start) {
            hash = (hash * a - (s.charAt(start - 1)-'a') * global % mod + mod) % mod;
            hash = (hash + (s.charAt(start + len - 1)-'a')) % mod;
            if (set.contains(hash)) return start;
            set.add(hash);
        }
        return -1;
    }
}
