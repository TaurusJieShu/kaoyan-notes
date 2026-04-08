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

# 快速排序 / 快速选择
```c
void swap(int* point1, int* point2) {
	int t = *point1;
	*point1 = *point2;
	*point2 = t;
}

int quick_select(int* nums, int l, int r, int k) {
	if(l == r) return nums[k];  // 达成目的 找到第k个元素
	
	// 比较部分：如果符合要求就往中间走
	int compared_num = nums[l];
	int i = l - 1;
	int j = r + 1;
	while(i < j) {
		do i++; while(nums[i] < compared_num);
		do j--; while(nums[j] > compared_num);
		// 找到两个不合适的元素，就交换这两个元素的位置
		if (i < j) swap(&nums[i], &nums[j]);
	}
	// 加入了选择，只做一部分内容，再进行快排
	if (j <= k) quick_select(nums, j+1, r, k); 
	else quick_select(nums, l, j, k);
}

void quick_sort(int* nums, int l, int r) {
	if(l == r) return; // 不需要返回的
	
	// 比较部分：如果符合要求就往中间走
	int compared_num = nums[l];
	int i = l - 1;
	int j = r + 1;
	
	while(i < j) {
		do i++; while(nums[i] < compared_num);
		do j--; while(nums[j] > compared_num);
		if (i < j) swap(&nums[i], &nums[j]);
	}
	// 两边分别再做快排
	quick_sort(nums, j+1, r);
	quick_sort(nums, l, j);
}
```
