# KMP

用于字符串模式匹配。核心是失配时利用已经匹配出的前缀信息。

```cpp
vector<int> prefix_function(const string& s) {
    int n = s.size();
    vector<int> pi(n);

    for (int i = 1; i < n; ++i) {
        int j = pi[i - 1];
        while (j > 0 && s[i] != s[j]) j = pi[j - 1];
        if (s[i] == s[j]) ++j;
        pi[i] = j;
    }
    return pi;
}
```

前缀函数时间复杂度 O(n)。
