---
title: "編譯器錯誤 c3861: |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3861
dev_langs: C++
helpviewer_keywords: C3861
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 82656822d408be4b2fc085abe8a007469c822a65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3861"></a>編譯器錯誤 C3861

> '*識別碼*': 找不到識別項  
  
即使使用引數相依查閱，編譯器仍無法解析識別項的參考。  
  
若要修正這個錯誤，比較使用*識別碼*識別項宣告的大小寫和拼字。 確認[範圍解析運算子](../../cpp/scope-resolution-operator.md)和命名空間[using 指示詞](../../cpp/namespaces-cpp.md#using_directives)正確使用。 如果標頭檔中宣告的識別項，請確認識別項參考之前，會包含標頭。 如果識別項就是要為外部可見的請確定它使用它的任何原始程式檔中宣告。 也請確認識別項宣告或定義不排除不由[條件式編譯指示詞](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)。 

若要從 Visual Studio 2015 中的 C 執行階段程式庫移除過時的函式的變更會造成 C3861。 若要解決這個錯誤，移除這些函式的參考，或它們取代成其安全的替代項目，如果有的話。 如需詳細資訊，請參閱[過時的函式](../../c-runtime-library/obsolete-functions.md)。  

如果錯誤 c3861： 從較舊版本的編譯器中會出現專案移轉之後，您可能必須支援的 Windows 版本相關問題。 Visual C++ 不再支援將 Windows 95、Windows 98、Windows ME、Windows NT 或 Windows 2000 當做目標。 如果您 WINVER 或 _WIN32_WINNT 巨集指派給其中一個這些 Windows 版本，您必須修改巨集。 如需詳細資訊，請參閱[修改 WINVER 和 _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md)。
  
## <a name="example"></a>範例  

下列範例會產生 C3861，因為未定義識別項。  
  
```cpp  
// C3861.cpp  
void f2(){}  
int main() {  
   f();    // C3861  
   f2();   // OK  
}  
```  
  
## <a name="example"></a>範例  

下列範例會產生 C3861，因為識別項只會顯示在檔案範圍，其定義，除非它被宣告中使用它的其他原始程式檔。  
  
```cpp  
// C3861_a1.cpp
// Compile with: cl /EHsc /W4 C3861_a1.cpp C3861_a2.cpp  
#include <iostream>
// Uncomment the following line to fix:
// int f();  // declaration makes external function visible
int main() {  
   std::cout << f() << std::endl;    // C3861
}  
```  
  
```cpp  
// C3861_a2.cpp  
int f() {  // declared and defined here
   return 42;  
}
```  
  
## <a name="example"></a>範例  

C + + 標準程式庫中的例外狀況類別，需要`std`命名空間。  
  
```cpp  
// C3861_b.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   try {  
      throw exception("Exception");   // C3861  
      // try the following line instead  
      // throw std::exception("Exception");  
   }  
   catch (...) {  
      std::cout << "caught an exception" << std::endl;  
   }  
}  
```  
## <a name="example"></a>範例  

已從 CRT 程式庫移除過時的函式。  
  
```cpp  
// C3861_c.cpp  
#include <stdio.h>  
int main() {  
   char line[21]; // room for 20 chars + '\0'  
   gets( line );  // C3861  
   // Use gets_s instead.  
   printf( "The line entered was: %s\n", line );  
}  
```
下列範例會產生 C3767，因為編譯器無法使用引數相依查閱，如 FriendFunc:  
  
```  
namespace N {  
   class C {  
      friend void FriendFunc() {}  
      friend void AnotherFriendFunc(C* c) {}  
   };  
}  
  
int main() {  
   using namespace N;  
   FriendFunc();   // C3861 error  
   C* pC = new C();  
   AnotherFriendFunc(pC);   // found via argument-dependent lookup  
}  
```  
  
若要修正錯誤，宣告在類別範圍中的為 friend，並在命名空間範圍中定義它：  
  

MyClass {類別  
   int m_private;  
   friend void func （);  
};  
  
void func （） {  
   MyClass s;  
   s.m_private = 0;  
}  
  
int main （） {  
   func （);  
}  