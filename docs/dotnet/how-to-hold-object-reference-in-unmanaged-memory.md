---
title: "如何：在 Unmanaged 記憶體中存放物件參考 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gcroot 關鍵字 [C++], 原生函式中的物件參考"
  - "物件參考, 在原生函式中"
  - "物件 [C++], 原生函式中的參考"
  - "參考, 到原生函式中的物件"
ms.assetid: a61eb8ce-3982-477d-8d3d-2173fd57166d
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 Unmanaged 記憶體中存放物件參考
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用包裝 <xref:System.Runtime.InteropServices.GCHandle> 的 gcroot.h，在 Unmanaged 記憶體中存放 CLR 物件參考。  或者您也可以直接使用 `GCHandle`。  
  
## 範例  
  
```  
// hold_object_reference.cpp  
// compile with: /clr  
#include "gcroot.h"  
using namespace System;  
  
#pragma managed  
class StringWrapper {  
  
private:  
   gcroot<String ^ > x;  
  
public:  
   StringWrapper() {  
      String ^ str = gcnew String("ManagedString");  
      x = str;  
   }  
  
   void PrintString() {  
      String ^ targetStr = x;  
      Console::WriteLine("StringWrapper::x == {0}", targetStr);  
   }  
};  
#pragma unmanaged  
int main() {  
   StringWrapper s;  
   s.PrintString();  
}  
```  
  
  **StringWrapper::x \=\= ManagedString**   
## 範例  
 `GCHandle` 提供您在 Unmanaged 記憶體中存放 Managed 物件參考的方法。您可使用 <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> 方法建立 Managed 物件的不透明控制代碼，並使用 <xref:System.Runtime.InteropServices.GCHandle.Free%2A> 來釋放控制代碼。  此外，<xref:System.Runtime.InteropServices.GCHandle.Target%2A> 方法允許您從 Managed 程式碼中的控制代碼取回物件參考。  
  
```  
// hold_object_reference_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma managed  
class StringWrapper {  
   IntPtr m_handle;  
public:  
   StringWrapper() {  
      String ^ str = gcnew String("ManagedString");  
      m_handle = static_cast<IntPtr>(GCHandle::Alloc(str));  
   }  
   ~StringWrapper() {  
      static_cast<GCHandle>(m_handle).Free();  
   }  
  
   void PrintString() {  
      String ^ targetStr = safe_cast< String ^ >(static_cast<GCHandle>(m_handle).Target);  
      Console::WriteLine("StringWrapper::m_handle == {0}", targetStr);  
   }  
};  
  
#pragma unmanaged  
int main() {  
   StringWrapper s;   
   s.PrintString();  
}  
```  
  
  **StringWrapper::m\_handle \=\= ManagedString**   
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)