---
title: nullptr （c + + 元件延伸模組） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a52f2a11634ff79bcb58302d4b2a4d7ceed362cc
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017119"
---
# <a name="nullptr--c-component-extensions"></a>nullptr (C++ 元件擴充功能)
**Nullptr**關鍵字表示*null 指標值*。 使用 null 指標值來表示的物件控制代碼、 內部指標或原生指標類型未指向物件。  
  
 使用**nullptr**以 managed 或原生程式碼。 編譯器會發出適當，但不同的指示，針對 managed 和原生的 null 指標值。 如需使用此關鍵字的 ISO 標準 c + + 版本的資訊，請參閱[nullptr](../cpp/nullptr.md)。  
  
 **__Nullptr**關鍵字是具有相同的意義是 Microsoft 專有關鍵字**nullptr**，但適用於原生的程式碼。 如果您使用**nullptr**原生 C/c + + 程式碼，然後再使用編譯[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項，編譯器無法判斷是否**nullptr**表示原生或管理 null 指標值。 若要讓您的意圖清除編譯器，使用**nullptr**指定的受管理的值或 **__nullptr**指定原生的值。  
  
 **Nullptr**關鍵字相當於**Nothing** Visual Basic 中並**null** C# 中。  
  
## <a name="usage"></a>使用量  
 **Nullptr**關鍵字可用於任何地方使用控制代碼、 原生指標或函式引數。  
  
 **Nullptr**關鍵字不是類型和不支援搭配使用：  
  
-   [sizeof](../cpp/sizeof-operator.md)  
  
-   [typeid](../cpp/typeid-operator.md)  
  
-   `throw nullptr` (雖然`throw (Object^)nullptr;`運作)  
  
 **Nullptr**關鍵字可用於下列指標類型的初始設定：  
  
-   原生指標  
  
-   Windows 執行階段控制代碼  
  
-   受管理的控制代碼  
  
-   受管理的內部指標  
  
 **Nullptr**關鍵字可以用來測試是否能使用參考之前，指標或控制代碼的參考為 null。  
  
 函式呼叫之間進行錯誤檢查中使用 null 指標值的語言應該正確解譯。  
  
 您無法初始化為零; 的控制代碼只有**nullptr**可用。 為物件控制代碼的常數 0 的指派產生 boxed`Int32`轉型和`Object^`。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範**nullptr**關鍵字可用於控制代碼，而原生指標，或可以使用函式引數。 與此範例示範**nullptr**關鍵字可以用來檢查參考，才能使用。  
  
```cpp  
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
  
 下列程式碼範例顯示**nullptr**和零可以交換使用原生指標。  
  
```cpp  
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
  
```Output  
pMyClass == nullptr  
  
pMyClass == 0  
  
pMyClass == nullptr  
  
pMyClass == 0  
```  
  
## <a name="example"></a>範例  
  
 下列程式碼範例顯示**nullptr**會解譯為任何類型的控制代碼或任何類型的原生指標。 如果使用不同類型的控制代碼，多載函式，將會產生模稜兩可錯誤。 **Nullptr**必須明確轉型為型別。  
  
```cpp  
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
  
 下列程式碼範例會顯示該轉型**nullptr**允許，並傳回包含轉換類型的指標或控點**nullptr**值。  
  
```cpp  
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
  
 下列程式碼範例顯示**nullptr**可用來當做函式參數。  
  
```cpp  
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
  
```Output  
test  
```  
  
## <a name="example"></a>範例  
  
 下列程式碼範例顯示當控制代碼宣告和未明確初始化，初始化為預設值**nullptr**。  
  
```cpp  
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
  
```Output  
NULL  
```  
  
## <a name="example"></a>範例  
  
 下列程式碼範例顯示**nullptr**可以指派給原生指標中，當您使用編譯`/clr`。  
  
```cpp  
// mcpp_nullptr_6.cpp  
// compile with: /clr  
int main() {  
   int * i = 0;  
   int * j = nullptr;  
}  
```  
  
## <a name="requirements"></a>需求  
 編譯器選項: (不需要，支援所有的程式碼產生選項，包括`/ZW`和`/clr`)  
  
## <a name="see-also"></a>另請參閱  
 [執行階段平台的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)   
 [nullptr](../cpp/nullptr.md)