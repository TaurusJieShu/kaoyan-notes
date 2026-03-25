### 调整数组往前移n位
```c
void left_str_n(char* str, int n) {
    if (str == NULL) retuen NULL;
    int length = 0;
	while (str[length] != '\0') length++; // strlen(str) - 1
	
    for (int i = n; i < length; i++) {
        str[i - n] = str[i];
    }
    str[length - n] = '\0';  // 终止符
}
```


