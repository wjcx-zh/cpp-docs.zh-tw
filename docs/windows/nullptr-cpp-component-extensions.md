---
title: "nullptr （c + + 元件擴充功能） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: be7fcc147a5f6f4b96f7bf7dd68376613489946c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="nullptr--c-component-extensions"></a>nullptr (C++ 元件擴充功能)
`nullptr`關鍵字表示*null 指標值*。 使用 null 指標值表示的物件控制代碼、 內部指標或原生指標類型不是指向物件。  
  
 使用`nullptr`managed 或原生程式碼。 編譯器會發出 managed 和原生的 null 指標值適用，但不同的指示。 使用此關鍵字的 ISO 標準 c + + 版本的相關資訊，請參閱[nullptr](../cpp/nullptr.md)。  
  
 `__nullptr`關鍵字是具有相同的意義是 Microsoft 專有關鍵字`nullptr`，但適用於只有原生程式碼。 如果您使用`nullptr`與原生 C/c + + 程式碼，然後再使用編譯[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項，編譯器無法判斷是否`nullptr`指出原生或 managed 的 null 指標值。 若要讓您的意圖清除編譯器，請使用`nullptr`指定受管理的值或`__nullptr`指定原生值。  
  
 `nullptr`關鍵字相當於`Nothing`在 Visual Basic 和`null`C# 中。  
  
## <a name="usage"></a>使用量  
 `nullptr`關鍵字可以使用任何可使用控制代碼、 原生指標或函式引數位置。  
  
 `nullptr`關鍵字不是型別和不支援搭配使用：  
  
-   [sizeof](../cpp/sizeof-operator.md)  
  
-   [typeid](../cpp/typeid-operator.md)  
  
-   `throw nullptr`(雖然`throw (Object^)nullptr;`運作)  
  
 `nullptr`關鍵字可用於下列指標類型的初始設定：  
  
-   原生指標  
  
-   Windows 執行階段控制代碼  
  
-   受管理的控制代碼  
  
-   受管理的內部指標  
  
 `nullptr`關鍵字可用來測試如果之前的參考用的指標或控制代碼的參考為 null。  
  
 使用錯誤檢查 null 指標值的語言之間的函式呼叫應該正確解譯。  
  
 您無法初始化的控制代碼為零。只有`nullptr`可用。 常數 0 為物件控制代碼的作業會產生 boxed`Int32`和轉型至`Object^`。  
  
## <a name="example"></a>範例  
 下列程式碼範例會示範`nullptr`關鍵字可用於控制代碼，而原生指標，或可以使用函式引數。 此範例示範和`nullptr`關鍵字可以用來檢查參考，才能使用。  
  
```  
// mcpp_nullptr.cpp  
// compile with: /clr  
value class V {};  
ref class G {};  
void f(System::Object ^) {}  
  
int main() {  
// Native pointer.  
   int *pN = nullptr;  
// Managed handle.  
   G ^pG = nullptr;  
   V ^pV1 = nullptr;  
// Managed interior pointer.  
   interior_ptr<V> pV2 = nullptr;  
// Reference checking before using a pointer.  
   if (pN == nullptr) {}  
   if (pG == nullptr) {}  
   if (pV1 == nullptr) {}  
   if (pV2 == nullptr) {}  
// nullptr can be used as a function argument.  
   f(nullptr);   // calls f(System::Object ^)  
}  
```  
  
## <a name="example"></a>範例  
 **範例**  
  
 下列程式碼範例顯示`nullptr`和零可以交換使用原生指標。  
  
```  
// mcpp_nullptr_1.cpp  
// compile with: /clr  
class MyClass {  
public:  
   int i;  
};  
  
int main() {  
   MyClass * pMyClass = nullptr;  
   if ( pMyClass == nullptr)  
      System::Console::WriteLine("pMyClass == nullptr");  
  
   if ( pMyClass == 0)  
      System::Console::WriteLine("pMyClass == 0");  
  
   pMyClass = 0;  
   if ( pMyClass == nullptr)  
      System::Console::WriteLine("pMyClass == nullptr");  
  
   if ( pMyClass == 0)  
      System::Console::WriteLine("pMyClass == 0");  
}  
```  
  
 **輸出**  
  
```Output  
pMyClass == nullptr  
  
pMyClass == 0  
  
pMyClass == nullptr  
  
pMyClass == 0  
```  
  
## <a name="example"></a>範例  
 **範例**  
  
 下列程式碼範例顯示`nullptr`會解譯為任何類型的控制代碼或任何類型的原生指標。 如果函式多載與不同類型的控制代碼，會產生模稜兩可錯誤。 `nullptr`必須明確轉換成的型別。  
  
```  
// mcpp_nullptr_2.cpp  
// compile with: /clr /LD  
void f(int *){}  
void f(int ^){}  
  
void f_null() {  
   f(nullptr);   // C2668  
   // try one of the following lines instead  
   f((int *) nullptr);  
   f((int ^) nullptr);  
}  
```  
  
## <a name="example"></a>範例  
 **範例**  
  
 下列程式碼範例會顯示該轉換`nullptr`允許和轉換類型，其中包含要傳回的指標或控點`nullptr`值。  
  
```  
// mcpp_nullptr_3.cpp  
// compile with: /clr /LD  
using namespace System;  
template <typename T>   
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type  
  
int main() {  
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)  
  
   // Delete the following line to resolve.  
   f(nullptr);  
  
   f(0);   // T = int, call f(int)  
}  
```  
  
## <a name="example"></a>範例  
 **範例**  
  
 下列程式碼範例顯示`nullptr`可用來當作函式參數。  
  
```  
// mcpp_nullptr_4.cpp  
// compile with: /clr  
using namespace System;  
void f(Object ^ x) {  
   Console::WriteLine("test");  
}  
  
int main() {  
   f(nullptr);  
}  
```  
  
 **輸出**  
  
```Output  
test  
```  
  
## <a name="example"></a>範例  
 **範例**  
  
 下列程式碼範例示範當宣告控制代碼，而未明確初始化，它們的預設初始化為`nullptr`。  
  
```  
// mcpp_nullptr_5.cpp  
// compile with: /clr  
using namespace System;  
ref class MyClass {  
public:  
   void Test() {  
      MyClass ^pMyClass;   // gc type  
      if (pMyClass == nullptr)  
         Console::WriteLine("NULL");  
   }  
};  
  
int main() {  
   MyClass ^ x = gcnew MyClass();  
   x -> Test();  
}  
```  
  
 **輸出**  
  
```Output  
NULL  
```  
  
## <a name="example"></a>範例  
 **範例**  
  
 下列程式碼範例顯示`nullptr`可以指派給原生指標中，當您使用編譯**/clr**。  
  
```  
// mcpp_nullptr_6.cpp  
// compile with: /clr  
int main() {  
   int * i = 0;  
   int * j = nullptr;  
}  
```  
  
## <a name="requirements"></a>需求  
 編譯器選項: (不需要，則所有的程式碼產生選項，包括支援**/ZW**和**/clr**)  
  
## <a name="see-also"></a>請參閱  
 [執行階段平台的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)   
 [nullptr](../cpp/nullptr.md)