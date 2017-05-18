---
title: "編譯器錯誤 C2316 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2316
dev_langs:
- C++
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: 60e5fb2346c92b3005e7cbfe1663d43cc0a12cdc
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-error-c2316"></a>編譯器錯誤 C2316

> '*例外狀況*': 無法攔截，因為無法存取解構函式和/或複製建構函式  
  
以傳值方式或以傳址方式攔截到例外狀況，但是複製建構函式及/或指派運算子都無法存取。  
  
此程式碼的 Visual Studio 2003 之前, 的 Visual c + + 版本接受，但現在會產生錯誤。  
  
Visual Studio 2015 中的一致性變更進行套用至錯誤的 catch 陳述式的 MFC 例外狀況衍生自這個錯誤`CException`。 因為`CException`繼承私用複製建構函式，類別和其系出物件是不可複製，因此無法傳遞的值，這也表示他們無法攔截的值。 Catch 陳述式，由無法攔截的例外狀況，在執行階段，會使先前的值所攔截 MFC 例外狀況，但現在，編譯器可正確識別這種情況以及報告錯誤 C2316。 若要修正此問題，我們建議您使用 MFC TRY/CATCH 巨集，而不是撰寫自己的例外狀況處理常式，但不是適用於您的程式碼，如果攔截 MFC 例外狀況的參考而。   
  
## <a name="example"></a>範例  
 下列範例會產生 C2316：  
  
```  
// C2316.cpp  
// compile with: /EHsc  
#include <stdio.h>  
  
extern "C" int printf_s(const char*, ...);  
  
struct B   
{  
public:  
    B() {}  
    // Delete the following line to resolve.  
private:  
    // copy constructor  
    B(const B&)   
    {  
    }  
};  
  
void f(const B&)   
{  
}  
  
int main()   
{  
    try   
    {  
        B aB;  
        f(aB);  
    }  
    catch (B b) {   // C2316  
        printf_s("Caught an exception!\n");     
    }  
}  
```
