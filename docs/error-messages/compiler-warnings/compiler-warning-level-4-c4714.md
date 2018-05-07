---
title: 編譯器警告 （層級 4） C4714 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4714
dev_langs:
- C++
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0f327e7ffc5d2fe00abe3c0845af10a846243bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4714"></a>編譯器警告 (層級 4) C4714
函式 'function' 標記為 __forceinline 無法內嵌  
  
 指定的函式已選取的內嵌展開，但編譯器無法執行內嵌。  
  
 雖然`__forceinline`是更強的指示，以比編譯器`__inline`、 內嵌仍然會由編譯器決定，會執行，但沒有啟發學習法會用來判斷優勢內嵌此函式。  
  
 在某些情況下，編譯器不會內嵌特定函式機械原因。 例如，編譯器不會內嵌：  
  
-   如果它會導致混用 SEH 與 c + + EH 函式。  
  
-   複製具有某些函式會建構-GX//ehs//eha 時傳值方式傳遞的物件。  
  
-   -GX//ehs//eha 時，無法回溯物件傳回值的函式。  
  
-   具有內嵌組譯碼不含-Og Ox//o1//o2 編譯時的函式。  
  
-   具有變數引數清單的函式。  
  
-   函式**再試一次**（c + + 例外狀況處理） 陳述式。  
  
 下列範例會產生 C4714:  
  
```  
// C4714.cpp  
// compile with: /Ob1 /GX /W4  
__forceinline void func1()  
{  
   try  
   {  
   }  
   catch (...)  
   {  
   }  
}  
  
void func2()  
{  
   func1();   // C4714  
}  
  
int main()  
{  
}  
```