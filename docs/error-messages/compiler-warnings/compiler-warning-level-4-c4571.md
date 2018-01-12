---
title: "編譯器警告 （層級 4） C4571 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4571
dev_langs: C++
helpviewer_keywords: C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cab2068b6117f092dcc098591bb620156b2c0cf6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4571"></a>編譯器警告 (層級 4) C4571
Visual c + + 7.1; 以來變更的告知性： catch 語意不再攔截結構化例外狀況 (SEH)  
  
 編譯時，將會產生每個 catch 區塊的 C4571 **/EHs**。  
  
 編譯時**/EHs**，catch 區塊不會攔截結構化例外狀況 （除以零，null 指標，例如）; 在 catch 區塊將只有 catch 明確擲回，c + + 例外狀況。  如需詳細資訊，請參閱[例外狀況處理](../../cpp/exception-handling-in-visual-cpp.md)。  
  
 此警告預設為關閉。  開啟這個警告，確保當您使用編譯**/EHs** catch （...） 區塊不想要攔截結構化例外狀況。  如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。  
  
 您可以在下列方面，來解決 C4571  
  
-   編譯與**/EHa**如果您仍然想要您的 catch 區塊來攔截結構化例外狀況。  
  
-   如果不想讓您的 catch 區塊來攔截結構化例外狀況，但您仍然想要使用 catch 區塊，請勿啟用 C4571。  您仍然可以攔截結構化例外狀況，使用結構化例外狀況處理關鍵字 (**__try**， **__except**，和**__finally**)。  但請記住，當編譯**/EHs** c + + 例外狀況擲回時，不在 SEH 例外狀況發生時，才只會呼叫解構函式。  
  
-   取代為特定的 c + + 例外的 catch 區塊的 catch 區塊，並選擇性地將結構化的例外處理周圍 c + + 例外狀況處理 (**__try**， **__except**，和**___identifier**)。  請參閱[結構化例外狀況處理 （C/c + +）](../../cpp/structured-exception-handling-c-cpp.md)如需詳細資訊。  
  
 請參閱[/EH （例外狀況處理模型）](../../build/reference/eh-exception-handling-model.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
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