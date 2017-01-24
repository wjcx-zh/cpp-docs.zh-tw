---
title: "未處理的 C++ 例外狀況 | Microsoft Docs"
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
  - "C++ 例外狀況處理, 未處理的例外狀況"
  - "catch 關鍵字 [C++], 找不到處理常式"
  - "事件處理常式, 未處理的例外狀況"
  - "例外狀況, 未處理的"
  - "未處理的例外狀況"
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 未處理的 C++ 例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果目前例外狀況中找不到相符處理常式 \(或省略 **catch** 處理常式\)，則會呼叫預先定義 `terminate` 執行階段函式。\(您可以在任何處理常式中明確呼叫 `terminate`\)。`terminate` 的預設動作是呼叫 `abort`。  如果您希望 `terminate` 在結束應用程式之前呼叫程式中的其他函式，請使用做為單一引數呼叫的函式名稱來呼叫 `set_terminate` 函式。  您可以隨時在程式中呼叫 `set_terminate`。  `terminate` 常式會一律呼叫指定的最後一個函式做為 `set_terminate` 的引數。  
  
## 範例  
 下列範例會擲回 `char *` 例外狀況，不過，其中並不包含任何指定攔截 `char *` 類型例外狀況的處理常式。  對 `terminate` 的呼叫會指示 `set_terminate` 呼叫 `term_func`。  
  
```  
// exceptions_Unhandled_Exceptions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
void term_func() {  
   cout << "term_func was called by terminate." << endl;  
   exit( -1 );  
}  
int main() {  
   try  
   {  
      set_terminate( term_func );  
      throw "Out of memory!"; // No catch handler for this exception  
   }  
   catch( int )  
   {  
      cout << "Integer exception raised." << endl;  
   }  
   return 0;  
}  
```  
  
## Output  
  
```  
term_func was called by terminate.  
```  
  
 `term_func` 函式應該終止程式或目前的執行緒，最好是透過呼叫 `exit` 的方式進行。  如果未如預期進行而傳回至呼叫端，則會呼叫 `abort`。  
  
## 請參閱  
 [C\+\+ 例外狀況處理](../cpp/cpp-exception-handling.md)