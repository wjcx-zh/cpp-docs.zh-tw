---
title: 編譯器錯誤 C2668 |Microsoft 文件
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2668
dev_langs:
- C++
helpviewer_keywords:
- C2668
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea6cb5f53d3d4d0971398dbba10e24b579ce6c62
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236397"
---
# <a name="compiler-error-c2668"></a>編譯器錯誤 C2668
'function': 模稜兩可的呼叫多載函式  
  
 無法解析指定的多載函式呼叫。 若要明確轉換一或多個實際的參數。  
  
 您也可以藉由使用範本來取得這項錯誤。 如果在相同類別中，您有一般成員函式以及相同的簽章樣板成員函式，必須先使用樣板化的其中一個。 這是目前的 Visual c + + 實作的限制。  
  
 在函式樣板的部分排序，請參閱知識庫文件 Q240869 如需詳細資訊。  
  
 如果您要建立包含支援 COM 物件的 ATL 專案`ISupportErrorInfo`，請參閱知識庫文章 Q243298。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2668:  
  
```  
// C2668.cpp  
struct A {};  
struct B : A {};  
struct X {};  
struct D : B, X {};  
  
void func( X, X ){}  
void func( A, B ){}  
D d;  
int main() {  
   func( d, d );   // C2668 D has an A, B, and X   
   func( (X)d, (X)d );   // OK, uses func( X, X )  
}  
```  
  
## <a name="example"></a>範例  
 若要解決此錯誤的另一個方法是使用[using 宣告](../../cpp/using-declaration.md):  
  
```  
// C2668b.cpp  
// compile with: /EHsc /c  
// C2668 expected  
#include <iostream>  
class TypeA {  
public:  
   TypeA(int value) {}  
};  
  
class TypeB {  
   TypeB(int intValue);  
   TypeB(double dbValue);  
};  
  
class TestCase {  
public:  
   void AssertEqual(long expected, long actual, std::string  
                    conditionExpression = "");  
};  
  
class AppTestCase : public TestCase {  
public:  
   // Uncomment the following line to resolve.  
   // using TestCase::AssertEqual;  
   void AssertEqual(const TypeA expected, const TypeA actual,  
                    std::string conditionExpression = "");  
   void AssertEqual(const TypeB expected, const TypeB actual,  
                    std::string conditionExpression = "");  
};  
  
class MyTestCase : public AppTestCase {  
   void TestSomething() {  
      int actual = 0;  
      AssertEqual(0, actual, "Value");  
   }  
};  
```  
  
## <a name="example"></a>範例  
 也可以針對 Visual Studio.NET 2003年所進行的編譯器一致性工作產生這個錯誤： 常數 0 轉換上模稜兩可的轉換。  
  
 在使用常數 0 轉換的轉換模稜兩可，因為 int 需要轉換兩個長時間和 void *。 若要解決這個錯誤，轉型 0 到它使用，因此不需要進行 （此程式碼是有效的 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中） 的任何轉換的函式參數的確切類型。  
  
```  
// C2668c.cpp  
#include "stdio.h"  
void f(long) {  
   printf_s("in f(long)\n");  
}  
void f(void*) {  
   printf_s("in f(void*)\n");  
}  
int main() {  
   f((int)0);   // C2668  
  
   // OK  
   f((long)0);  
   f((void*)0);  
}  
```  
  
## <a name="example"></a>範例  
 這個錯誤可能是因為 CRT 現在具有 float 和所有數學函式的雙精度浮點格式。  
  
```  
// C2668d.cpp  
#include <math.h>  
int main() {  
   int i = 0;  
   float f;  
   f = cos(i);   // C2668  
   f = cos((float)i);   // OK  
}  
```  
  
## <a name="example"></a>範例  
 由於 math.h CRT 中已移除 pow （int，int），就會發生此錯誤。  
  
```  
// C2668e.cpp  
#include <math.h>  
int main() {  
   pow(9,9);   // C2668  
   pow((double)9,9);   // OK  
}  
```

## <a name="example"></a>範例  
這段程式碼在 Visual Studio 2015 會成功，但無法以 Visual Studio 2017 和更新版本 C2668。 在 Visual Studio 2015 中，編譯器會使用與一般 copy-initialization 相同的方式錯誤地處理 copy-list-initialization；它只會考慮轉換建構函式來進行多載解析。 

```
C++
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```