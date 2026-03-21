## 🔷 C 函数设计基础写法（Checklist）

1. **先判断函数类型（最核心）**
    - 求值（计算结果） → 用返回值 `return`
    - 操作（修改数据） → 用 `void` + 指针参数
2. **参数只传“必要信息”**
    - 不要多传（降低耦合）
    - 不要少传（保证函数自洽）
    - 数组一律：`arr + n`
3. **区分输入 / 输出**
    - 输入参数 → 普通变量 / `const T *`
    - 输出参数 → `T *out_xxx`
    - 修改数据 → `T *`（非 const）
    - 原地修改 → 加“_inplace”函数后缀
---

4. **只读数据一律加 `const`**
    ```c
    double sum(const int *arr, int n);
    ```
    - 表达“不会修改”
    - 提升安全性 + 可读性
---

5. **返回值优先原则**
    - 单个核心结果 → `return`
    - 多个结果 → 输出参数out_ or `struct`
    - 不要滥用输出参数

---

6. **错误处理标准写法**
    ```c
    int func(输入..., 输出参数...);
    ```
    - `return` → 成功 / 失败
    - `out_xxx` → 实际结果
---

7. **参数顺序规范（很重要）**
    ```
    1. 被操作对象（如果有）
    2. 输入参数
    3. 输出参数（out_）
    ```
8. **输出参数命名规范**
- 统一用：`out_`	
    ```c
    int get_max(const int *arr, int n, int *out_max);
    ```
    

---

9. **函数命名用“动词语义”**
    
    - 查询：`get / is / has / find / calc`
        
    - 操作：`set / init / update / print / destroy`
        
    - ❌ 不用 `_` 区分返回值
        

---

10. **是否修改数据要“显式表达”**
    

- 修改 → `T *`
    
- 不修改 → `const T *`
    
- 可加 `_inplace` 提升语义
    

```c
void normalize_inplace(double *arr, int n);
```

---

11. **避免混合职责（非常关键）**
    

- ❌ 计算 + 修改 + 打印 写在一个函数
    
- ✅ 拆分为多个函数
    

---

12. **常用模板（直接套用）**
    

- 纯计算：
    

```c
double calc_mean(const double *arr, int n);
```

- 原地修改：
    

```c
void sort(int *arr, int n);
```

- 多输出 + 状态：
    

```c
int stats(const int *arr, int n, double *out_mean, int *out_max);
```

---

## 🔥 一句话总纲

**输入在前，输出在后；单结果用 return，多结果用 out_；修改数据用指针，不修改必须 const。**