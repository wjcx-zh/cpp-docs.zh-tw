---
title: "編譯器錯誤 C2712 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2712
dev_langs:
- C++
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 89b7d0ad3c7e175db1525c2f3fb8407240ce943c
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2712"></a>編譯器錯誤 C2712
無法在需要物件回溯 (Object Unwinding) 的函式中使用 __try  
  
 如果您使用，就會發生錯誤 C2712 [/EHsc](../../build/reference/eh-exception-handling-model.md)，而且也處理結構化例外狀況的函式需要回溯 （解構） 的物件。  
  
 可能的解決方案：  
  
-   將需要 SEH 的程式碼移至另一個函式  
  
-   重寫使用 SEH 的函式，以避免使用具有解構函式的本機變數和參數。 請勿在建構函式或解構函式中使用 SEH  
  
-   編譯時不要使用 /EHsc  
  
 如果您呼叫方法時使用的宣告，也會發生錯誤 C2712 [__event](../../cpp/event.md)關鍵字。 由於事件可能在多執行緒環境中，編譯器會產生程式碼可防止基礎事件物件的操作，然後將產生的程式碼封入 SEH [try-finally 陳述式](../../cpp/try-finally-statement.md)。 因此，如果您呼叫事件方法，並以類型具有解構函式的引數傳值，就會發生錯誤 C2712。 此情況下的解決方案之一，是傳遞引數做為常數參考。  
  
## <a name="example"></a>範例  
 如果您使用編譯，也會發生 C2712 **/clr︰ 純**，並宣告指標-至-函式中的靜態陣列`__try`區塊。 靜態成員要求編譯器使用底下的動態初始化**/clr: pure**，這表示 c + + 例外狀況處理。 然而，在 `__try` 區塊中不允許執行 C++ 例外狀況處理。  
  
 **/Clr: pure**和**/clr: safe** Visual Studio 2015 中的編譯器選項已被取代。  
  
 下列範例會產生 C2712，並說明如何加以修正。  
  
```  
// C2712.cpp  
// compile with: /clr:pure /c  
struct S1 {  
   static int smf();  
   void fnc();  
};  
  
void S1::fnc() {  
   __try {  
      static int (*array_1[])() = {smf,};   // C2712  
  
      // OK  
      static int (*array_2[2])();  
      array_2[0] = smf;  
    }  
    __except(0) {}  
}  
```
