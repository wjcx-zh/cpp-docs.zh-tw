---
title: "編譯器警告 （層級 4） C4256 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4256
dev_langs: C++
helpviewer_keywords: C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4bbaec27948f061cb21eeb432446517d4f9a6b2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4256"></a>編譯器警告 (層級 4) C4256
'function': 具有虛擬基底類別建構函式有 '...';可能不相容與舊版本的 Visual c + + 呼叫  
  
 可能不相容。  
  
 請參考下列程式碼範例。 如果 S2::S2 建構函式的定義 (int i，...) 使用 Visual c + + 編譯器，第 7 版之前的版本所編譯，但下列範例使用最新版本進行編譯、 S3 建構函式的呼叫會無法正常運作的原因特殊案例的呼叫慣例改變。 如果兩個都是以 Visual C++ 6.0 編譯的，呼叫也不會正常運作，除非沒有傳遞省略符號參數。  
  
 若要修正這個警告，  
  
1.  請勿使用建構函式中的省略符號。  
  
2.  請確定專案中的所有元件都建置與目前的版本 （包括任何可能定義或參考此類別的程式庫），然後停用警告使用[警告](../../preprocessor/warning.md)pragma。  
  
 下列範例會產生 C4256:  
  
```  
// C4256.cpp  
// compile with: /W4  
// #pragma warning(disable : 4256)  
struct S1  
{  
};  
  
struct S2: virtual public S1  
{  
   S2( int i, ... )    // C4256  
   {  
      i = 0;  
   }  
   /*  
   // try the following line instead  
   S2( int i)  
   {  
      i = 0;  
   }  
   */  
};  
  
void func1()  
{  
   S2 S3( 2, 1, 2 );   // C4256  
   // try the following line instead  
   // S2 S3( 2 );  
}  
  
int main()  
{  
}  
```