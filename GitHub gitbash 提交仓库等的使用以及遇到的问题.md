1.git 提交到远程仓库出问题

```C++
Connection was reset, errno 10054
```

解决办法：
```c
git config --global http.sslVerify "false"
```

