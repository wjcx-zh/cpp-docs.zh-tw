---
title: "如何：存取 System::String 中的字元 | Microsoft Docs"
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
  - "字元 [C++], 在 System::String 中存取"
  - "範例 [C++], 字串"
  - "字串 [C++], 存取字元"
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：存取 System::String 中的字元
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以存取 <xref:System.String> 物件的字元，以進行使用 `wchar_t*` 字串之 Unmanaged 函式的高效能呼叫。  此方法會產生內部指標，指向 <xref:System.String> 物件的第一個字元。  可以直接使用這個指標，或 Pin 並傳遞至使用一般 `wchar_t` 字串的函式。  
  
## 範例  
 `PtrToStringChars` 會傳回 <xref:System.Char>，這是內部指標 \(也稱為 `byref`\)。  因此會適用於記憶體回收。  您不需要 Pin 這個指標，除非要傳遞至原生 \(Native\) 函式。  
  
 請考慮下列程式碼：不需要 Pin，因為 `ppchar` 是內部指標，如果記憶體回收行程移動此指標所指向的字串，則也會更新 `ppchar`。  若不使用 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md)，程式碼還是可以運作，而且不會有 Pin 所導致的潛在效能影響。  
  
 如果您將 `ppchar`  傳遞至原生函式，則它必須是 Pin 指標，而記憶體回收行程會無法更新 Unmanaged 堆疊框架上的任何指標。  
  
```  
// PtrToStringChars.cpp  
// compile with: /clr  
#include<vcclr.h>  
using namespace System;  
  
int main() {  
   String ^ mystring = "abcdefg";  
  
   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );  
  
   for ( ; *ppchar != L'\0'; ++ppchar )  
      Console::Write(*ppchar);  
}  
```  
  
  **abcdefg**   
## 範例  
 這個範例會示範需要 Pin 的地方。  
  
```  
// PtrToStringChars_2.cpp  
// compile with: /clr  
#include <string.h>  
#include <vcclr.h>  
// using namespace System;  
  
size_t getlen(System::String ^ s) {  
   // Since this is an outside string, we want to be secure.  
   // To be secure, we need a maximum size.  
   size_t maxsize = 256;  
   // make sure it doesn't move during the unmanaged call  
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);  
   return wcsnlen(pinchars, maxsize);  
};  
  
int main() {  
   System::Console::WriteLine(getlen("testing"));  
}  
```  
  
 **7**   
## 範例  
 內部指標具有所有的原生 C\+\+ 指標的屬性。  例如，您可以使用這個指標逐一查看連結的資料結構，並且只使用一個指標來進行插入和刪除：  
  
```  
// PtrToStringChars_3.cpp  
// compile with: /clr /LD  
using namespace System;  
ref struct ListNode {  
   Int32 elem;   
   ListNode ^ Next;  
};  
  
void deleteNode( ListNode ^ list, Int32 e ) {   
   interior_ptr<ListNode ^> ptrToNext = &list;  
   while (*ptrToNext != nullptr) {  
      if ( (*ptrToNext) -> elem == e )  
         *ptrToNext = (*ptrToNext) -> Next;   // delete node  
      else  
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node  
   }  
}  
```  
  
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)