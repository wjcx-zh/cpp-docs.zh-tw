---
title: "nullptr  (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__nullptr keyword (C++)"
  - "nullptr keyword [C++]"
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
caps.latest.revision: 24
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# nullptr  (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`nullptr` 關鍵字表示 *null 指標值*。  使用空指標值表示物件控制碼、內部指標或原生指標型別不指向物件。  
  
 使用與 Managed 或機器碼的 `nullptr` 。  編譯器發出 Managed 和原生 null 指標值的適當，但不同的指示。  如需使用這個關鍵字 ISO 標準 C\+\+ 版本的詳細資訊，請參閱 [nullptr](../cpp/nullptr.md)。  
  
 `__nullptr` 關鍵字與 `nullptr` 相同的 Microsoft 專有的關鍵字有相同的意義，但僅套用至機器碼。  如果您使用與原生 C\/C\+\+ 程式碼的 `nullptr` 會編譯使用 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 編譯器選項，編譯器無法判斷 `nullptr` 是否表示一個原生或 Managed null 指標值。  若要讓要清除給編譯器，請使用 `nullptr` 指定 Managed 值或 `__nullptr` 指定的值。  
  
 `nullptr`關鍵字相當於 Visual Basic 中的 `Nothing` 關鍵字和 C\# 的`null`。  
  
## 使用方式  
 可以使用 `nullptr` 關鍵字任何控制代碼，原生指標，或者可以使用函式引數。  
  
 `nullptr` 關鍵字不是型別且不支援使用:  
  
-   [sizeof](../cpp/sizeof-operator.md)  
  
-   [typeid](../cpp/typeid-operator.md)  
  
-   `throw nullptr` \(雖然 `throw (Object^)nullptr;` 會運作\)  
  
 `nullptr` 關鍵字可使用在下列指標型別的初始化:  
  
-   原生指標。  
  
-   Windows 執行階段控制代碼  
  
-   Managed 控制代碼  
  
-   Managed 內部指標  
  
 `nullptr` 關鍵字可用來測試，如果指標或控制代碼參考是空的，才能使用參考。  
  
 語言中應該正確解譯為錯誤檢查 null 指標值的函式呼叫。  
  
 您無法使用控制代碼為零；只能使用 `nullptr` 。  常數 0 指派給物件控制代碼的實際 Boxed `Int32` 和 `Object^` 的轉換。  
  
## 範例  
 下列程式碼範例示範，可使用 `nullptr` 關鍵字，原生控制代碼指標，或者可以使用函式引數。  然後範例會說明 `nullptr` 關鍵字可用來檢查參考，才能使用它。  
  
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
  
## 範例  
 **範例**  
  
 下列程式碼範例會顯示包含 `nullptr` 和零在原生指標可以交替使用。  
  
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
  
 **Output**  
  
  **pMyClass \=\= nullptr**  
 **pMyClass \=\= 0**  
 **pMyClass \=\= nullptr**  
 **pMyClass \=\= 0**   
## 範例  
 **範例**  
  
 下列程式碼範例中， `nullptr` 會解譯為對任何型別或原生指標的控制代碼以外的任何型別。  在使用控制代碼的函式多載的情況下對不同的型別，區分定義錯誤將會產生。  `nullptr` 必須明確轉型為型別。  
  
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
  
## 範例  
 **範例**  
  
 下列程式碼範例表示，轉換為 `nullptr` 允許並傳回指標或控制代碼包含 `nullptr` 值的轉換型別。  
  
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
  
## 範例  
 **範例**  
  
 下列程式碼範例中， `nullptr` 可做為函式參數。  
  
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
  
 **Output**  
  
  **測試**   
## 範例  
 **範例**  
  
 下列程式碼範例中示範控制代碼宣告和明確初始化時，它們是預設初始化為 `nullptr`。  
  
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
  
 **Output**  
  
  **NULL**   
## 範例  
 **範例**  
  
 下列程式碼範例表示 `nullptr` 可以指派至原生指標，在編譯 **\/clr**時。  
  
```  
// mcpp_nullptr_6.cpp  
// compile with: /clr  
int main() {  
   int * i = 0;  
   int * j = nullptr;  
}  
```  
  
## 需求  
 編譯器選項:\(不需要；支援任何程式碼產生選項，包括 **\/ZW** 和 **\/clr**\)  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)   
 [nullptr](../cpp/nullptr.md)