---
title: "finally | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "finally 關鍵字 [C++]"
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# finally
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了 `try` 和 `catch` 子句外， CLR 例外狀況處理支援 `finally` 子句。  語意與處理 \(SEH\) 的結構化例外狀況的 `__finally` 區塊是相同的。  `__finally` 區塊可以跟隨在 `try` 或 `catch` 區塊。  
  
## 備註  
 `finally` 區塊的目的是要清除在例外狀況後所有資源時發生。  請注意 `finally` 區塊永遠執行，因此，即使沒有擲回任何例外狀況。  如果 Managed 例外狀況相關聯的 `try` 區塊內，則會擲回 `catch` 區塊只執行。  
  
 `finally` 為內容相關性關鍵字。如需詳細資訊，請參閱[視內容而有所區別的關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
## 範例  
 下列範例示範簡單的 `finally` 區塊:  
  
```  
// keyword__finally.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyException: public System::Exception{};  
  
void ThrowMyException() {  
   throw gcnew MyException;  
}  
  
int main() {  
   try {  
      ThrowMyException();  
   }  
   catch ( MyException^ e ) {  
      Console::WriteLine(  "in catch" );  
      Console::WriteLine( e->GetType() );  
   }  
   finally {  
      Console::WriteLine(  "in finally" );  
   }  
}  
```  
  
  **在 Catch**  
**MyException**  
**在最後**   
## 請參閱  
 [Exception Handling](../windows/exception-handling-cpp-component-extensions.md)