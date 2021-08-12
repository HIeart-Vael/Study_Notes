# C++竞赛编程技巧

## 持续输入：

```C++
while(cin)
```



## 输入一串数列，逗号分隔

```C++
string str;
vector<int> vec;
while(getline(cin, str, ',')) {
    vec.push_back(stoi(str));
}
```

