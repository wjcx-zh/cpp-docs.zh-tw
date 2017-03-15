---
title: "編譯器警告 (層級 4) C4571 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4571"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4571"
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4571
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

告知性：catch\(...\) 語意 \(Semantics\) 從 Visual C\+\+ 7.1 開始已經變更，不再攔截結構化例外狀況處理常式 \(SEH\)  
  
 利用 **\/EHs** 編譯時，每一個 catch\(...\) 區塊都會產生 C4571。  
  
 利用 **\/EHs** 編譯時，catch\(...\) 區塊將不會攔截結構化例外 \(例如，除以零、null 指標\)；catch\(...\) 區塊將只能攔截明確擲回的 C\+\+ 例外狀況。如需詳細資訊，請參閱[例外狀況處理](../../cpp/exception-handling-in-visual-cpp.md)。  
  
 此警告在預設情況下為關閉的。開啟這項警告，可確保利用 **\/EHs** 編譯時，catch \(...\) 區塊不會企圖攔截結構化例外。如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 您可以用下列其中一個方法解決 C4571 的問題，  
  
-   如果仍然要 catch\(...\) 區塊攔截結構化例外，請利用 **\/EHa** 編譯。  
  
-   如果不要 catch\(...\) 區塊攔截結構化例外，但仍然要使用 catch\(...\) 區塊，則切勿啟用 C4571。您仍然可以使用結構化例外狀況處理關鍵字 \(**\_\_try**、**\_\_except** 和 **\_\_finally**\)，攔截結構化例外。但切記！利用 **\/EHs** 編譯時，解構函式 \(Destructor\) 只會在擲回 C\+\+ 例外狀況時呼叫，而不是在有 SEH 例外狀況時發生。  
  
-   以特定 C\+\+ 例外狀況的 catch 區塊取代 catch\(...\) 區塊，同時也可以在 C\+\+ 例外處理四周加入結構化例外處理 \(**\_\_try**、**\_\_except** 和 **\_\_finally**\)。如需詳細資訊，請參閱[結構化例外狀況處理](../../cpp/structured-exception-handling-c-cpp.md)。  
  
 如需詳細資訊，請參閱[\/EH \(例外狀況處理模型\)](../../build/reference/eh-exception-handling-model.md)。  
  
## 範例  
 下列範例會產生 C4571。  
  
```  
// C4571.cpp  
// compile with: /EHs /W4 /c  
#pragma warning(default : 4571)  
int main() {  
   try {  
      int i = 0, j = 1;  
      j /= i;   // this will throw a SE (divide by zero)  
   }  
   catch(...) {}   // C4571 warning  
}  
```