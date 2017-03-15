---
title: "如何：以原生類型宣告控制代碼 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "gcroot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gcroot 關鍵字 [C++]"
  - "控制代碼, 宣告"
  - "類型 [C++], 宣告控制代碼於"
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何：以原生類型宣告控制代碼
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您不能宣告控制代碼型別原生型別。vcclr.h 會提供型別安全包裝函式樣板 `gcroot` 參考從 C\+\+ 堆積參考 CLR 物件。  這個樣板可讓您在原生型別中內嵌虛擬控制代碼，並且將它視為基礎型別。  大部分的情況下，都可以使用 `gcroot` 物件做為內嵌型別而不用任何轉型。  不過，您也可以使用 [for each、in](../dotnet/for-each-in.md) 搭配 `static_cast` 來擷取基礎 Managed 參考。  
  
 `gcroot` 樣板是使用數值類別 System::Runtime::InteropServices::GCHandle 的功能進行實作的，此數值類別提供「控制代碼」給記憶體回收的堆積。  請注意，控制代碼本身不會被記憶體回收，當 `gcroot` 類別中的解構函式 \(Destructor\) \(此解構函式無法以手動方式呼叫\) 不再使用控制代碼時，便會釋放控制代碼。  如果您在原生堆積上具現化 `gcroot` 物件，就必須在該資源上呼叫 Delete。  
  
 執行階段將會維護控制代碼與所參考的 CLR 物件之間的關聯。  當 CLR 物件與記憶體回收的堆積一起移動時，控制代碼將會傳回物件的新位址。  將變數指派給 `gcroot` 樣板之前，不需要 Pin 變數。  
  
## 範例  
 此範例會示範如何在原生堆疊上建立 `gcroot` 物件。  
  
```  
// mcpp_gcroot.cpp  
// compile with: /clr  
#include <vcclr.h>  
using namespace System;  
  
class CppClass {  
public:  
   gcroot<String^> str;   // can use str as if it were String^  
   CppClass() {}  
};  
  
int main() {  
   CppClass c;  
   c.str = gcnew String("hello");  
   Console::WriteLine( c.str );   // no cast required  
}  
```  
  
  **hello**   
## 範例  
 此範例會示範如何在原生堆積上建立 `gcroot` 物件。  
  
```  
// mcpp_gcroot_2.cpp  
// compile with: /clr  
// compile with: /clr  
#include <vcclr.h>  
using namespace System;  
  
struct CppClass {  
   gcroot<String ^> * str;  
   CppClass() : str(new gcroot<String ^>) {}  
  
   ~CppClass() { delete str; }  
  
};  
  
int main() {  
   CppClass c;  
   *c.str = gcnew String("hello");  
   Console::WriteLine( *c.str );  
}  
```  
  
  **hello**   
## 範例  
 此範例會示範如何在 boxed 型別上使用 `gcroot`，藉以使用 `gcroot` 在原生型別中存放實值型別 \(並非參考型別\) 的參考。  
  
```  
// mcpp_gcroot_3.cpp  
// compile with: /clr  
#include < vcclr.h >  
using namespace System;  
  
public value struct V {  
   String^ str;  
};  
  
class Native {  
public:  
   gcroot< V^ > v_handle;  
};  
  
int main() {  
   Native native;  
   V v;  
   native.v_handle = v;  
   native.v_handle->str = "Hello";  
   Console::WriteLine("String in V: {0}", native.v_handle->str);  
}  
```  
  
  **V: Hello 中的字串**   
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)