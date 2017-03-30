---
---
# <a name="compiler-warning-level-1-c4055"></a>編譯器警告 (層級 1) C4055  
  
'conversion': 從資料指標 'type1' 到函式指標 'type2'  
  
**過時︰**由 Visual Studio 2017 和更新版本的版本不會產生這個警告。

 資料指標轉型 (可能不正確) 成函式指標。 這在 /Za 下是層級 1 警告，在 /Ze 下是層級 4 警告。  
  
 下列範例會產生 C4055：  
  
```C  
// C4055.c  
// compile with: /Za /W1 /c  
typedef int (*PFUNC)();  
int *pi;  
PFUNC f() {  
   return (PFUNC)pi;   // C4055  
}  
```  
  
 這在 /Ze 下是層級 4 警告。  
  
```C  
// C4055b.c  
// compile with: /W4 /c  
typedef int (*PFUNC)();  
int *pi;  
PFUNC f() {  
return (PFUNC)pi;   // C4055  
}  
```