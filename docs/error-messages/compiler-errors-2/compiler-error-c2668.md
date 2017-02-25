---
title: "編譯器錯誤 C2668 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2668"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2668"
ms.assetid: 041e9627-1c76-420e-a653-cfc83f933bd3
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 編譯器錯誤 C2668
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 模稜兩可的呼叫多載函式  
  
 無法解析指定的多載函式呼叫。  您可能需要明確轉換實質參數的其中一個或多個。  
  
 您也可以使用樣板來取得這項錯誤。  如果在同一個類別中，您具有一個一般的成員函式和一個樣板的成員函式，而且它們都具用相同的簽章，則樣板成員函式必須先出現。  這是目前 Visual C\+\+ 實作的一項限制。  
  
 如需函式樣板的部分指定詳細資訊，請參閱知識庫文件 Q240869。  
  
 如果是建置包含支援 `ISupportErrorInfo` 之 COM 物件的 ATL 專案，請參閱知識庫文件 Q243298。  
  
## 範例  
 下列範例會產生 C2668：  
  
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
  
## 範例  
 另一解決這個錯誤的方法是使用 [using 宣告](../../cpp/using-declaration.md)：  
  
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
  
## 範例  
 對 Visual Studio .NET 2003 的編譯器完成符合標準處理後也會出現這個錯誤：轉換 \(Conversion\) 常數為 0 的轉型 \(Cast\) 是模稜兩可的。  
  
 轉換使用常數 0 之轉型是模稜兩可的，因為 int 必須轉換成 long 和 void\*。  若要解決這個錯誤，請將 0 轉型成使用 0 之函式參數的確切型別，這樣便可不必進行任何轉換 \(在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中，這個程式碼將是有效的\)。  
  
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
  
## 範例  
 可能是因為現在 CRT 具有所有數學函式的浮點和雙精度浮點數格式而發生這個錯誤。  
  
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
  
## 範例  
 可能是因為已從 the CRT 中的 math.h 移除 pow\(int, int\) 而產生這個錯誤。  
  
```  
// C2668e.cpp  
#include <math.h>  
int main() {  
   pow(9,9);   // C2668  
   pow((double)9,9);   // OK  
}  
```