---
title: 編譯器錯誤 C2712 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2712
dev_langs:
- C++
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c26c5d7a24c022cacf4c20687b2d8c58f7e9e342
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2712"></a>編譯器錯誤 C2712
無法在需要物件回溯 (Object Unwinding) 的函式中使用 __try  
  
 如果您使用，可能會發生錯誤 C2712 [/EHsc](../../build/reference/eh-exception-handling-model.md)，而且也處理結構化例外狀況的函式有需要回溯 （解構） 的物件。  
  
 可能的解決方案：  
  
-   將需要 SEH 的程式碼移至另一個函式  
  
-   重寫使用 SEH 的函式，以避免使用具有解構函式的本機變數和參數。 請勿在建構函式或解構函式中使用 SEH  
  
-   編譯時不要使用 /EHsc  
  
 如果您呼叫方法，使用宣告，也可能發生錯誤 C2712 [__event](../../cpp/event.md)關鍵字。 由於事件可能會用在多執行緒環境中，編譯器會產生程式碼會防止基礎事件物件的操作，然後將產生的程式碼包含在 SEH [try-finally 陳述式](../../cpp/try-finally-statement.md)。 因此，如果您呼叫事件方法，並以類型具有解構函式的引數傳值，就會發生錯誤 C2712。 此情況下的解決方案之一，是傳遞引數做為常數參考。  
  
## <a name="example"></a>範例  
 如果您使用編譯也會發生 C2712 **/clr: pure**並宣告指標-對函式中的靜態陣列`__try`區塊。 靜態成員需要有編譯器才能下使用動態初始化 **/clr: pure**，這表示 c + + 例外狀況處理。 然而，在 `__try` 區塊中不允許執行 C++ 例外狀況處理。  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
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